---
title: "Acer One S1002 - what wifi card / module is it using? Not easy to diagnose..."
date: 2022-08-03
forum: Hardware
---

### Post by andrzejl2 on 2022-08-03
SOLVED...

Hello,

My father bought this PoS machine which is HORRIBLE in every single way (I curse at Acer for releasing it):

- 64 bit capable CPU but 32 bit UEFI which means Windows 64 bit and most of 64 bit distos fails to boot or install
- 2 gigs of SOLDERED ram memory, no upgrade possible
- 30 gb memory card (yes its a memory card NOT hdd or ssd)
- many other faults

Anyway. I got Ubuntu 22.04 LTS working on it (wasn't easy) as system fails to boot after initial install. Needs to be booted into LiveUSB and from "Try Ubuntu" connected to internet and fixed using these commands:

```
mount /dev/mmcblk2p2 /mnt
mount -t proc none /mnt/proc/
mount -o bind /dev /mnt/dev/
mount -o bind /sys /mnt/sys/
mount -o bind /run /mnt/run/
mount -t efivarfs none /mnt/sys/firmware/efi/efivars
mount /dev/mmcblk2p1 /mnt/boot/efi/
chroot /mnt
apt-get remove -y --purge --allow-remove-essential grub-efi-amd64-signed shim-signed
apt -y install efibootmgr grub-common grub-efi-ia32 grub-efi-ia32-bin grub-pc-bin grub2-common mokutil secureboot-db
apt -y --purge autoremove
grub-install /dev/mmcblk2
update-grub
exit
reboot
```

After that system boots as expected upon reboot.

My problem is that I cannot figure out what wifi module does it use.

I have no idea how to diagnose it - I tried the usual stuff:

```
lshw -C network
```

>  *-network:0       description: Wireless interface
       physical id: f
       bus info: mmc@0:0001:1
       logical name: wlan1
       serial: 7c:c7:09:e2:af:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bs driverversion=5.15.0-43-generic multicast=yes wireless=IEEE 802.11

```
inxi -v7
```

> System:  Host: Acer-One-S1002 Kernel: 5.15.0-43-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Console: pty pts/1 DM: GDM3 42.0 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Acer product: One S1002 v: 1.10 serial: NTG5CEP005612789C67200 Chassis:
    type: 10 serial: 1ZNM1Z00400608171B7200
  Mobo: Acer model: Popcorn serial: NBG5C11001604F0A0B7200 UEFI: American Megatrends v: 1.10
    date: 10/20/2015
Network:
  IF-ID-1: wlan1 state: down mac: 7c:c7:09:e2:af:45
  WAN IP: No WAN IP found. Connected to web? SSL issues?

```
lspci
```

> 00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)


```
lsusb
```

> Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 005: ID 06cb:73f4 Synaptics, Inc. ITE Device(8910)
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I have no idea which diagnostic information is necessary for you guys to help me solve it so ask and you shall be given.

System is installed as Ubuntu Minimal with 3rd party codecs / players and 100% updated.

Thank you in advance for any help provided.

I am blind...

configuration: broadcast=yes **driver=rtl8723bs** driverversion=5.15.0-43-generic multicast=yes wireless=IEEE 802.11

Kindest regards.

Andrzej

---

### Post by Yellow Pasque on 2022-08-03
Hey, don't be so hard on yourself. You can mark the thread solved using the "thread tools' menu above the first post.

---

