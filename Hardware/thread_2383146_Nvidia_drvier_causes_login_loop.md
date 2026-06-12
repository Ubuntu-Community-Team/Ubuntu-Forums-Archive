---
title: "Nvidia drvier causes login loop"
date: 2018-01-21
forum: Hardware
---

### Post by rwalkerIII on 2018-01-21
On Ubuntu 17.10, installing TensorFlow CUDA drivers for Nvidia, caused Linux to go into a login loop.  The Nvidia driver would crash after login.  
Everything runs fine with nouveau, but wanted to know if there was a known solution for this?  

I searched around, tried many suggested solutions, none worked.  Installed latest Nvidia driver, "nvidia-current" still got the login loop.  Installed driver "nvidia-384", and again got the login loop.

Running: wayland (not xorg)

Following are the details:
Motherboard:
   Core i7-6700
   Gigabyte Z170XP-SLI
    32GB RAM

Linux:
   4.13.0-25

Video card:
 *-display                 
       description: VGA compatible controller
       product: GM206 [GeForce GTX 960]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:131 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:c0000-dffff

Nvidia driver error that I believe causes re-login:
Jan 21 08:54:34 walkubu systemd[1]: Started Login Service.
Jan 21 08:54:34 walkubu apport[837]:    ...done.
Jan 21 08:54:34 walkubu systemd[1]: Started LSB: automatic crash report generation.
Jan 21 08:54:34 walkubu ModemManager[833]: <info>  ModemManager (version 1.6.8) starting in system bus...
Jan 21 08:54:34 walkubu nvidia-persistenced: Received signal 15
Jan 21 08:54:34 walkubu nvidia-persistenced: Socket closed.
Jan 21 08:54:34 walkubu systemd[1]: Stopping NVIDIA Persistence Daemon...
Jan 21 08:54:34 walkubu nvidia-persistenced: PID file unlocked.
Jan 21 08:54:34 walkubu gpu-manager[836]: /etc/modprobe.d is not a file
Jan 21 08:54:34 walkubu nvidia-persistenced: PID file closed.
Jan 21 08:54:34 walkubu nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Jan 21 08:54:34 walkubu nvidia-persistenced: Shutdown (822)
Jan 21 08:54:34 walkubu grub-common[813]:    ...done.
Jan 21 08:54:34 walkubu systemd[1]: Started LSB: Record successful boot for GRUB.
Jan 21 08:54:34 walkubu systemd[1]: Stopped NVIDIA Persistence Daemon.

Any information would be appreciated.

---

### Post by Yellow Pasque on 2018-01-21
You did switch to Xorg with the nvidia driver, correct? [https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers](https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers)

---

### Post by rwalkerIII on 2018-01-21
Thanks.  Just tried disabling Wayland in /etc/gdm3/custom.conf, re-installed Nvidia driver 384, rebooted, same errors.

---

