---
title: "Cannot install Ubuntu (or any other Linux) on Clevo M860TU Barebone"
date: 2008-10-21
forum: Hardware
---

### Post by sv2dgi on 2008-10-21
Also posted as [bug 285768]("https://bugs.launchpad.net/ubuntu/+bug/285768")

**Machine specifications**: (nfo file attached in bug report)
CPU: Intel Core 2 Duo T9400
Chipset: Intel PM45 + ICH9M
Memory: 4GB DDR3-1066
Disk: WD Scorpio 320GB SATA
Optical: DVD writer SATA
Video: NVidia GeForce 9600M GS
Audio: Intel HD
LAN: Realtek 8168C/8111C 1Gbps Ethernet
WIFI: Intel 5100 AGN
Camera(USB-Internal), Fingerprint sensor, Bluetooth(internal)
Disk was partitioned during Windows install as follows:
80GB Windows | 80GB for Linux Root | 200M for Linux Boot | 150 GB NTFS for data

Windows boots Ok, runs ok, no problem.
Tried to install x64 Linux. LiveCD AND AlternateCD boot ok, show menu, I select Install (or Run Live) and after 2 seconds without having time to read what the screen says other than an "irq storm..." it reboots.
Tried to add parameters "acpi=off, noapic, nolapic, nofb" in all combinations, system moves forward, but locks after showing "io scheduler cfq". I left it for 10 minutes there - still locked. Tried to add DEBUG_something to the kernel line, which was supposed to show more info - but I get the same messages.
I tried both 8.04 (Hardy) and 8.10 (Intrepid). Same results. I tried the startup CD of OpenSUSE 11 - exactly the same behavior. So it must be something with the kernel itself. All tests were made with 64-bit OSes. Vista running on machine is Business-64bit.
I saw that some systems had problems with Fedora and problems were gone with BIOS update. But there is no new BIOS for my machine as far as I know.
Its BIOS has limited entries. I tried playing with them - same results. Disk boots in AHCI mode for Windows, I tried both SATA and AHCI - no change. I tried also enabling / disabling EFI - still no change. Finally I search for any APIC or ACPI settings in BIOS but there are none. There is also an option in BIOS (which mainly enables/disables AHCI) that asks what OS you will boot (Vista/XP/Other) and I tried all three settings.
I am stuck with Windows and an empty partiton waiting for Ubuntu...
Since I could not see bash in ANY linux I tried up to now, to do any lsusb/lspci etc commands, I attach the .nfo file from Windows Vista.

I contacted Clevo support and I received the following: (English is as I received it - not corrected or mistyped...)

Hi:
There isn&#8217;t a BIOS update for this yet. All the Clevo computers are not officially support Linux any way. 

Best Regards
 
Goldenstar Computer UK Ltd
Service Team

(Just keep in mind in case you will buy one...)

---

### Post by sv2dgi on 2008-10-23
Update:
I have tried Gentoo, which has a parameter "DEBUG" which lets you in a busybox just before initrd runs.
Linux kernel seems OK, stable, without any parameters that affect ACPI or APIC. Disk is detected.
BUT, after I exit busybox, lots of things pop up and then I get a:

CPU T9400 blah blah blah blah
Unpacking firmware....
And then the reboot! Is it possible that CPU does not get a correct microcode file?

---

### Post by bhaskar on 2008-10-23
I have one of these rebranded and sold as Xtreme Notebooks Raptor 560x.

1. You will need Ubuntu 8.10 or Fedora Core 10.  Ubuntu 8.04 comes up in 800x600 mode.  It runs very well with *32-bit* Ubuntu 8.10.

2. With 64-bit Ubuntu 8.10 or Debian Unstable install CD, it boots, streams text too fast for me to read.  Then reboots.  It happens too fast for me to read.  This happens with the Fedora Core 10 live CD too.

3. With Fedora Core 10 installer DVD (not the live CD), I am able to install successfully, but then it does the same infinite hard reboot loop.  If I disable the cpufreq startup, then I can successfully boot and run in 64-bit mode, but then I can't shut down - a shutdown attempt goes into the hard reboot.

The best advice I have had is to wait 6 months and try again.

---

### Post by Sef on 2008-10-24
> I contacted Clevo support and I received the following: (English is as I received it - not corrected or mistyped...)

Hi:
There isn&#8217;t a BIOS update for this yet. All the Clevo computers are not officially support Linux any way. 
Then I would write them a note and tell them politely that you will not be buying nor recommending their products to your friends.

---

### Post by cdukes on 2008-11-24
Disable ACPI in the bios and pass acpi=off in the boot statement

---

### Post by JagerQ on 2009-01-07
I'm running Ubuntu x64 on this by using a mem=XXXX flag but I can't access the full 4GB of ram. So mem=4096m gets me 2508m total

---

