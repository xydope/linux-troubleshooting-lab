# linux-troubleshooting-lab

Hands-on break-fix lab for practicing Linux troubleshooting. Each scenario breaks a clean system in a specific way; the goal is to diagnose and fix it, then document the root cause.

## Lab setup

- OS: AlmaLinux 9 (planned: Ubuntu 24.04, AlmaLinux 10)
- Hypervisor: VM with a `clean-base` snapshot, reverted before every scenario
- Docker-based scenarios planned as a separate track

## How it works

1. Revert the VM to the `clean-base` snapshot
2. Run a scenario's `break.sh` without reading it
3. Diagnose and fix the problem
4. Compare with `SOLUTION.md`

## Structure

```
scenarios/
└── NN-name/
    ├── break.sh       # breaks the system
    ├── README.md      # symptoms only, no spoilers
    └── SOLUTION.md    # diagnosis, root cause, fix, prevention
docs/
└── troubleshooting-checklist.md
```

## Planned scenarios

- [ ] Services and systemd (nginx config errors, port conflicts, broken unit files)
- [ ] Disk and filesystems (full disk, inode exhaustion, bad fstab, LVM)
- [ ] Network (DNS, routing, firewalld, wrong bind address)
- [ ] Permissions and SELinux
- [ ] Performance (CPU, memory, OOM, iowait)
- [ ] Boot issues (GRUB, emergency mode, root password reset)
- [ ] Docker (broken images, networks, volumes, failing containers)

## Troubleshooting approach

`systemctl status` → `journalctl` → `ss -tlnp` → `df -h` / `df -i` → `dmesg` → app logs → permissions / SELinux → config

## Disclaimer

Scripts intentionally break the system. Run them only in a disposable VM with a snapshot.