---
title: "Graphics not working on HP EliteOne 800 G2 AiO with Ubuntu 16.04.1"
date: 2016-08-10
forum: Hardware
---

### Post by ericjoh on 2016-08-10
Hi,

I have recently bought a HP EliteOne 800 G2 AiO with Intel Core i7-6700 3.4G 8M 2133 4C CPU, 32 GB DDR4-2133 SODIMM (2x16 GB) RAM, 256 GB SATA 2.5 3D SSD.

When first booting it in Windows the graphics seems to work as it should. Then I have tested installed Ubuntu 14.04, Ubuntu 16.04 and Kubuntu 16.04. For all of the installations the graphics is not working correctly. The screen seems to be split in half in hight so that the whole screen is squeezed in in the upper half of the screen. Now when I upgraded all the packages on Ubuntu 16.04 (to Ubuntu 16.04.1) the screen is suddenly completely blank when the system is booted up. I can log into the desktop environment but have to type the password without seeing anything on the screen. The screen is still blank after logged into the desktop environment. I can still log in over SSH to the computer.

Any idea how I can fix the graphics so that it works? I also have the previous generation of this HP AiO computer model, HP EliteOne 800 G1 AiO, where the graphics works perfectly. I guess the problem is the graphics chip in HP EliteOne 800 G2 AiO has not a correct software driver in Ubuntu 16.04 LTS.

Thanks in advance!

---

### Post by ericjoh on 2016-08-12
When I try to figure out what kind of integrated graphic card is used I type "lspci -v" and get the following:

[...]
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06) (prog-if 00 [VGA controller])
        DeviceName: Onboard IGD
        Subsystem: Hewlett-Packard Company Skylake Integrated Graphics
        Flags: bus master, fast devsel, latency 0, IRQ 127
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 3000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [40] Vendor Specific Information: Len=0c <?>
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [100] #1b
        Capabilities: [200] Address Translation Service (ATS)
        Capabilities: [300] #13
        Kernel driver in use: i915_bpo
        Kernel modules: i915_bpo
[...]

Is it possible to get a working driver for this? Currently the screen is black after the initial BIOS information has been showed and the system is up and running. Thanks for any idea how I might get the graphics to work!

---

### Post by ericjoh on 2016-09-09
From what I understand the driver for the graphic chip (Intel Corporation HD Graphics 530 (rev 06)) is buggy and the only thing I can do, if I want to be able to run Ubuntu on the computer, is to wait and hope someone one day will provide a working driver :(

By the way, after running "apt-get update ; apt-get -y dist-upgrade" today, after not having touched the computer in a few weeks, the problem with seeing a completely black screen is gone and now I see the screen splitted in half vertically again, so something seems to have happened to the graphics driver during the last weeks for Ubuntu 16.04.

---

### Post by Yellow Pasque on 2016-09-09
Can you give the contents of /var/log/Xorg.0.log file? Use code tags (or pastebin) as it's a lot of text.

Since the hardware is really new, I'd be inclined to try a Live USB stick of Ubuntu 16.10 if it's not too much trouble (time/bandwidth):
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by ericjoh on 2016-10-12
Thanks for your reply! I just tested the latest version of Ubuntu 16.10 ([yakkety-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso")  12-Oct-2016 10:39) from a  Live USB stick and unfortunately the problem  is the same, i.e., the screen is split in half in hight so that the  whole screen is squeezed in in the upper half of the screen and the  lower half of the screen is black with different colored vertical bars.

Here is my /var/log/Xorg.0.log: [http://paste.ubuntu.com/23312836/](http://paste.ubuntu.com/23312836/)

---

### Post by Yellow Pasque on 2016-10-12
Try the generic modesetting driver

---

### Post by ericjoh on 2016-10-13
Can you please tell me how to active the generic modesetting drive? From what I can see Ubuntu 16.04 no longer uses the "xorg.conf" file, at least I cannot find it in /etc/X11/ or /usr/share/X11/. When I tried to install the package "xserver-xorg-video-modesetting" it said it is already included in "xserver-xorg-core".

---

### Post by ericjoh on 2016-10-17
Thanks to [**[COLOR=#000000]Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594") I have now added the following /etc/X11/xorg.conf:

[FONT=courier new]Section "Device"
              Identifier      "Configured Video Device"
              Driver          "modesetting"
    EndSection
    
    Section "Monitor"
              Identifier      "Configured Monitor"
    EndSection
    
    Section "Screen"
              Identifier      "Default Screen"
  Monitor         "Configured Monitor"
              Device          "Configured Video Device"
    EndSection[/FONT]

However, after rebooting the computer the screen still looks the same as before (i.e. split in half in height) :-(

Here is the new /var/log/Xorg.0.log : [http://paste.ubuntu.com/23339031/](http://paste.ubuntu.com/23339031/)

---

### Post by andreas_z on 2017-04-30
I think this is **finally** solved - see <a href="https://bugs.freedesktop.org/show_bug.cgi?id=97822>here</a>

In a nutshell, enter BIOS on startup and **disable legacy boot option** (you are highly likely booting into Linux using UEFI already, rather than legacy boot). It is really only the *option* of legacy boot, so we're not losing anything by disabling this option.

This should solve the split-screen problem - it did for me.

[For everyone who still likes to use legacy boot, you may want to consider switching to UEFI for this machine (EliteOne 800). This should be far simpler than trying to solve this problem which likely has to do with some firmware issue in the presence of legacy boot option]

---

