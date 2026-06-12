---
title: "Ati drivers for Ubuntu 16.xx"
date: 2017-05-08
forum: Hardware
---

### Post by 4l3x2 on 2017-05-08
Good afternoon.

In order to get the best performances from a Windows game to run under Wine, I'd like to install the original drivers for my video card (Sapphire Toxic with Ati Radeon R9 270x) but the 16.xx release of Ubuntu (in my case XUbuntu 16.04.2) is not supported for this chip (but older chips are supported :evil: ).

The 15.04 release is supported, instead, so I asked Amd if there is a way to use that driver.
They answered (in less than a day) to watch in the unofficial Amd Linux Driver, where I found the same version (15.04) but with a note:
Amd drivers in .deb format can always be repackaged

Is this action allowed from an older distro to a newer?

If yes, how can I do it?

If not I fear I'll have to make a dual boot system only to play some games, maybe with Lubuntu to keep it light....

Thank you very much for your help :KS

---

### Post by Yellow Pasque on 2017-05-08
No, you can't use the old fglrx/Catalyst driver in Ubuntu 16.04.

The newer proprietary driver AMDGPU-Pro doesn't list Pitcairn-based GPU's as officially supported. I know I've seen some reports where folks tried and it didn't work or it worked, but slowly.

So just stick with the open source radeon driver, or install Ubuntu 14.04.1 if you want to try fglrx/Catalyst.

---

### Post by QIII on 2017-05-08
Hello!

The open source AMDGPU driver and the AMDGPU-PRO driver (the AMDGPU driver with a proprietary overlay) are what the Linux community got after begging AMD for an open source driver for many years.  Be careful what you wish for ...

Anyway, AMDGPU only works with GCN (Graphics Core Next) GPUs.  AMD started with GCN 1.2 and 1.3 chips, and is working back to GCN 1.1 (partially completed) and GCN 1.0 (they're working on it).

The Southern Islands chips (including the Pitcairn GPUs) are GCN 1.0.  So although they will eventually be supported by AMDGPU, they may not yet be.

This means you will either have to:  

1.  Wait and use the open source Radeon driver installed by default with Ubuntu until Pitcairn chips are supported.

2.  Wait and use Ubuntu 14.04.1 or earlier with fglrx until Pitcairn chips are supported.

I'm sorry the news isn't better, but AMD did what we asked them to do.

Cheers!

---

### Post by 4l3x2 on 2017-05-08
Yes, I was thinking to use a dual boot system; on the first partition I'll keep XUbuntu 16.04.2 to work, on a second one I'll install LUbuntu 14.04.1 to play some game.

So, just to summarize for my needs:
- my chipset, soon or later, will be supported both by AMD and the Linux community, so I only have to wait for it without the need to change the graphic card (I plan to play old games, Grand Prix Legends, Grand Prix 4, Sanitarium....)
- since they are all 32bits games I think I'll go better installing a 32bits OS
- seems that newer releases than 14.04.1 doesn't support fglrx anymore (I'll use only LTS releases), so I won't update the system, but what could be a working strategy for other programs? Reach a functional configuration and stop all the updates? I mean updating wine, or gimp etc....
- what is exactly fglrx? A completely proprietary driver developed by AMD/NVIDIA/MATROX or something different?
- after installing the boot loader from the 14.04.1 version, will I have any trouble? How can I get rid of them? A command line is ok, like grub-install /dev/sda followed by update-grub2 from 16.04.2
- Logitech wheels are supported directly from the 3.19 kernel, if don't go wrong, what version is the newest allowed by 14.04.1 release?

Thank you very much for your help

---

### Post by Yellow Pasque on 2017-05-08
> **QIII said:**
> The open source AMDGPU driver and the AMDGPU-PRO driver (the AMDGPU driver with a proprietary overlay) are what the Linux community got after begging AMD for an open source driver for many years.  Be careful what you wish for... I'm sorry the news isn't better, but AMD did what we asked them to do.

This seems overly negative. The open source driver works well for most uses. What exactly were you wishing for? A blob and no support for open source like Nvidia?

> Anyway, AMDGPU only works with GCN (Graphics Core Next) GPUs.  AMD started with GCN 1.2 and 1.3 chips, and is working back to GCN 1.1 (partially completed) and GCN 1.0 (they're working on it).
The Southern Islands chips (including the Pitcairn GPUs) are GCN 1.0.  So although they will eventually be supported by AMDGPU, they may not yet be.

Unless you want to run recent games/apps using Vulkan, the amdgpu kernel module is not an interesting "upgrade" over the radeon kernel module for GCN 1.0/1.1. They perform similarly on OpenGL benchmarks: [http://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-410&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-410&num=1)

[QUOTE=4l3x2]my chipset, soon or later, will be supported both by AMD and the Linux community[/QUOTE]

It's already supported by the open source radeon driver (i.e. "the community").

> what is exactly fglrx?
It's the Linux version of the ATI/AMD Catalyst Windows driver. They use a lot of 3D code from the Windows driver (like game profiles).

---

### Post by QIII on 2017-05-08
> **Temüjin said:**
> This seems overly negative. The open source driver works well for most uses. What exactly were you wishing for? A blob and no support for open source like Nvidia?

Nope.  AMD did the right thing.  I applaud them.  But this did cause a lot of turmoil.

---

### Post by mastablasta on 2017-05-09
> **4l3x2 said:**
> 
- Logitech wheels are supported directly from the 3.19 kernel, if don't go wrong, what version is the newest allowed by 14.04.1 release?


i believe it is 3.13

since you probably read arround the issue isn't so much the driver as it is that they do not support newer xserver that is implemented in the later ubuntus.

is the default driver giving you issues in 16.04? poor performance? perhaps some switches can slightly improve it.

also i am not sure what was sovled by havign opensource and opensource with proprietary part. as long as proprietary part doesn't get propper support time, then issue Will resurface and you have radeon / unsupported fglrx issue again. because the main issue for most users wasn't the closed soruce nature of the fglrx driver, but the fac tthat are only a few year tzhe support for newer xserver and kernel was not longer implemented. so you could dhave 3 year old chip that suddenly lost descent GPU support. luckilly Ubuntu has 5 year support now, so the PC i got in 2012 Will still work OK in 2019 (radeon driver doesn't manage power propperly on it).

---

### Post by mörgæs on 2017-05-09
> **4l3x2 said:**
> on a second one I'll install LUbuntu 14.04.1 to play some game.



Lubuntu 14.04 is out of support so you shouldn't go that way. If you really want a 14.04 Buntu then Ubuntu, supported through april 2019, is a better choice.

---

### Post by efflandt on 2017-05-09
Not sure what would work best if you use UEFI, but if it is a BIOS system I would only install grub on the system you use most and not on the other one. For example install grub when installing 16.04.2 and do not install grub when installing 14.04.1. After any kernel updates in 14.04.1 you would need to boot 16.04.2 and run "sudo update-grub" from there to boot the newest 14.04.1 kernel. That is basically what I did when I installed both Ubuntu (with grub) and Lubuntu (without grub) in separate partitions (with common /home, but both systems same version#) to boot from SD card on a tablet PC.

---

