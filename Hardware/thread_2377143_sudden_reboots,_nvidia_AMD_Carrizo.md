---
title: "sudden reboots, nvidia? AMD Carrizo?"
date: 2017-11-09
forum: Hardware
---

### Post by sgian on 2017-11-09
I am currently on Ubuntu 17.10 on my computer.  Specs are below
AMD X4 845 quad core 3.5 GHz cpu
NVIDIA GT 710 graphics
4 GB RAM

I had been running the current NVIDIA proprietary driver 384.90 and the proprietary AMD CPU microcode, but this morning it was consistently crashing when I had a wine program (Rootsmagic 7) and a libreoffice 5 word processor document open.  It would work for a while, then suddenly reboot causing me to lose work.  I found nothing regarding the crash in syslog or the kernel log, but the last entry was always a typical UFW block each time.  By crash, I mean the computer would reboot without warning.  

After removing the proprietary NVIDIA driver and going back to nouveau, I have not had any more problems with sudden reboots or other crashes.  However, I want to use the proprietary driver so that I can record screencasts of minecraft and stuff, because the fps are twice as high with the proprietary driver than the open source driver.  Also the GPUtest benchmarks I ran were less than half with the open source drivers compared to the proprietary driver.  The 384 driver is the only proprietary option with the Software Sources GUI app and with the terminal command "ubuntu-drivers devices".  

I also ran KDE neon before installing 17.10, and was having trouble with the proprietary driver with KDE neon on two separate installations on the same pc.  With KDE neon, the graphics would freeze for 10-20 minutes until I ran out of patience and pressed Ctl-Alt-F1 to check the syslog.  With KDE neon, it was always a NVIDIA graphics problem listed, but not the same each time.  I don't remember specifics.  When I went back to Ctl-Alt-F7 the GUI was black showing nothing.

I have tried two different versions of ubuntu and had the above-mentioned problems, I have run memtest without issue, I have run gputest benchmarks without problems, and the only thing that works is to not use the proprietary driver.  Is there any chance left that it could be a faulty graphics card or power supply instead of a faulty proprietary driver?  I have another pc with the same GT 710 card and proprietary driver on the same KDE neon version that I tried on this computer, but that computer hasn't had any problems, so I am not completely sure it is a driver problem.

---

### Post by #&amp;thj^% on 2017-11-09
The proprietary NVIDIA drivers are still not supported under Wayland yet. When you want to install and use the NVIDIA drivers, you have to select Ubuntu on Xorg on the GDM login screen.
They are getting just a bit better with 18.04 but still far from acceptable.
I have not used the KDE session so I have nothing relevant to add for that.
Kind Regards
EDIT: Additionally you can force the GDM login screen to use Xorg generally.
To achieve this, execute:
```
 sudo nano /etc/gdm3/custom.conf.
```
Remove the # from the line # WaylandEnable=false.

---

### Post by sgian on 2017-11-10
Thank you for the response.  Last night I tried logging in with xorg and installing the nvidia 384 proprietary driver on xorg.  Then I left the computer on all night.  This morning it suddenly rebooted while using kmymoney with chromium open, but this time there is some interesting stuff in the syslog (which I don't understand but it references the gpu).  An excerpt is attached.

EDIT--the HP S2031 mentioned in the syslog is my monitor.

---

### Post by sgian on 2017-11-10
Searching again found this thread at nvidia devtalk, I guess I wasn't using the right search terms in my previous searches (not having the right error phrasing)?  Apparently nvidia-384 and nvidia-387 with 17.10 is broken at this time.  Something to do with headless start?  [https://devtalk.nvidia.com/default/topic/1025477/linux/x-org-crashes-on-ubuntu-17-10-with-driver-nvidia-384-after-upgrade/1](https://devtalk.nvidia.com/default/topic/1025477/linux/x-org-crashes-on-ubuntu-17-10-with-driver-nvidia-384-after-upgrade/1)  I'll try to manually install a prior driver, maybe 340?

---

### Post by sgian on 2017-11-11
I tried installing 16.04 (from a disk I burned back in April or May of 2016) with two different graphics cards (a gt 610 and a gt 710).  Both installations of Ubuntu failed.  So I researched my cpu and found that Carrizo architecture has been problematic on linux for a couple of years.  Here is a bug reported in May 2016 about Carrizo which never got fixed [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074)

Is there a mainline kernel I can use that isn't buggy with AMD Carrizo?  4.4 does not work for me, 4.10 (in KDE neon) is buggy for me, and 4.13 in Ubuntu 17.10 only works with nouveau but not the proprietary nvidia graphics driver.

The only AMD graphics card I have left is an old R5450 which wasn't supported well last I checked, but I might try it with this CPU to see if there are more stable results.  I am not happy with AMD since 16.04 came out, so I am reluctant to buy a new AMD graphics card to test for better stability.

---

### Post by sgian on 2018-03-30
I'm back, but this time I am on 18.04 and a GT610 graphics card with my Carrizo CPU and NVIDIA 390 proprietary driver.  I've noticed that whenever I have firefox open for a while, this computer suddenly reboots.  There is usually this error now in the log viewer
```
Unrecoverable failure in required component org.gnome.Shell.desktop
```
and 
```
Couldn't get size: 0x800000000000000e
```
in addition, 
```
$ dmesg | grep VGA[    0.109663] pci 0000:02:00.0: vgaarb: setting as boot VGA device
[    0.109663] pci 0000:02:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.884930] fb0: EFI VGA frame buffer device
[    1.346972] nvidia 0000:02:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[   25.792106] NVRM: Your system is not currently configured to drive a VGA console
               on the primary VGA device. The NVIDIA Linux graphics driver
               requires the use of a text-mode VGA console. Use of other console
```

I have two desktops running 18.04 with the proprietary NVIDIA 390 driver, but only this one with the Carrizo does sudden reboots.  I tried for several hours one morning turning off the frame buffer, but all the grub modifications I could find with my searches failed to take care of the VGA error in 18.04.  I have also turned off hardware acceleration in firefox, but that didn't help either.

---

### Post by Yellow Pasque on 2018-03-30
If it was me, I would make sure the BIOS is updated and double check the settings there.
The bug reports I've seen with Carrizo involved the integrated graphics (especially on laptops), and the symptoms were black screens, X failing to start, etc. I can't remember anything about spontaneous reboots.

> ```
[   25.792106] NVRM: Your system is not currently configured to drive a VGA console
               on the primary VGA device. The NVIDIA Linux graphics driver
               requires the use of a text-mode VGA console. Use of other console..
```

This a common warning with the Nvidia driver. I really doubt it has any relation to the issue.

> The only AMD graphics card I have left is an old R5450 which wasn't supported well last I checked

I'm not sure where you got this impression, except maybe from some ignorant users that think it's unsupported because AMD shifted support from a proprietary driver to an open source one. The 5450 is well supported with the stock radeon driver.

---

### Post by sgian on 2018-03-31
Thank you for the suggestions.  The board is a MSI A68HM Grenade with the most recent V1.4 BIOS update.  I've tried installing in either UEFI or legacy settings but no difference.  Fast boot is disabled.

I recently tried the R5450 but couldn't play Civ VI on it so I went back to the GT 610.  It did seem a little more stable with the R5450 than with the NVIDIA cards, but I only had it in for a day so it wasn't long enough to know for sure.

It rebooted again at 8:06 my time this morning even though I wasn't using Firefox.  I had Gramps and LibreOffice open, and haven't checked yet to see how much data I lost.  Nothing new showed up in the logs.

---

### Post by rbmorse on 2018-03-31
Spontaneous reboots can also be caused by memory problems.  Make sure all the memory modules are fully seated in their respective sockets.  

I use the free and open source tester "memtest86+" ( [http://www.memtest.org/](http://www.memtest.org/) ) to test memory integrity, but I don't know if it supports the Carrizo family of AMD CPUs.  Unfortunately, development of the free Memtest86 stopped some time ago. Passmark Software distributes a proprietary derivative called "Memtest86".  While they sell a "Pro" version, they also make available a "free" (i.e., no cost) version for download, but I have not used it. 

In either case, ideally, you should run the tests overnight unless the tester begins reporting errors right away. 

Any reported error (except for configuration problems that can be corrected locally) means the responsible module must be replaced.

---

### Post by Yellow Pasque on 2018-03-31
The OP already ran memtest..

> I recently tried the R5450 but couldn't play Civ VI on it

Well, it doesn't meet the minimum requirements of the game (on Linux or Windows).

>  Is there any chance left that it could be a faulty graphics card or power supply instead of a faulty proprietary driver?

Spontaneous reboot can be caused by faulty or underpowered PSU's, but it seems odd that it only happens with proprietary nvidia linux driver. I think the best place to ask about it is the Nvidia Linux forum: [https://devtalk.nvidia.com/default/board/98/](https://devtalk.nvidia.com/default/board/98/)

---

