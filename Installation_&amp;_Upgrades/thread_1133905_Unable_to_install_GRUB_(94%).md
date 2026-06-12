---
title: "Unable to install GRUB (94%)"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by QueenZ on 2009-04-23
I'm installing Ubuntu 9.04 from Live CD (USB Flash). I'm installing it over my Fedora 10 that I've been testing this month. OK, so after the installation process - 94% (Installing GRUB boot loader) Running "grub-install /dev/sda"... it shows this message..

============================================
**Unable to install GRUB in /dev/sda**
Executing 'grub-install /dev/sda' failed

This is fatal error.
============================================

Screenshot: [http://i42.tinypic.com/x4f32v.jpg](http://i42.tinypic.com/x4f32v.jpg)

Then I click OK and the installation window goes away and Application problem window shows up where i can report the problem..

**Content of the report:**
Title: ubiquity crashed with InstallStepError in configure_bootloader()
PackageArchitecture: i386
ProcCmdline: /usr/bin/python /usr/lib/ubiquity/bin/ubiquity gtk_ui
SourcePackage: ubiquity
MediaBuild Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
UbiquityDebug: (binary data)
ProcEnviron: Error [Errno 13] Permission denied: '/proc/20731/environ'
ExecutablePath: /usr/lib/ubiquity/bin/ubiquity

Screenshot: [http://i44.tinypic.com/dxolrk.jpg](http://i44.tinypic.com/dxolrk.jpg)

I have 50GB HDD:
44.6 GB is for my Windows Vista
11 GB is for Ubuntu that I am trying to instlall
196 MB is for SWAP space

I have tried to install it many times, sometimes with Ext3 and sometimes with Ext4 but always get the same results..

My installation summary looks like this..

>  Language: English
 Keyboard layout: USA
 Name: QueenZ
 Login name: queenz
 Migration Assistant:

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #2 of SCSI1 (0,0,0) (sda) as swap
 partition #3 of SCSI1 (0,0,0) (sda) as ext3

I think that it installs the system but just doesn't install GRUB which means that i can't get into any of my current installed OS's.. Maybe I just need to install GRUB but I'm not sure if it completed installing the system.. And what happened? Why couldn't it install GRUB? What am I gonna do now? :(

---

### Post by QueenZ on 2009-04-23
This time i unchecked Install GRUB option and the installation went fine but now i don't have GRUB.. How can i get it?

---

### Post by QueenZ on 2009-04-23
Any ideas..?

---

### Post by QueenZ on 2009-04-23
root@ubuntu:/home/ubuntu# grub-install /dev/sda3
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu#

---

### Post by lo900 on 2009-04-23
I have the same problem at the last stage of installation (grub)
it did not create initrd; and it did not create "grub" folder under boot
(i want it to create the boot loader under /dev/sda11 and chain boot it like my other installations on the same laptop)
now booting to /dev/sda11 gives grub error 13

i am thinking to boot from live CD and manually install grub as:

root hd(0,10)
setup hd(0,10)
 
but I'm not 100% correct about it, waiting for any help pls.

---

### Post by Eloquence on 2009-04-23
Hi Guys,
Had this same problem installing EEEBuntu to my Samsung NC10. Here's what I did to get it to work:

Upon boot of the LiveCD / LiveUSB whatever:
[LIST]
[*]Put the following at the end of the boot sequence before quiet splash or the like: noacpi acpi=off
[/LIST]

This will turn the ACPI off that interferes with the GRUB loading sequence in the installer. 

You can still specify what partition/what drive you want GRUB to be installed on.

Worked like a charm for me. Let me know if it works for you.:)

-Elo

---

### Post by lo900 on 2009-04-23
many thanks, I will re install it now with this added first and I'll report back.

---

### Post by fourwheeldrifter on 2009-04-23
> **Eloquence said:**
> Hi Guys,
Had this same problem installing EEEBuntu to my Samsung NC10. Here's what I did to get it to work:

Upon boot of the LiveCD / LiveUSB whatever:
[LIST]
[*]Put the following at the end of the boot sequence before quiet splash or the like: noacpi acpi=off
[/LIST]

This will turn the ACPI off that interferes with the GRUB loading sequence in the installer. 

You can still specify what partition/what drive you want GRUB to be installed on.

Worked like a charm for me. Let me know if it works for you.:)

-Elo
i have the same problem as the original poster

i tried this instructions (using the 64bit version) and it still failed with the exact error as before

---

### Post by lo900 on 2009-04-23
no dice, it is the same.
if I install after I boot to live session, I get at the end "configuring hardware" then the error "ubiquity crush" (bug report sent)

---

### Post by hiec on 2009-04-23
Maybe you could try to install GRUB by hand? I'm rather new to linux and Ubuntu, but since nobody else proposed something I thought you could try that.
There are quite a few How-tos that explain how to install GRUB manually. Just use google.
If you try that, always remeber that GRUB starts to count partitions and devices with 0, so usually /dev/sda1 is hdd0 for Grub, /dev/sda2 is hdd1 and so on.

---

### Post by Rmc22 on 2009-04-23
I've got a similar problem, I've not found an answer either, let me know if you find one!!

[http://ubuntuforums.org/showthread.php?t=1129019]("http://ubuntuforums.org/showthread.php?t=1129019")

---

### Post by lo900 on 2009-04-23
I thought about doing it manually; even copy the missing /boot/groub from another distro I have. but the installation create these file only in /boot, and I do not know how to create the missing initrd file manually, or if anything else missing.

this how far it reached before it stoped:

/boot
total 5612
-rw-r--r-- 1 root root  529118 2009-04-17 07:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   96795 2009-04-17 07:41 config-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-03-27 21:15 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-17 07:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-17 07:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501776 2009-04-17 07:41 vmlinuz-2.6.28-11-generic

---

### Post by fourwheeldrifter on 2009-04-23
i also tried manually, i got errors that it couldnt write to boot or that it was a block device, interestingly enough, if i were to be able to run any sort of bootloader that could get me into ubuntu it would actually be ready to run, its just grub causing issues, i wonder if it is the new grub thats meant to be able to boot ext4 causing the issues?

---

### Post by lo900 on 2009-04-24
ok, this is not a solution for this problem, but this is how I have done it.

- after a fresh install on /dev/sda11 finished and grub stage failed

- I've copied /boot from fedora installation I have on the same laptop over to 9.04 /boot folder, and I have edited the menu.lst to reflect the 9.04 root partition (hd0,10) 

- now I reboot, an it works (but fedora has kernel 2.6.27.11) so I want the new 9.04 kernel 2.6.28 to be the one I have, so from Synaptic I re-installed all that I can see already installed with 2.6.28 in it (I do not know which one created the "initrd.img-2.6.28-11-generic" at the end, but it is done so I am good.

- I've copied /boot to USB (because I want to use it later)

- I have done a new clean installation again in the same partition

- at the end I copied the saved /boot/grub and "initrd.img-2.6.28-11-generic" from USB over to the new 9.04 installation and fixed "menue.lst" in it to point now to the 2.6.28 kernel

- from live-CD run setup grub "root (hd0,10) -- then setup (hd0,10)"

- rebooted, and here I lived to tell the story from my new 9.04 WORKING installation.

These steps may not work with you as it has for me.

---

### Post by QueenZ on 2009-04-25
This is how I solved this problem..

I made 2 new and clean partitions (NEW) - 1 for system and another for swap and it worked...

---

### Post by fourwheeldrifter on 2009-04-26
my solution was downloading the alternate cd and letting it install lilo after it falls back to the installer menu when grub fails

i think this is something ubuntu need to fix

---

### Post by Shmoo on 2009-05-10
> **fourwheeldrifter said:**
> my solution was downloading the alternate cd and letting it install lilo after it falls back to the installer menu when grub fails

i think this is something ubuntu need to fix

I'm going to try this now. I assume you're talking about the text based alternative, that's the only alternate choice I see. I've tried so many things trying to fix this error. I think the problem is my computer has no master or slave drive, it only has a SATA drive, which seems to confuse Grub? 

Anyway I'll report if this fixed it for me too, I sure hope so.

---

### Post by Shmoo on 2009-05-10
I got to 76% partitioned with the alternate CD, and then it wanted me to switch out with another Ubuntu CD, is that normal? I have the normal Ubuntu CD but my computer wouldn't even let me open my CD drive.

---

### Post by harveywb on 2009-05-17
I have had the ubiquity error in 8.10 and 9.04. I got by it using the alternate version of Ubuntu. Seems like a video problem. After installing the alternate version all was well. Good luck.

---

### Post by presence1960 on 2009-05-17
to restore GRUB  follow this :

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

---

