---
title: "No xserver on Sony Vaio Pro 13"
date: 2013-07-17
forum: Hardware
---

### Post by tripkick on 2013-07-17
On a week old Vaio (svp132a1cm) I managed to install Kubuntu 13.04 alongside Windows 8 (disabling secure boot, setting the bios to legacy and running boot-repair after the install). 

Grub works, it starts Windows and it starts Linux though not without editing the entry. I have to delete the gfxmode entry and add nomodeset as a kernel parameter. Otherwise Linux stops booting with the message
```
fb conflicting fb hw usage inteldrmfb vs efi vga - removing generic driver
```

But the edited entry only offers a login on the standard ttys, the xserver doesn't start. 

When I compare the X.org logfile of the installed system and the one on the install stick I fiind that this line 
 ```
config/udev: Adding drm device (/dev/dri/card0)
```
is missing on the installed system. In fact there isn't even a directory /dev/dri

lspci says 
```

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 90b6
    Flags: fast devsel, IRQ 16
    Memory at f7000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
```

Any hints?

Thanks.

---

### Post by tripkick on 2013-07-18
Kubuntu 13.10 solves all mentioned problems (apart from wifi) and allows a UEFI install from the stick. But for some reason grub now doesn't boot Windows 8 and simply restarts. :-(

---

### Post by tripkick on 2013-07-18
For some reason grub installed a bootmgfw.efi that wasn't working. But there was a backup file ```
/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
``` Renaming a copy of this file to bootmgfw.efi and running update-grub solved the problem.

---

### Post by debsidman on 2013-07-20
Hi, I am considering to buy the same laptop and wanted to see how you are getting on with it. I will not bual boot and usually use Debian rather than Ubuntu but would be interested in your overall experience with this laptop. Is everything else working for you?

Many thanks in advance.

---

### Post by tripkick on 2013-07-20
Hi,

it's not my laptop, I installed Ubuntu for someone else. Next week I'll probably learn more on how it works. I'll let you know. But you should probably try it with Debian testing (jessie) and a current kernel. (Ubuntu 13.10 uses Linux 3.10, iirc). Wifi still doesn't work but you could temporarily use one of the small usb-wifi-sticks. 

Regards.

---

### Post by tripkick on 2013-08-02
Most things seem to work - at least I haven't heard anything to the contrary. Only exception (apart from wifi): It's not possible to watch films: mplayer and dragonplayer only play the audio and show a green screen.

---

### Post by gordintoronto on 2013-08-02
How about VLC?

---

