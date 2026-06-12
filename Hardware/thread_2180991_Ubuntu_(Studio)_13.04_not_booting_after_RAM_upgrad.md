---
title: "Ubuntu (Studio) 13.04 not booting after RAM upgrade"
date: 2013-10-15
forum: Hardware
---

### Post by JsweheX on 2013-10-15
Hi guys,

I have an early 2008 MacBook (hardware specs appended at the end of this post) which I successfully dual booted with Ubuntu Studio 13.04 alongside OS X 10.6.8 some time ago. When I initially dual-booted, I had already added a second hard drive (Crucial M4 SSD 128GB) alongside the stock 5400RPM 160GB HDD and I additionally upgraded 1 of 2 1GB sticks to a 4GB stick with the proper specifications (667 MHz DDR2 SDRAM (PC2-5300)) for a total of 5GB. I finally got around to upgrading the other 1GB stick to a 4GB stick of the recommended RAM for a total of 8GB. This is when my problems started.

Upon booting up the computer, rEFInd interrupted the boot process as normal and gave me the option to boot into either OS X 10.6.8 or Ubuntu Studio 13.04. I selected Ubuntu Studio 13.04 and GRUB loaded as normal. I selected the standard Ubuntu boot and I got a blank screen. I waited about 30 minutes and absolutely nothing happened.

My first thought was that it was bad RAM. So, I rebooted and selected my rarely used OS X partition. It loaded with absolutely no problems and booted up. Using Apple's System Profiler, I checked my computer's stats and sure enough, 8GB of RAM was displayed (and OS X running much faster than it used to). Obviously I rebooted and tried to load up Ubuntu Studio 13.04 once again.

Upon rebooting, all normal steps of my computer's boot-up process happened. Once I selected Ubuntu from the GRUB menu, I got a blank screen. After ~1 hour, the loading screen for Ubuntu Studio 13.04 appeared and was seemingly functional, but working at a snail's pace. I put the computer in it's place and went to sleep. Upon waking up I checked it and surely enough the login screen had appeared. I attempted to type in my password, but nothing appeared. After waiting a few minutes the password text that I typed in appeared and I tried to login, but the mouse was moving so slowly that I tried to use TAB to get there (with no response).

I rebooted once again, and tried to boot into recovery mode. The output of recovery mode appeared rather quickly, but eventually glitched out and the text got garbled. After waiting about half an hour, the screen had reached a static state where I could make out a garbled menu which had some selections (which were not at all readable).

I restored the RAM to it's initial configuration (4GB+1GB) and booted into Ubuntu Studio perfectly I also tried using the new 4GB stick of ram in conjunction with the old 1GB stick, and that worked as well.

I now have the 2 4GB sticks inserted into the computer and now have a black screen with nothing, not even a cursor, and it is doing it's horrendously slow booting process again (upwards of 15 minutes to even see the loading screen...waiting on login as I've typed up this post).

Please help me! I am guessing I am going to have to enter a command either in the EFI boot instructions, or somewhere in the script Ubuntu uses to startup. However I am a complete n00b when it comes to hardware issues, as it is my first time dealing with them.

Other tidbits:

[LIST]
[*]    GRUB bootloader has no option for performing a memtest due to the MacBook's EFI boot process.
[*]    Recovery modes glitch out entirely as described.
[*]    Previous installations of Ubuntu Studio have the same problem as current.
[/LIST]

MacBook 4,1 Hardware Specs:
"Penryn" 2.4 GHz Intel Core 2 Duo Processor w/ 3MB shared L2 cache
Intel GMA X3100 Integrated Graphics Processor with 144MB of DDR2 SDRAM
160GB 5400RPM HDD
128GB Crucial M4 SSD
2x4GB 667 MHz DDR2 SDRAM (PC2-5300)
Note: Some sources say the processor can only accomodate 6GB of RAM, but other sources say it can handle 8GB. Considering the OS X partition only shows increased performance with 8GB of RAM, I am guessing that the processor/mobo can accomdate 8GB.

EDIT1: I have searched the forums, and other forums, thoroughly for a solution to my issue. None of the threads marked [solved] that referred to slow boot times after a RAM upgrade were relevant to my situation.

---

### Post by JsweheX on 2013-10-15
EDIT: Thought I had it solved. I didn't. One of the RAM sticks wasn't fully inserted. I was only showing 4GB when successfully booting.

---

### Post by Yellow Pasque on 2013-10-16
6GB max, so it's not going to work.
[http://forums.macrumors.com/showthread.php?t=1350570](http://forums.macrumors.com/showthread.php?t=1350570)

---

### Post by JsweheX on 2013-10-16
> Note: Some sources say the processor can only accomodate 6GB of RAM, but  other sources say it can handle 8GB. Considering the OS X partition  only shows increased performance with 8GB of RAM, I am guessing that the  processor/mobo can accomdate 8GB.

.

---

