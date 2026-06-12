---
title: "Ubuntu 8.10 won't work with NVidia card and Intel D945GCNL mainboard"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by soporte_cedecis on 2009-02-23
Hi all,

I have been working with server versions of Ubuntu since 6.04, no problemo at all. I have't installed any desktop, and I have been using fairly standard hardware, once I had a problem with an Intel 965 board, had to wait 7.10 release due to problems with SATA and suchalike, but the server is working flawlessly since then. Now I am trying to install Ubuntu 8.10 with all gear and desktop, but it has been a pain in the bum. I have tried with the official Ubuntu CD, alternate CD, other distros (Fedora, Suse, Debian, Mint), other UNI*Xes like Solaris and OpenSolaris, have all kinds of problems, but cannot make the system work. If I remove the PCIExpress 16 NVidia GForce 7100 GS and boot only with the integrated Intel 82945G video card, everything works fine. If I try to boot with the NVidia card, the system freezes at boot time. Have tried lotsa fings, none worked. Tried safe video mode to install, tried to remove the card to install the system then add it again and configure the correct drivers, tried tweaking the BIOS setup, the list is very long. Thing is, when I add the NVidia card, Ubuntu keeps loading Intel drivers, even though it is disabled, then freezes, sometimes with an "aiieee", sometimes with "program terminated abnormally", sometimes with a trace way too long. It also seems that something with "udevd" (whatever it might be...) is failing to ignore Intel's card. Also, Intel's bios config is way confuse, the manual is not of any help at all, and the card is supposed to be disabled, but the system insists on loading its drivers and ignoring NVidia card. I know this is not Windows, but when I boot WindowsXP (it is a dual-boot machine), the card is there, no problem, Intel card is not present, as it shouldn't be.
I really do not know what is going on, but this should be a painless process. No system would boot with NVidia card in place. I have been able to boot the system using Intel's card as main display, tweaked X11 to change the drivers (tried restricted drivers, Envy, none worked, they say there is no NVidia card, have to install all manually), changed to NVidia in bios, put card in place and the system freezes again. I have tried acpi=off, noacpi, noapic, nolapic, all-generic-ide, irq=nommpol, nothing worked. Sometimes, after a large trace is displayed, I have a "segmentation fault". Also there is a "init: rc-default main process (5048) terminated with status 255". And if I try ctrl-alt-del, it gives me the same 255 status, and wont reboot. Again, errors may vary. Strangelly enough, this same system worked fine with Ubuntu 8.04, but now not even this version would install. I suspect it has something to do with hardware detection, but Intel does not provide support for Linux, and I have been googleing and it seems no-one has such problem. I have changed already the card to a 6200, still have the same problem, have changed hard drive, memory modules, and despaired.

I know this is too little information, but the system acts weird. With the 965 board, the error was always the same, so I was able to work it out. Now, the system just went bersek.

The hard specs are:

motherboard: Intel Newberry Lake D945GCNL
processor: DualCore Intel Core 2 Duo E4400, 2000 MHz (10 x 200)
hard drive: Western Digital WDC WD1600AABS-00PRA0 160 GB
memory: 2x 1 GB Kingston 9905316-005.A04LF
northbridge: Intel Lakeport-G i945GC
southbridge: Intel 82801GB ICH7
BIOS: Version NL94510J.86A.0033.2008.0807.1932
integrated sound card: Realtek ALC888/S/T @ Intel 82801GB ICH7 - High Definition Audio Controller [A-1]	PCI
integrated NIC: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC
integrated video card: Intel(R) 82945G Express Chipset Family
PCIExpress 16x video card: NVIDIA GeForce 7100 GS

If some more info is neede, it can be provided (sure you guys will arsk more stuff, just don't know what to post first, so many different errors).

Plz advise. It is driving me nuts.

---

### Post by cariboo on 2009-02-23
I would suggest going into the bios and checking if there is a setting to tell the system where you video card is located.

Jim

---

### Post by soporte_cedecis on 2009-02-23
> **cariboo907 said:**
> I would suggest going into the bios and checking if there is a setting to tell the system where you video card is located.

Jim

Nope, Jim, there isn't. All it gives me is the possibility to choose onboard card, pci card, pcie card or auto, but it does not work propr'ly, it only "suggests" which one should be the main card, but it does not disable the other card. It is a bit of a deadlock here, really. Have tried all possible combinations, but none work.
Thks anyway.

---

### Post by soporte_cedecis on 2009-02-24
Fellas, the problem has been solved. I booted the machine using only the Intel onboard card, reset xorg.conf to minimum standards (removed intel drivers), booted again with NVidia card in place and it worked. Then I installed NVidia drivers provided by Ubuntu, and now everything works fine. Shouldn't be like this, but anyway, nothing is perfect.
Don`t know how to close a thread or mark it as solved, but also could not find information about this. S'pose the administrators will take care of this.

---

### Post by MikeOliverAZ on 2009-03-06
I have a Gateway and it ONLY has the NVidia video and same problem but no built in Intel to use, what next?  Any hope or is this machine doomed to a windows life?

---

### Post by Jules Delespy on 2009-12-03
I know this is an aged post, but I found it as I went through much trouble installing on an affected machine, and it is likely others will find their way here in the future.
The issue is installation on machines where 1) graphics processing is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references where a solution was proposed. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. It seems reasonable to think that it is the best current solution.
The problem has existed in all versions of Ubuntu since at least version 5.10, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_...integrated.txt"]
[/URL][http://www.albertomilone.com/nvidia_int ... grated.txt]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1256691](http://ubuntuforums.org/showthread.php?t=1256691)
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
[http://ubuntuforums.org/showthread.php?t=675497](http://ubuntuforums.org/showthread.php?t=675497)
[http://ubuntuforums.org/showthread.php?t=1308919](http://ubuntuforums.org/showthread.php?t=1308919)
[https://bugs.launchpad.net/ubuntu/+sour ... +bug/55104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104")
[http://www.bikechatforums.com/viewtopic.php?p=2356664](http://www.bikechatforums.com/viewtopic.php?p=2356664)
[http://www.nvnews.net/vbulletin/showthread.php?t=128934](http://www.nvnews.net/vbulletin/showthread.php?t=128934)
[http://ubuntuforums.org/showthread.php?t=196693](http://ubuntuforums.org/showthread.php?t=196693)
[http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)
[http://ubuntuforums.org/showthread.php?t=192677](http://ubuntuforums.org/showthread.php?t=192677)
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)
[http://ubuntuforums.org/showthread.php?t=295133](http://ubuntuforums.org/showthread.php?t=295133)
[http://javadocs.wordpress.com/2008/09/2 ... -gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")
[http://ubuntuforums.org/showthread.php?t=207303](http://ubuntuforums.org/showthread.php?t=207303)
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)
[http://mepislovers.org/forums/showthread.php?t=6487](http://mepislovers.org/forums/showthread.php?t=6487)
[http://www.opensubscriber.com/message/s ... 46049.html]("http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html")
[http://ubuntuforums.org/showthread.php?t=126492](http://ubuntuforums.org/showthread.php?t=126492)

---

