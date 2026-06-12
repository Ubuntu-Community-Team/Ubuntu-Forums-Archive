---
title: "Odd freezes"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by Linkofpower on 2006-03-21
I've been having trouble with freezes since install -- but by turning off my computer for a few hours i managed to get enough of it installed to rescue it through synaptic.

Trouble is, now when doing cpu intensive things like using automatix, or the screensaver.. it just randomly freezes

i've got 1 gig of ram, and am using a 2.8 ghz p4.. shouldn't be happening

---

### Post by akudewan on 2006-03-21
Is it a total freeze up? Does the Num Lock LED work? Can you do "ctrl + Alt +F1" to go to the terminal ?

---

### Post by tseliot on 2006-03-21
Please post the model of your motherboard

---

### Post by Linkofpower on 2006-03-21
Yes, complete lockup, numlock turned off, no response at all; just like during startup..

and as for my motherboard.. I supposea printout of lscpi will work? no idea how to go about it other than that

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 82)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by falloutvictim on 2006-03-21
I'm having the same problem, only it just started on a fresh install after XP hosed.  I'm running a soyo kt400 ultra with and xp2400 processor and a ati radeon 9250 pci graphics card.
I first installed XP, which I couldn't boot into after I installed breezy.  So, I wiped the hard drive and started over without XP.  So Breezy was running fine for a full day, then the monitor just shut off.  The system was still running fine!  My music was playing perfectly.  So I shut down manually since there was no response from any key combinations.  Restarted to the strangest pixelated screen I've ever seen, with huge green globs all over the place on the terminal start up screens.  So I thought there was a video problem, and proceeded to install the ATI drivers three different ways (via the automated install ATI offers (ICK!), via a line by line instructional tour on this forum (see radeon 9800 install), and via an fglrxconfig and some manual xorconf editing).  With new drivers, I could get all the way into Gnome, but it would freeze, either opening synaptic, or terminal, or on log out (which were the only apps I tried).  With the fglrx installed and edited in the xorgconfig file, it would freeze when I logged in, and it would only show half the Gnome desktop.  
So that's where I am.  I'm having a hard time doing anything without a total lock up.
Any ideas would be most appreciated.
Thanks

---

### Post by tuxinvader on 2006-03-21
If it happens after it's been running for a while it could be cooling problems

Next time it locks reset it and check the CPU and system temps in the BIOS. Perhaps you're cpu fan is dying? Is it a new system?

Have you tried running memtest (3rd option in Grub bootloader) to check it's not a dodgy dimm?

---

### Post by Linkofpower on 2006-03-21
[QUOTE=tuxinvader]If it happens after it's been running for a while it could be cooling problems

Next time it locks reset it and check the CPU and system temps in the BIOS. Perhaps you're cpu fan is dying? Is it a new system?

Have you tried running memtest (3rd option in Grub bootloader) to check it's not a dodgy dimm?[/QUOTE]


i'm thinking cooling problems too.. but that doesn't explain why suse runs and installs with 0 problems, while every other distro/os i've tried freezes during install and only works buggily.. plus it's been cold as hell ehre the past few days.. don't see how it could be over heating (normally the room gets hot when it does)

as for memtest -- I ran it from teh gentoo live cd.. got to 12% on the  third test and stopped working, whereas the cursors and + were still blinking, but the machine wasdoing nothing and was unresponsive.. but I removed each stick of memory with no results.. and I don't have another stick to try to see if thats the problem

and if it makes any difference -- it freezes halfway through copying portage on gentoo install, if I turn it off it gets to compiling the kernel; but freezes halfway through installing (again wierd as i've compiled a kernel on suse with no problems).. and after a few crashes it won't even load the terminals (if your familiar with it, it has 3 choices (two kernels and memtest) it load it, then gives you 6 terminals on f1-f6 and a live cd area to work with ti install and bootstrap the system) it just says it's loading.. then goes to a black screen

---

### Post by tseliot on 2006-03-21
All of you: Can you try to disable "apic"?

You can do it from the Bios or following this guide of mine:
[HOWTO: Double Clock Speed Problem]("http://www.ubuntuforums.org/showthread.php?t=75281")

follow this section: "b) If you have installed Ubuntu..."

and use "noapic nolapic" as boot parameter (it's all explained in my guide).

I hope it helps.

P.S. An upgrade of the BIOS might help you as well

---

### Post by Linkofpower on 2006-03-21
doesn't seem to be that problem, as I run ~8-15% with firefox and synaptic running.. as for the bios -- gladly do so.. but I have no idea how to find the model of my motherboard to start looking >_>

---

### Post by tseliot on 2006-03-21
[QUOTE=Linkofpower]doesn't seem to be that problem, as I run ~8-15% with firefox and synaptic running.. as for the bios -- gladly do so.. but I have no idea how to find the model of my motherboard to start looking >_>[/QUOTE]
I didn't say you have the problem my guide is about. I need you to pass "noapic nolapic" at boot and my guide explains how to do that. That's all.

Disabling APIC can do the trick (sometimes).

---

### Post by Linkofpower on 2006-03-21
ahh, gotcha.. my bad.. testing now...

edit: ran automix; told it to install wine -- downloads slow as hell; therefore good strenous test -- froze at 1%... seems it was a failure

---

### Post by tseliot on 2006-03-22
[QUOTE=Linkofpower]ahh, gotcha.. my bad.. testing now...

edit: ran automix; told it to install wine -- downloads slow as hell; therefore good strenous test -- froze at 1%... seems it was a failure[/QUOTE]
Downloading wine is very slow (I know it).

Did only Automatix or your entire computer freeze?

---

### Post by Linkofpower on 2006-03-22
The entire thing froze, no response, and all of the lightso n the keyboard turned off.. Happens whenever I do something cpu intensive -- like automatix, or untarring large amounts of

---

### Post by akudewan on 2006-03-22
Have a look at /var/log/messages. does it have anything interesting around the time of a hang? Seems like an overheating problem to me.

Edit: Not so sure if its overheating (I read the thread again). None the less, /var/log/messages may have something

---

### Post by jbcola on 2007-10-17
I've got a similar problem... 
The system freezed during openarena, i think it's linked with the VT6420 on the Mobo, the lspci output is also posted:

Here is the content of the /var/log/messages file
Oct 17 20:52:09 desktop kernel: [ 4737.991526]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 17 20:52:09 desktop kernel: [ 4737.991544] ata1: soft resetting port
Oct 17 20:52:10 desktop kernel: [ 4738.158082] ATA: abnormal status 0x7F on port 0x000000000001d407
Oct 17 20:52:10 desktop kernel: [ 4738.169381] ATA: abnormal status 0x7F on port 0x000000000001d407
Oct 17 20:52:13 desktop kernel: [ 4741.903907] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
Oct 17 20:52:19 desktop kernel: [ 4747.381531] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
Oct 17 20:52:19 desktop kernel: [ 4747.381541] ata1.00: configured for UDMA/133
Oct 17 20:52:19 desktop kernel: [ 4747.381557] ata1: EH complete
Oct 17 20:52:47 desktop kernel: [ 4775.936516] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Oct 17 20:52:51 desktop kernel: [ 4779.769404] sda: Write Protect is off
Oct 17 20:53:08 desktop kernel: [ 4796.307913] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 17 20:58:52 desktop syslogd 1.4.1#20ubuntu4: restart.
_______________________________________________________________________
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0e.0 Network controller: AVM Audiovisuelles MKTG & Computer System GmbH Fritz!PCI v2.0 ISDN (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 02e0 (rev a2)

Best regards,
Jean-Luc

---

### Post by SneakyWho_am_i on 2008-03-27
Hey....

I had the same problem for some time. Not just with CPU intensive tasks but if I left it on at night sometimes it would lock up before I woke.

Do you still have your installation CD?

Set aside all ideas of incompatible hardware, kernel messages etc etc etc for the time being.
You said you have 1GB of RAM - the more RAM you have, the higher the chance that some of it is dodgy. Random crashes are a textbook example of something that MIGHT be caused by "bad" RAM.

SO

Stick your install CD in the drive, and reboot.
Select "memory test" or whatever it's called, to run Memtest86+

Walk away. The test will take 999,999,999,999 years to complete, due to your largeish amount of RAM. Try to be patient. It's worth it. Even if it passes the first 7 test with flying colours, it might show errors on the 8th - and that's enough to do what you're talking about - so make sure it completes all the tests.


If your rRAM is healthy, breathe a sigh of relief - it's one less thing to worry about. If not, that's a shame. Don't throw it away yet cause it's now the 21st century.
[http://google.com/linux?q=badram](http://google.com/linux?q=badram)
I think that that url will do it; go from there, I hope it helps you.
Good luck.

---

