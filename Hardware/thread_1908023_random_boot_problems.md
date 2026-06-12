---
title: "random boot problems"
date: 2012-01-12
forum: Hardware
---

### Post by Tamale on 2012-01-12
Hello everyone, I'm having problems booting into ubuntu 11.10.

When I power on my laptop, it goes through grub and the boot splash and then freezes at 'checking battery state'.  I can switch to a virtual term and login, at which point it says "failed to start X server".  X.org.0.log simply says "No screens found - aborting".  Here's the last few relevant lines from Xorg.0.log:

```

[   127.379] (II) VESA: driver for VESA chipsets: vesa
[   127.379] (II) FBDEV: driver for framebuffer: fbdev
[   127.379] (++) using VT number 7

[   127.379] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[   127.379] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   127.379] (II) [KMS] Kernel modesetting enabled.
[   127.379] (WW) Falling back to old probe method for vesa
[   127.379] (WW) Falling back to old probe method for fbdev
[   127.379] (II) Loading sub module "fbdevhw"
[   127.379] (II) LoadModule: "fbdevhw"
[   127.379] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   127.379] (II) Module fbdevhw: vendor="X.Org Foundation"
[   127.379]    compiled for 1.10.4, module version = 0.0.2
[   127.379]    ABI class: X.Org Video Driver, version 10.0
[   127.379] (II) RADEON(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   127.379] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   127.379] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   127.379] (==) RADEON(0): Default visual is TrueColor
[   127.379] (==) RADEON(0): RGB weight 888
[   127.379] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   127.379] (--) RADEON(0): Chipset: "AMD Radeon HD 6900M Series" (ChipID = 0x6720)
[   127.379] (II) RADEON(0): PCIE card detected
[   127.379] drmOpenDevice: node name is /dev/dri/card0
[   127.379] drmOpenDevice: open result is 12, (OK)
[   127.379] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   127.379] drmOpenDevice: node name is /dev/dri/card0
[   127.379] drmOpenDevice: open result is 12, (OK)
[   127.379] drmOpenByBusid: drmOpenMinor returns 12
[   127.379] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   127.379] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   127.379] (EE) RADEON(0): [drm] failed to set drm interface version.
[   127.379] (EE) RADEON(0): Kernel modesetting setup failed
[   127.379] (II) UnloadModule: "radeon"
[   127.379] (II) Unloading radeon
[   127.379] (EE) Screen(s) found, but none have a usable configuration.
[   127.379] 
Fatal server error:
[   127.379] no screens found
[   127.379] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[   127.379] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   127.379] 
[   127.383]  ddxSigGiveUp: Closing log

```

---

### Post by drs305 on 2012-01-12
I am not a video guru. That being said, I do see a line about modesetting failing. 

You can place a kernel option in Grub 2 to disable modesetting every time. You might try this once to see if it boots. If it does, and your video works satisfactorily, you can incorporate the 'nomodeset' option permanently in /etc/default/grub  on the GRUB_CMDLINE_LINUX_DEFAULT= line.

If it doesn't boot, then you will at least know that the problem may be with your video drivers.

To add the nomodeset option temporarily to see if it affects your boot, at the grub menu press 'e'.

Cursor to the 'linux' line, go to the end, remove 'quiet splash' and add 'nomodeset'. 

CTRL-x to boot.

This change is not persistent. You would have to repeat it or add the nomodeset option to /etc/default/grub, save the file, then run "sudo update-grub". 

Normally users with video problems who are able to boot with this option then install their graphics drivers and no longer need the 'nomodeset' option.

---

### Post by drs305 on 2012-01-12
I am not a video guru. That being said, I do see a line about modesetting failing. I don't know why it would fail only intermittently.

You can place a kernel option in Grub 2 to disable modesetting every time. You might try this once to see if it boots. If it does, and your video works satisfactorily, you can incorporate the 'nomodeset' option permanently in /etc/default/grub  on the GRUB_CMDLINE_LINUX_DEFAULT= line.

If it doesn't boot, then you will at least know that you need to load the problem may be with your video drivers.

To add the nomodeset option temporarily to see if it affects your boot, at the grub menu press 'e'.

Cursor to the 'linux' line, go to the end, remove 'quiet splash' and add 'nomodeset'. 

CTRL-x to boot.

This change is not persistent. You would have to repeat it or add the nomodeset option to /etc/default/grub, save the file, then run "sudo update-grub". 

Normally users with video problems who are able to boot with this option then install their graphics drivers and no longer need the 'nomodeset' option.

---

### Post by Tamale on 2012-01-12
Thanks so much, I'll give that a try and let you know if it works.

---

### Post by Tamale on 2012-01-20
Sorry this took so long, but setting 'nomodeset' made it fail every time.

Any other ideas, anyone??

---

### Post by Tamale on 2012-01-26
help???

---

### Post by Tamale on 2012-02-06
It's gotten worse after another apt-get update / upgrade.

Now I can't boot at all, ever.  Please assist.. for now my only workaround is to boot into windows 7 and run ubuntu in a virtual machine.. which is HARDLY the same!

---

### Post by drs305 on 2012-02-06
Perhaps this link by forum member *MAFoElffin* will help:
[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank")

---

### Post by Tamale on 2012-02-06
> **drs305 said:**
> Perhaps this link by forum member *MAFoElffin* will help:
[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank")

That's a pretty awesome guide, but seems to be very out of date (still references gdm instead of lightdm) and unfortunately doesn't have much detail for the 'checking battery state' issue.

I really need somoene to pour over the output of my X log and help figure out where it's going wrong.

I can't be the only one running ubuntu on a Dell precision laptop.. shouldn't issues like these be pretty basic in the list of Q/A for new releases of ubuntu?

---

### Post by drs305 on 2012-02-06
> **Tamale said:**
> That's a pretty awesome guide, but seems to be very out of date (still references gdm instead of lightdm) and unfortunately doesn't have much detail for the 'checking battery state' issue.

I really need somoene to pour over the output of my X log and help figure out where it's going wrong.

I can't be the only one running ubuntu on a Dell precision laptop.. shouldn't issues like these be pretty basic in the list of Q/A for new releases of ubuntu?

Although the original post was 10 months ago, the OP is still responding in the thread and using the latest release (and Precise). You might try posting a link to your problem in his thread with a brief explanation of you problem.

I hope you can get an answer.

---

### Post by Tamale on 2012-02-06
> **drs305 said:**
> Although the original post was 10 months ago, the OP is still responding in the thread and using the latest release (and Precise). You might try posting a link to your problem in his thread with a brief explanation of you problem.

I hope you can get an answer.

Thanks, I've linked to [http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank](http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank) for help.

---

### Post by Tamale on 2012-02-10
Looks like that thread has too much activity about issues like grub failures and bootloader misconfigurations.. I'm pretty confident this is simply an ATI driver issue.. can someone direct me to a more appropriate place for assistance?

---

