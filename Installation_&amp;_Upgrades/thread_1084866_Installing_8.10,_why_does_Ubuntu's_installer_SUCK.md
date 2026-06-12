---
title: "Installing 8.10, why does Ubuntu's installer SUCK?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by udbhav on 2009-03-02
I want to get rid of Vista, and install Ubuntu 8.10 on my Dell Optiplex 320.  I burned the Installer CD image, booted from my DVD rom drive and selected install Ubuntu.  The screen goes blank and nothing shows up.  I tried modifying the install command to not use "quiet" so I could see what was going on.  It seems like the bootup process hangs at "usbcore: registered new device driver usb"

---

### Post by LucaTNT on 2009-03-02
Maybe the quickest solution would be to use the alternate CD to install Ubuntu

---

### Post by udbhav on 2009-03-02
I tried that already.  Same problem with the alternative installer.

---

### Post by mlentink on 2009-03-02
[LEFT]1. In view of the fact that millions have used it with success, I would personally be reluctant to use terminology like "** why does Ubuntu's installer SUCK?".** Obviously you do not. This may say more about you than about the Ubuntu installer.
2. Generally, it is considered polite to include just a tad more detail than currenlty provided, so as to enable others to help you
3. We are not the Microsoft helpdesk here. All of us are enthousiats who volunteer to help each other.

Now...
What was it you wanted help about?


Edit:
I really want to try to be helpful, as per the rules most of us accept on this forum. If you felt I was in any way offensive, please accept my apologies. But do tell us everything needed (whether you feel it to be so or not) to enable all the good people here to help you. 
[/LEFT]

---

### Post by udbhav on 2009-03-02
Ok, so when I use the normal install cd or the alternate cd, after selecting install ubuntu in either normal mode or safe graphics mode, i get a blank screen.  If I remove the quiet option to begin the install process, the startup sequence hangs at "usbcore: registered new device driver usb."  Do you need my system specs?

---

### Post by mlentink on 2009-03-02
> **udbhav said:**
> Ok, so when I use the normal install cd or the alternate cd, after selecting install ubuntu in either normal mode or safe graphics mode, i get a blank screen.  If I remove the quiet option to begin the install process, the startup sequence hangs at "usbcore: registered new device driver usb."  Do you need my system specs?


I would think we would, yes. If I remember correctly, Windows has something called Sytem Info, or sysinfo or somesuch. I think that would be helpful. Furthermore, you may want to check whether your LiveCD was burned correctly in the first place. There's loads of information on how to do that to be found by a simple search of these forums.

---

### Post by udbhav on 2009-03-03
It's a 32 bit 1.80 GHz Intel Core 2 with 2 GM RAM.  When I try to check the CD to make sure it was burned correctly, the same thing happens.  Blank screen.

---

### Post by Dr.Suave on 2009-03-03
Try [Linux Mint]("http://www.linuxmint.com/") - it's pretty much another flavour of Ubuntu, and it might get around your bug.

---

### Post by avtolle on 2009-03-03
I'd caution that the OP may well have the same problem with Mint. To the OP: what graphics card does your computer have?

---

### Post by udbhav on 2009-03-03
Radeon Xpress 200 Series

---

### Post by cariboo on 2009-03-03
What usb device have you got plugged in that is stopping the boot process?

Jim

---

### Post by udbhav on 2009-03-05
The only USB device that is currently plugged in is this terrible Microsoft keyboard and a mouse.  I tried changing the USB port they were plugged into, to no avail.  I was going to try and use a PS/2 keyboard, but the computer doesn't have any PS/2 ports.  

Incidentally, I didn't mean to offend with the post title.  I read some stupid thing on reddit that if you bait all the kind people on these forums you get quick and detailed responses.  I just wanted to try to see if it was true.  I wouldn't actually use this method even if it did work, I was just curious.  I love Ubuntu, use it on my laptop, and am just trying to install it on my desktop at work.  Thanks in advance.

---

### Post by Therion on 2009-03-05
Can you access your BIOS and take a look at your settings? 

Of particular interest would be the EHCI settings.

---

### Post by betrunkenaffe on 2009-03-05
Personally, I'd blame the terrible keyboard and mouse combo :)

Do you have any friends that wouldn't mind coming over with theirs to test it with theirs plugged in. If it works, there's your answer, 40 bucks later and you have it installed.

---

### Post by rampage355 on 2009-04-05
This is a know issue [https://wiki.ubuntu.com/DellOptiplex320](https://wiki.ubuntu.com/DellOptiplex320)
Bad thing is that it has been around for a while, I just tried for the first time yesterday to install on my Optiplex 320 with ubuntu 9.10 beta and it really has a cow. I can get it to install using the safe graphic mode, but when reboot it locks up with a blinking cursor in the upper left corner. According to the link it is a grub issue. Hope this helps and hope they get it fixed soon.

Greg

---

### Post by jbeiter on 2009-04-06
I'm having the same problem. So there is no decent work around for this?

It looks like from that wiki page that even if you get past the installer SNAFU, the installed system is still going to be screwed up?

I've seen screwy issues with Ubuntu and Dell servers with mass storage bios... Ubuntu and Dell does not appear to be a nice combo in general.

---

### Post by rampage355 on 2009-04-06
when I get a chance I will try to install GRUB2 and see how that works, believe it or not the kids are bugging me to install it lol, only reason I have windows now is for itunes. I will report back on how that works, I not sure why they just don't use GRUB2 anyways.

---

### Post by jbeiter on 2009-04-07
Anyone know if this issue is unique to Ubuntu, or if the Optiplex has the same problem with other linux distributions like Fedora 10?

.. I'm starting to think it might be less work to install another distro.

---

### Post by Pasdar on 2009-04-07
I get the same problem on my laptop and many other people have the same problem too. I managed to get past that stuck screen though. If you remove quiet you'll most likely see the following error:

"Marking TSC unstable due to check_tsc_sync_source failed"

This problem definitely has to do with the lack of support for many ATI videocards in Ubuntu/Linux.

In 8.10 (alternate CD) you can get past this by setting "acpi=off", and then selecting text mode install. You can do that in the boot screen by pressing F6 twice and selecting acpi=off and then F4 once and selecting text mode install. Then hit enter again and it will load text mode install.

However, I wouldn't recommend any beginner to do these things. When installation is done it will boot up and X will crash, which means you have to continue configuring your system by command to make it function properly.

The Jaunty CD on the other hand doesn't need any selection of options during boot screen. You can just select LiveCD startup and X will crash at some point, any pro can then attempt to fix it.

This really sucks, because I really want to install Ubuntu on my laptop. One of the reasons is that my bluetooth device doesn't work in WIndows and it does work in Ubuntu. Its redicolous if you knew that this laptop came with VISTA. Asus says it doesnt work because of a bug in VISTA. I also tried other versions of Windows and that doesnt work either, lol... oh well...

---

### Post by jbeiter on 2009-04-07
Yes, this optiplex does have ATI graphics (onboard)  I was able to get past the install by booting with 'hpet=disable' for the kernel command line but once the system is installed, it freezes on boot.

I tried to install Fedora too, same problem.

---

### Post by upchucky on 2009-04-07
its been 4 weeks since the op posted, i suspect this thread is dead.

if the op is still trying, bump this so I know im not wasting my time.

---

### Post by Pasdar on 2009-04-07
This problem has existed for as long as Ubuntu has existed and it is still not solved. I consider it an advancement that the Jaunty CD actually continued upon boot without having to change settings, however I don't expect any miracles any time soon.

I've read that 8.10 and higher is not compatible with ATI 3470, and that 8.04 is. I'm going to attempt to install that one to see what happens, i'll keep you guys updated.

---

### Post by Pasdar on 2009-04-07
Ok, tried it with 8.04 too. Doesn't work. So I'll install Windows on my laptop again. I'll give it a try again when 9.04 final is released.

---

### Post by upchucky on 2009-04-07
hardware issues will continue to plague us until the hardware vendors are un-brainwashed of the Microsoft way of world domination. this is not an ubuntu or Linux problem, but it is a manufacturer problem. when a piece of hardware does not work I take it back and find hardware that does work, this is the only way of getting the message across to the hardware vendors that Microsoft is not a god nor is it the only game in town.


Pasdar, you may want to start your own post, it seems that you have gotten further than the op did, you probably have another issue that can be fixed since you indicated you got x to start then it crashed, this indicates a simple resolution setting.

if you are still trying, create your own thread as i will not reply to this one any more unless the original poster responds.

---

### Post by flesh.wound on 2009-04-22
It won't be any less work to install with another distro.  My 320 gave me problems on Gentoo and even FreeBSD.  There are multiple issues in the system all of which can be overcome with a little effort.

My 320 is now running almost perfectly.  Basic installation required a couple of things:  "acpi=off" and LILO as the bootloader.  After installation though there are still a few problems you may have to work through.  I have heard GRUB2 works but I can't verify that.  Apparently there is an issue with GRUB seeing the SATA drives across the controller.  There is also some quirkiness with the PATA that goes to the CDROM.  I'm still working on that and have a USB CDROM connected until that is fixed.  The "acpi=off" generally has to be used (put it in LILO) until you can get the issues resolved with that.  It took a kernel recompile for me to get past that one and get ACPI turned back on.  I have heard of hangs in a variety of places.  Mine would occur during the probing of the USB keyboard.  Most of these issues appear to be centered around the AMD/ATI SB600 chipset.  After the kernel recompile this now shows up in my dmesg:

ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround

which tells me that the kernel gurus were aware of SB600 issues and worked around them somewhere between 2.6.27 and 2.6.29.  My dmesg at this point looks very clean and I'm actually amazed at how well it is discovering everything.  It even found an 8MB NVRAM that it loaded up as /dev/sda and screwed my boot until I figured it out.  The video was a little screwy but was easily fixed by turning off the Visual Effects in Appearance Preferences.  Hopefully I'll get worked around that but it isn't a high priority.  It would also fail to recognize my 2nd core until I got everything resolved.  So even though some of you may think you have it running the way it should be, I would suggest you check your dmesg to make sure it sees the 2nd CPU before claiming victory.  It wasn't until I could get rid of "acpi=off" that it recognized #2.

For the record, mine is an Optiplex 320 mini-tower.  It is running dual-core PentiumD and I am using the AMD64 image.  Everything else is pretty much standard across the board as the 320s go:  SB600 chipset, SATA hard drives and controller, PATA-->ATAPI CD-ROM, Broadcom Ethernet.  I'm still working on trimming down my modules I'm trying to load so I can figure out what is really supported on the system.  Once I get that done I plan on posting everything I have found because it looks like if the right SB600 related drivers get installed right off the bat then ALL of the problems go away.  I may even go back and work on 2.6.27 again to see if I can get the right combination of drivers to make it work with a "nearly" stock kernel.

---

### Post by flesh.wound on 2009-04-22
And here is my "lspci" for your reference and comparison since it is not going to change.

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

