---
title: "Booting up, all I get is a black screen that says GRUB"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2009-08-19
I needed to wipe my drives and repartition them accordingly so I did so and then installed Ubuntu to /dev/sda2 (internal harddrive). I have XP on there and didn't want to mess with it and grub so I installed grub to the external hard drive (hd1). I tried to bootup from the external drive and all I get is a screen that says "GRUB". I booted up the live cd and looked and there is no /boot/grub/menu.lst or wherever all the grub files normally are on my ubuntu partition. Did they install somewhere else or what? What is going on?

Thanks.

---

### Post by stinger30au on 2009-08-19
super grub disk should help u find out whats gong on

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by billdotson on 2009-08-19
I'll try that. However, I have a new issue now. I just decided to wipe it and install Ubuntu and grub on the external hard drive because I needed to go ahead and start a huge file operation before I went to sleep. I installed it, put grub on hd1 like I always have done and then tried to boot up. Grub error 17. This always happens when I am installing to an external drive and I normally just boot the live cd, change the /boot/grub/menu.lst so that the ubuntu is hd0 and it works fine. However, when I looked at menu.lst there was no root     (hd0,2) line in any of the Linux ones, only Windows XP (hd0,0) (should be hd1 since the booting drive is external). So I added one to each as (hd0,0)  and changed XP to (hd1,0). Rebooted, same thing. Ok, user error. Changed to (hd0,2) which is the correct ubuntu partition. What?! Still does it. Why are there no root lines in menu.lst, have they gone away for UUIDs or something. I really don't like UUIDs so far...

---

### Post by presence1960 on 2009-08-19
We need to see exactly what setup you have on there and your boot process. Boot from the Ubuntu Live CD with your external drive **_plugged in_**. Choose "try Ubuntu without any changes", when the desktop loads come back here and use the link in my signature line to download to the desktop the Boot Info Script 0.32

Once you have it on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on desktop. Paste entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by billdotson on 2009-08-20
Repartitioned and reinstalled on a logical partition. GRUB error 5 now which means: "disk geometry error." From what I have seen it *could be* that the MBR or BIOS or whatever can't boot something that far out on the drive. 

output of sudo fdisk -l:

[http://paste.ubuntu.com/256557/]("http://paste.ubuntu.com/256557/")

output of boot_info_script.sh:

[http://paste.ubuntu.com/256551/]("http://paste.ubuntu.com/256551/")

I changed XP from (hd0,0) to (hd1,0) because, technically, with GRUB on the external drive it changes. I changed the line uuid ########### to root (hd1,5) on the Ubuntu Linux entries because I have never seen a GRUB entry without those lines and it wasn't booting anyway.

Super grub disk wouldn't even read that there was an extended partition. Sudo grub-install says it cannot find /boot, but typing the following shows its location:

```

sudo grub
grub find /boot/grub/stage1
``` (or something similar)

My UUIDs:

```

18F48147F48127D8 sda1
5dd4d9a3-78e3-4487-a932-f43ad3d34d4d sda2
ef768e22-55a8-498f-bf6a-f7fc95bb3fbb sda3
6A9EA3DB18F29E67 sda4
e768bd6e-9cdc-49e1-8a6c-d612776fb24a sdb1 
20db4ece-3786-4045-9814-781656533554 sdb2
9c9df884-0b6c-4ab0-a6d8-8420ada7d340 sdb5
f016c527-878c-421e-a406-6beb98159da4 sdb6
3688cd6a-e164-4ebc-b703-1a97eb6b36ec sdb7

```

I don't know a ton about bootloaders or GRUB but really, this stumps me. I thought GRUB was able to boot from a logical partition (also implies being able to read them unlike super grub disk).

---

### Post by presence1960 on 2009-08-20
well we can go round & round all night and say what it may be or what this could be. Why don't you run the boot info script so we can see exactly how your machine is setup and it's boot process. What do you have to lose.

P.S. sorry I see you put it iup as a link...my bad

---

### Post by presence1960 on 2009-08-20
GRUB is installed to the MBR of your external disk and looks to partition number 6 which is correct. But Grub is also installed to MBR of your sda disk but looks on partition 3 of sdb which is why you get a GRUB error.

Here is what I would do. If your machine can boot from USB all you need to do is restore the Windows bootloader to MBR of sda by doing [this]("http://ubuntuforums.org/showthread.php?t=1014708"). Do this with external unplugged!

when done boot with your external unplugged and see if windows boots. if it does reboot one more time and go into BIOS and set your USB disk to boot ahead of your internal disk. This will allow windows to boot when the external is unplugged and will allow GRUB to take over when you boot with the external plugged in. Then you can boot into Ubuntu.

Currently the GRUB on sda is taking over when you boot and it points to sdb3 , when it should be pointing to sdb6.

Or option #2:

If your machine can't boot from USB do this with external plugged in:
> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,5)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,5)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR of sda, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

then boot into ubuntu & open a terminal and run this command > gksu gedit /boot/grub/menu.lst That is a lowercase L at the end.
Scroll down the bottom to your windows entry and change it to this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1

Note : for this option you do not have to set external to boot before internal disk but your external will have to be plugged on boot because GRUB will look for menu.lst on sdb6. Option #1 is better.

---

### Post by presence1960 on 2009-08-20
> **billdotson said:**
> Repartitioned and reinstalled on a logical partition. GRUB error 5 now which means: "disk geometry error." From what I have seen it *could be* that the MBR or BIOS or whatever can't boot something that far out on the drive. 

Bill that is not what error 5 means.

From the GRUB Manual 0.97:

> 5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 


for errors reported by GRUB [http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

For the GRUB Manual 0.97 start page: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by raymondh on 2009-08-20
> **billdotson said:**
> Repartitioned and reinstalled on a logical partition. GRUB error 5 now which means: "disk geometry error." From what I have seen it *could be* that the MBR or BIOS or whatever can't boot something that far out on the drive. 


error 18.

---

### Post by billdotson on 2009-08-21
If error 5 is a failed sanity check and it is pointing to /dev/sdb3 then I know why (maybe). /dev/sdb3 is a partition with a unspecified/unformatted filesystem so that I can install either opensolaris, desktopBSD or PC-BSD on it later. Linux is the only OS I know that can boot from a logical partition. If that is not why I suppose I could reinstall Ubuntu again on a newly formatted ext3 partition (I don't even use 9.04 that much anymore, at least for anything moderately important as X likes to crash, livecd included and the only way to fix it is ctrl-alt-f1 and sudo /etc/init.d/gdm stop /etc/init.d/gdm start. Of course, if X crashes all the GUI apps crash with it (why does that have to be, can't there be a temporary configuration file or something to keep this from happening?) If an explorer window crashed that program is gone, not all of them (most of the time).

What I generally always do when I want to boot from a device is hit F8 to load the BBS prompt and choose what I want to boot from. 
To get my external hard drive to boot Ubuntu before all I have had to do was install grub to the mbr of the external drive, load a livecd, change the sdb and hd1 entries to sda and hd0 (and Windows if there to hd1) and it would boot. It has been a long time since something happened and the Windows bootloader got overwritten by grub. I really do not know how that happened. Oh well, aside from super grub disk not being able to view extended or logical partitions it was very helpful with the XP bootloader.

---

### Post by billdotson on 2009-08-21
Ok, whatever. Here we go. I actually created a new msdos partition table with gparted and then repartitioned the external hard drive. All I have plugged in now is the external hard drive. I installed Ubuntu to /dev/sda6 and that partition has a boot flag on it. 

Here is the output of sudo fdisk -l:

```

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11747    94357746   83  Linux
/dev/sda2           11748       20949    73915065   83  Linux
/dev/sda3           20950       24926    31945252+  83  Linux
/dev/sda4           24927       36483    92831602+   5  Extended
/dev/sda5           24927       25874     7614778+  82  Linux swap / Solaris
/dev/sda6   *       25875       28547    21470841   83  Linux
/dev/sda7           28548       31220    21470841   83  Linux
/dev/sda8           31221       33904    21559198+  83  Linux
/dev/sda9           33905       36483    20715786    b  W95 FAT32


```

boot_info_script.sh:
[http://pastebin.ubuntu.com/256890/]("http://pastebin.ubuntu.com/256890/")


This is just plain dumb, what do I have to do to boot from this, wipe it with zeros?

---

### Post by presence1960 on 2009-08-21
> **billdotson said:**
> Ok, whatever. Here we go. I actually created a new msdos partition table with gparted and then repartitioned the external hard drive. All I have plugged in now is the external hard drive. I installed Ubuntu to /dev/sda6 and that partition has a boot flag on it. 

Here is the output of sudo fdisk -l:

```

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11747    94357746   83  Linux
/dev/sda2           11748       20949    73915065   83  Linux
/dev/sda3           20950       24926    31945252+  83  Linux
/dev/sda4           24927       36483    92831602+   5  Extended
/dev/sda5           24927       25874     7614778+  82  Linux swap / Solaris
/dev/sda6   *       25875       28547    21470841   83  Linux
/dev/sda7           28548       31220    21470841   83  Linux
/dev/sda8           31221       33904    21559198+  83  Linux
/dev/sda9           33905       36483    20715786    b  W95 FAT32


```

boot_info_script.sh:
[http://pastebin.ubuntu.com/256890/]("http://pastebin.ubuntu.com/256890/")


This is just plain dumb, what do I have to do to boot from this, wipe it with zeros?

Is your machine set to boot from USB or Removable if it is capable of doing so?

There really was no need to rebuild the partition table all you needed to do was either option I gave you back in post # 7. Everything was set up OK but GRUB (pointing to wrong partition) and USB needed to be set in BIOS to boot.

You will still have a problem when you connect sda because GRUB there still points to the wrong partition. I suggested that you restore windows bootloader to MBR of sda. So restore windows bootloader to MBR of sda. Reboot & make sure windows boots. If successful reboot again and go into BIOS and set your external drive to boot before sda. GRUB will take over on boot and GRUB on sdb is pointing to correct partition. But your external must be set in BIOS to boot first or it will never boot. This way  when you boot with external plugged in GRUB will take over, when you boot without external plugged in you will boot right into windows.

I am not trying to be wise, but you are on here asking for our help, but yet you do not try what we suggest. That is counterproductive. You have tried your way and it isn't working, at least give our suggestions a try- what have you got to lose?

Maybe you need to study how GRUB works- see [GRUB 0.97 Manual]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by billdotson on 2009-08-21
I just don't understand what the huge change is between what I used to do and what I have to do now. I remember a couple years ago I put Ubuntu on the external drive, installed grub there, and changed the root (hd1,0) entries to (hd0,0) in the menu.lst. Then I would hit F8 to go to the boot menu and choose what I wanted to boot first and it would work. Heck, I believe when I wiped Hardy or Gutsy or whatever I had on here and reinstalled Jaunty and grub to the external drive it just automatically worked. Now the root entries have just disappeared and have been replaced with uuids.

You said to go into the static BIOS settings and change the hard drive boot order but I am confused as I thought the BBS was basically that except it only does it for that one time. Maybe it has to do with no matter what, the uuids always point to the same spot. 

I can't recover the regular windows bootloader as I don't have an XP install cd. This is an academic licensed build of XP so I installed it once and had to give the CD back. It is just becoming a major nuisance when I have to work like this just trying to get something to boot, almost enough to get me to saw screw it and just run a Livecd anytime I need to do some *nix utility work.

Anyway on to a response:

The machine can boot from USB hard drives and some flash drives and to do so I normally just go to the BBS menu. That is how super grub disk on the flash drive booted perfectly well. When you choose the external drive in the BBS doesn't it become, at that time, sda instead of sdb?

The /dev/sda is the external drive in this right now. After I created the msdos partition table I powered off, unplugged the internal drive and booted up and ran all that. syslinux or whatever is in the MBR for XP now. I had heard someone talking about using super grub disk and it had a Windows repair option so I did it. Boots into XP fine now.

I have never plugged and unplugged the external drive to choose boot order. The external always stays in because my backup data is there. The BBS popup has always allowed me to just choose what I wanted to boot that time without having to set anything permanently in the BIOS.

To be honest, I am really just confused as #$%&*#$%& and don't even have a clue what is going on now.

---

### Post by presence1960 on 2009-08-21
> **billdotson said:**
> I just don't understand what the huge change is between what I used to do and what I have to do now. I remember a couple years ago I put Ubuntu on the external drive, installed grub there, and changed the root (hd1,0) entries to (hd0,0) in the menu.lst. Then I would hit F8 to go to the boot menu and choose what I wanted to boot first and it would work. Heck, I believe when I wiped Hardy or Gutsy or whatever I had on here and reinstalled Jaunty and grub to the external drive it just automatically worked. Now the root entries have just disappeared and have been replaced with uuids.

You said to go into the static BIOS settings and change the hard drive boot order but I am confused as I thought the BBS was basically that except it only does it for that one time. Maybe it has to do with no matter what, the uuids always point to the same spot. 

I can't recover the regular windows bootloader as I don't have an XP install cd. This is an academic licensed build of XP so I installed it once and had to give the CD back. It is just becoming a major nuisance when I have to work like this just trying to get something to boot, almost enough to get me to saw screw it and just run a Livecd anytime I need to do some *nix utility work.

Anyway on to a response:

The machine can boot from USB hard drives and some flash drives and to do so I normally just go to the BBS menu. That is how super grub disk on the flash drive booted perfectly well. When you choose the external drive in the BBS doesn't it become, at that time, sda instead of sdb?

The /dev/sda is the external drive in this right now. After I created the msdos partition table I powered off, unplugged the internal drive and booted up and ran all that. syslinux or whatever is in the MBR for XP now. I had heard someone talking about using super grub disk and it had a Windows repair option so I did it. Boots into XP fine now.

I have never plugged and unplugged the external drive to choose boot order. The external always stays in because my backup data is there. The BBS popup has always allowed me to just choose what I wanted to boot that time without having to set anything permanently in the BIOS.

To be honest, I am really just confused as #$%&*#$%& and don't even have a clue what is going on now.

if you are going to keep the external plugged in all the time then install GRUB to the MBR of the internal disk. just be aware that if you boot without the external you will get a GRUB error!

---

### Post by billdotson on 2009-08-22
I just don't understand why I have been able to install Linux distributions and boot them from the external hard drive before. If I have GRUB installed to the external and the OS on it I can take it anywhere. If I have GRUB on the MBR of the internal I cannot. I don't know if I already said this but when I did fdisk and the boot info script the only drive I had plugged in was the external drive. This was after I unplugged the internal drive and make a new msdos partition table for it.

So, after a new partition table, having the external drive as the only one plugged in, and installing Ubuntu on the 6th partition (second logical partition) I am still getting GRUB error 5. I don't think it is possible that the problem has anything to do with the internal drive as it isn't plugged in. The only thing I can think of is that I have one partition on there that isn't empty space but it set as "unformatted". Perhaps GRUB doesn't like that. I may go ahead and install PC-BSD there like I was planning on and see. 

The partitions on my drive are not corrupted and it is a new partition table so I don't think the chance of it being bad is very high.

By the way, does anyone use grub 2.0 or is that in alpha or beta or something? Anyone know why super grub disk won't detect extended partitions? Is everyone sure that grub recognizes logical partitions (with its /boot on them)?

---

### Post by presence1960 on 2009-08-22
GRUB recognizes logical partitions as I have Ubuntu jaunty and Mint 5 on logicals (sda5 & sda7)

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14621   117443151    5  Extended
/dev/sda2           14622       17885    26218080   83  Linux
/dev/sda3           17886       25064    57665317+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d562f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48301   387977751   83  Linux
/dev/sdb3           48302       60801   100406250    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321   83  Linux
raz@raz-desktop:~$ 

```

I feel for you, especially since all your reported info looks good. Hopefully you can get this sorted out & share the problem & solution with us so maybe someone else won't have to go through this. I hope you get it fixed soon.

---

### Post by billdotson on 2009-08-22
Seriously, this is absolutely ridiculous.

---

