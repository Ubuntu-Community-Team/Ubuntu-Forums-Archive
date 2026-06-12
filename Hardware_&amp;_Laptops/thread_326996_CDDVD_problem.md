---
title: "CD/DVD problem"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by odin942zx on 2006-12-28
hi, im new to linux, and i have it installed on a second harddrive in my computer

i have 2 CD drives in my computer (a CD drive and a DVD/CD burner), but under Places-->Computer, it only shows the CD drive, and it wont even let me mount it...

the CD/DVD burner doesnt show up anywhere under linux, but both CD drives show up in BIOS and on my win2k drive...

could someone help me out?

thanks

---

### Post by tommcd on 2006-12-28
What happens when you put a disk (like a music CD) in each drive? Does it show up on your desktop? 
From terminal (applications>accesories>terminal) do:
"cat /etc/fstab" (without quotes) and you should have an easy to spot entry for each drive. If not you may have to manually add it. On my system my DVD burner is listed like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Post your fstab.

---

### Post by odin942zx on 2006-12-28
when i put in a music CD, nothing happens...it doesn't even spin up...

this is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=86a01b8e-ae9a-4478-8869-3a65cb69da18 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=7cb72a95-e9e6-4935-bca5-209cba8a4b19 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by tommcd on 2006-12-28
1) I assume both drives work in windows, correct?
2) Does the other cdrom (/dev/hdb /media/cdrom0 in your fstab) work in ubuntu?
3) Look in the /media directory. You should have an entry for each drive there (cdrom0 and cdrom1). If not, you can make the second one like this 'sudo mkdir /media/cdrom1'. Then try to mount it: 'mount /media/cdrom1' Only data CDs will mount like that. For music CDs just open rhythmbox or sound juicer and try to play it.
4) You will need to add an entry to your fstab for the 2nd drive. First backup your fstab like this 'sudo cp /etc/fstab /etc/fstab.bak'. Then to add the second drive do 'gksudo gedit /etc/fstab'. This opens a text editor. To add the 2nd drive (AFAIK) it should be:
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
Save and exit. Then do 'sudo mount -a' and try it.
Also, could the IDE cable be bad? Do you have the devices set as master and slave? This usually works better than 'cable select'.
Hope this helps.

---

### Post by odin942zx on 2006-12-28
thanks, man

well, now both drives are recognized, but the DVD burner is labeled CD-ROM 1, and when i click on it, an error pops up, saying "no medium found"

the other one works normally though...

---

### Post by tommcd on 2006-12-29
(Sorry I took so long to get back...)
The DVD burner labeled as cdrom1 is not a problem. My DVD burner is labeled:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
and it works fine.
So the CD drive (is it a CDRW or CDROM?) works fine, correct? This is /dev/hdb /media/cdrom0 in your fstab, correct? And you now also have a DVD burner (/dev/hdc /media/cdrom1 in your fstab) that is not working, correct? (In my last post I said you should add /dev/hdc /media/cdrom0... to fstab. It should have been /dev/hdc /media/cdrom1. Sorry for the typo). Do you have the directories /media/cdrom0 and /media/cdrom1 ? If not, create them like this 'sudo mkdir /media/cdrom1'.
If you put a music CD in the DVD burner and open sound juicer or rhythmbox can you play it? If you put a data CD in can you mount it? Try:
sudo mount /dev/hdc /media/cdrom1 (if that don't work)
sudo mount -t iso9660 /dev/hdc  /media/cdrom1
If you put a data CD in the DVD burner and do 'ls -la /media' in terminal does the DVD burner show up with file permissions? Also, do you get errors if you do 'dmesg | grep hdc'
Here is what I get for my DVD burner:

tom@ubuntu:~$ dmesg | grep hdc
[17179573.792000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[17179575.104000] hdc: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[17179575.788000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)

Lastly, open synaptic package manager (system>administration>synaptic..) and search for pmount and hal. They should both be installed. If not, right click on them and select 'mark for installation' and then click 'apply' and install them. Also, you might want to install ivman (a tool to auto mount media devices) while you are at it. 
Can you burn a data CD/DVD with the DVD burner? Install gnome baker from synaptic and try to burn a data CD. I had a similar problem in zenwalk-linux. I could not mount a data CD but I could burn CDs fine.

---

### Post by odin942zx on 2006-12-29
well i had already created the directory "/media/cdrom1", and i edited my fstab, but niether of those "mount" commands work, and none of those programs recognized my DVD burner

now that i changed fstab from "/dev/hdc /media/cdrom0" to "/dev/hdc /media/cdrom1", when i click on the icon for the DVD drive in Places-->Computer, the error message says "mount: special device /dev/hdc does not exist"

when i put any kind of CD or DVD in that drive, nothing happens- it doesn't spin up or anything, and it wasn't recognized by gnome baker...

---

### Post by tommcd on 2006-12-29
Well if /dev/hdc /media/cdrom0 was working better for you then perhaps you should use that. AFAIK though, if you have 2 optical drives they should be cdrom0 and cdrom1. I only have 1 on my system.
What about pmount and hal? Are they installed in synaptic? 
 What kind of DVD burner is it? You may have the odd device that is not supported. Do a google search for 'name_of_device linux'. 
Sorry I can't be of more help. Perhaps someone else will jump in here.

---

### Post by odin942zx on 2006-12-29
well thanks for your help

btw, under my /media, there were 3 subdirectories, rather than 2: cdrom, cdrom0, and cdrom1 (the one that i made).  would that have anything to do w/ this problem?

---

### Post by tommcd on 2006-12-30
I don't think it would cause the DVD burner to be unable to mount. Try to mount it to any of those directories. sudo mount /dev/hdc media/cdrom, then /media/cdrom0, /media/cdrom1. It probably won't work but it's worth a shot. Do you know what kind of drive it is?
btw, today I got I/O errors with 'dmesg | grep hdc'. I don't know why. Yesterday I had none. The drive still works perfectly.

---

### Post by odin942zx on 2006-12-30
well the drive that doesn't work is:  _NEC DVD_RW ND-3550A

apparently this dude also had a problem w/ the same drive: [http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg46300.html](http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg46300.html)

but i dont see anything about that particular drive not being supported...

---

### Post by odin942zx on 2006-12-30
ok, well i messed around with the IDE cables and the jumper settings, and now, both the CD drive and the DVD/CD drive are fully functional

but for some reason, my computer recognizes 3 CD drives...

i went into fstab, but it only showed 1 CD drive...wierd...

well this is my fstab so far: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=86a01b8e-ae9a-4478-8869-3a65cb69da18 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=7cb72a95-e9e6-4935-bca5-209cba8a4b19 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by tommcd on 2007-01-02
Well, I thought you had added /dev/hdc to your fstab. If you only have 1 optical drive in your fstab I don't know how you are able to mount both of them.  How do you know that your computer recognizes 3 CD drives, are there 3 listed in places>computer?
This is why I suggested to use master and slave instead of cable select for your jumper settings. It is less likely to cause problems. Glad you got it working!

---

### Post by odin942zx on 2007-01-02
well i used Master/Slave jumper settings, but it's still acting wierd...

well i'll figure it out eventually

thanks for all your help

---

### Post by tommcd on 2007-01-03
For what it's worth, forum staffer Taurus uses the same DVD burner as you, and his apparently is ok:
[http://ubuntuforums.org/showthread.php?t=269655&highlight=NEC+ND-3550A](http://ubuntuforums.org/showthread.php?t=269655&highlight=NEC+ND-3550A)
When you said "ok, well i messed around with the IDE cables and the jumper settings, and now, both the CD drive and the DVD/CD drive are fully functional", did you try a different IDE cable? If the drive is working intermittently perhaps the cable is bad. Also, is the DVD burner set up as master or slave. For my LiteOn DVD burner the manufacturer says for optimum performance it should be the master. Perhaps you could try hooking it up by itself, set to master, without the CD drive. AFAIK it should then correspond to the /dev/hdb in your fstab. If you are going to keep the 2 drives you should then put /dev/hdc back in fstab. But try the DVD burner by itself.

---

