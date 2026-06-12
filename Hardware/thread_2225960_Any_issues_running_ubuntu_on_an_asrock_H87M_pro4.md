---
title: "Any issues running ubuntu on an asrock H87M pro4  ?"
date: 2014-05-24
forum: Hardware
---

### Post by hbc2 on 2014-05-24
Hi,

My basic question is in the subject line.   Some background: I need to cheaply run several simultaneous VMs (virtualbox) at home and I need vt-d.  This motherboard fits in my budget and has what I require.  I want the base OS to be linux (basically because its free and I don't want all the Windows hassles) but I've never used linux before. I've heard that ubuntu is easiest on newbies like me.   

I googled a couple things about linux and this motherboard 
1) there may be a shutdown issue (the PC restarted after shutting down) but that seems solved by a later bios (i can't now find that thread where the guy said it was fixed, though).
2) saseith says "[COLOR=#333333][FONT=Arial]The Linux driver and software support leaves something to be desired, but this has not affected the core functionality, just the ability to use some of the add-on features by ASRock such as remote management of the machine.[/FONT][/COLOR]"  ([http://www.amazon.co.uk/ASRock-H87M-PRO4-Motherboard-Generation/dp/B00CYWEYOK](http://www.amazon.co.uk/ASRock-H87M-PRO4-Motherboard-Generation/dp/B00CYWEYOK))

It would be great if someone could confirm that sound, networking, and hdmi video (and vt-d) all work before I pull the trigger. (seems that saseith confirms but i don't know if "core functionality" leaves out, say, sound or something.  )

It would be great to hear what people have to say about this motherboard.

Thanks!

---

### Post by oldfred on 2014-05-24
I have not seen anyone with that model. Always interested myself as I am planning on a new system.

Other Asrock systems:
 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by hbc2 on 2014-05-25
[FONT=arial]oldfred,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]thanks for the links.[/FONT]

[FONT=arial]Here's another thread with and issue and a possible workaround.  [/FONT]
[FONT=arial]I'm a bit concerned with this because I want to run the OS off an SSD attached to SATA3.[/FONT]

[FONT=arial]The workaround *seems* to indicate that if I just leave video shared memory to "Auto" in the BIOS all will be well (i guess at the expense of some RAM), is that your take as well?[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Asrock H87M, Ubuntu 13.10 and AHCI  [/FONT]
[FONT=arial]http://forum.xbmc.org/showthread.php?tid=177052[/FONT]
[FONT=arial]
[/FONT]---
[FONT=arial]On a positive note, it seems that VT-d will work on this motherboard:[/FONT]
[FONT=arial]"VT-d Compatible ASRock Motherboards . . . all boards based on Z87, H87, Q87 and B85 (information provided by ASRock support)" [/FONT]
[FONT=arial]http://wiki.xen.org/wiki/VTd_HowTo[/FONT]

---

### Post by oldfred on 2014-05-25
I would think that may be the case with any Intel internal video, you need some shared memory.
 If you have a video card then it would be different?

I think with SSD drives you have to use AHCI for trim to work.

He says he will have a full review shortly.Gigabyte's Z97-HD3 Z97    
[http://www.phoronix.com/scan.php?page=news_item&px=MTY5OTE](http://www.phoronix.com/scan.php?page=news_item&px=MTY5OTE)

---

### Post by vladimir13 on 2014-06-11
I just spent hours installing Xubuntu 14.04 on a rig using this very MB. A sequence of endless b$. I've been through the torture of installing ubuntu more times, but it was always rather annoying (16Gig swap partition on my 64 SSD as a hands off default? really?), this time it's more of a blocker... Can't stop progress, I guess :).

First thing, I always use USB flash disk, so maybe a pure cd with pure is would save me the trouble.
1st try: Unetbootin + xubuntu 13.10 desktop x64 - wouldnt run the installer (though it went flawlessly on my old Core2 system that would not boot the installer created by UUI)
2: Unetbootin + xubuntu 14.04 desktop x64 - no option for 14.04, so daily build selected.. installer ran ok, but system would not boot with the "Gave up waiting for root device" and a prompt. After some googling and failing to fix that by setting parameters to kernel in grub, i noticed that there is no /dev/sda1 (which was seen perfectly by the installer) and I 
3: tried to switch the drive into IDE/compatibility mode in BIOS. Now it booted, but no USB keyboard or mouse would function. PS/2 tested to work with keyboard but not with mouse, so a split cable would probably not work. Google -> unetbootin said to be culprit, 
4: 14.04 install USB created by UUI and now usb keyboard and mouse worked. But guess what...

No wired network. eth0 present, but DHCP not working, tested with 2 routers, 3 eth cables, static IP would say it is successfully connected, but no http (no www, no connection to the router web console), no ping... Hope to work around this with a wifi dongle but heck... That one remains to be cracked..

I hope this helps you decide with that board, feature-wise it looks cool and I dont expect a single glitch in windows... but forget about a use friendly installation of xubuntu... That board/hw is not that new and one would expect things to behave better..

---

### Post by oldfred on 2014-06-11
I never let system auto install as I want to be able to control partition sizes.

Plus since board is both BIOS & UEFI, I strongly suggest using gpt partitioning and have both an efi partition of 300GB FAT32 and a bios_grub unformatted 1 or 2MB for BIOS boot. If UEFI booting make sure boot flag is on the FAT32 partition as boot flag is what gparted uses to flag the efi partition with correct GUID for efi boot files.

I put swap on hard drive. If you have 8 or 16GB of RAM you may not even need swap unless editing videos, but I like to have a little like 2GB. Only if hibernating do you need swap equal to RAM in GiB not GB. And with an SSD, it should boot quick enough that hibernation does not save much anyway.

On my 64GB SSD I have two / (root) partitions. One has 12.04 which I am still using and the other is 14.04 which I am configuring but probably will not fully convert to until first point release. I alternate installs on SSD or have two that let me boot just in case.

---

