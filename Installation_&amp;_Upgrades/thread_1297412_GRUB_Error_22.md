---
title: "GRUB Error 22"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by chris.reid on 2009-10-21
Here is what I have done and some of the issues I am up against.
Ubuntu 9.04 Jaunty Jackalope

First of all I am using a shuttle xpc and cannot boot from a live cd because of the bios.
So I have a working USB Live bootable that seems to be working (but i cannot have any hdd's plugged in when it boots) 
I have an external firewire that I use to access my main hdd when using the USB Live.

ok, now on to the problem.

previously when I installed ubuntu while installing it did not install to my 100gb partition I had created for it, instead it used a 10GB partition that I was going to use as a swap. 
I got ubuntu working great as I am a noob and really trying to get familiar with it. 
I installed apache, mysql, php, connected python cgi and also had it working perfectly with dynDNS. Basically this is why I wanted to try linux was to host my own server for Subversion and apache cgi access. Well like I said I had it all working, but was starting to run out of space on the 10GB partition. 
So since I wanted to go through the process of backup disk imaging I read some articles and thought this is a good time to try it out. So that I don't have to reinstall and set it all up again (which wouldn't be that bad).


I used dd to create 2 images (out of curiosity) 
```

#BACKUP:
dd if=/dev/sdb8 | gzip > /mnt/BKUP/UBUNTU.bin.2009.10.21.bin.gz
dd if=/dev/sdb8 > /mnt/BKUP/UbuntuImage.2009.10.21.dd

```Then changed the partitions by using gparted on my USB live that works.
Remember my main hdd is connected as firewire (don't know if this matters)
I made the boot partition 

[LIST]
[*]100GB **Ext3** (set its flag to boot) now **/dev/sdb1** ** used below
[/LIST]
Also created some other partitions for data storage and swap.

[LIST]
[*]10GB **swap**
[*]100GB **Ext3 **(storage)
[*]250GB **Fat32** (storage)
[/LIST]

```

#RESTORE: (notice that I repartioned everything and sdb1 was the new boot partition)
dd if=/mnt/BKUP/UbuntuImage.2009.10.21.dd  of=**/dev/sdb1**

```Then restarted with the hdd attached internally and the USB Live disconneced.
I get this:

```

GRUB Loading stage1.5

GRUB Loading, please wait...
Error 22

```From what I can read, it is an MBR problem. Is there a way to fix this.
Guess I could install ubuntu onto the Drive (is Ext3 OK?). And push the image over top of the install. Would this preserve the MBR?. Or I could tar all the files and overwrite the fresh installs? OR is there a simple way to get the MBR fixed. I don't have another USB drive and would like to keep this one, as I need to install ubuntu on a few more machines. 

Thanks 

Chris

---

### Post by chris.reid on 2009-10-21
The final comments in this thread look like they could do it.
[http://www.astahost.com/info.php/restoring-grub-boot-loader_t14048.html](http://www.astahost.com/info.php/restoring-grub-boot-loader_t14048.html)

And this is what gave me the idea of what was happening
[http://ubuntuforums.org/showthread.php?t=993211](http://ubuntuforums.org/showthread.php?t=993211)

[COLOR=Red]## Legend[/COLOR]
**[COLOR=Red]X[/COLOR]** = s or h or whatever once hdd is installed internally for these examples it was external firewire drive

I am guessing my problem is that previously my boot was **/dev/[COLOR=Red]X[/COLOR]da_8_**

so that is what the MBR is trying to do.

I need to change it to **/dev/[COLOR=Red]X[/COLOR]da_1_** (the current boot partition).

Can I do this in a file? Or should I mount /dev/sda1 from within the USB Live. And grub-install to mountpoint?

Let me know if this sounds like a plan. I am not doing anything since this is only my first week of playing with linux. And I have learned not to move ahead too quickly

---

### Post by chris.reid on 2009-10-21
Tried the grub-install /dev/sdb1 with no success. 
Any ideas out there.....

---

### Post by oldfred on 2009-10-22
I have seen two previous threads in the last couple of weeks where someone used dd to copy from a small drive to a new larger drive and could not then see the larger drive. The copy converted the new drive to the old small drive's size. And it is very difficult to fix the drive size.

The dd is for copying from a drive or partition of the same size. I am not sure what it did in your case. the copy is an exact copy, so you may have two partitions with the same uuid which of course cannot be.  

Can you from your usb boot run blkid to see the uuid.

---

### Post by sahabcse on 2009-10-22
please follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by chris.reid on 2009-10-22
@oldfred
Actually the docs and everything I have read say it is fine to put a dd image onto a larger drive, but there are some work arounds to put it on a smaller drive.
As for running blkid, I am afraid not. I went ahead and reinstalled the entire drive.

However the bios bug with the shuttle that I have seen all over the net, was actually a badly written CD. Now I can boot and use the LiveCD, but it is too late. I already have everything up and working.

@sahabcse
I tried this and I also tried some other more sophisticated ones that take into account that the drive is external. None of them worked. In the near future I will pull out an old drive and try to make this all happen again so I can learn from it.

Thanks guys, but I moved on and just reinstalled. Much easier this time and I wrote a nice log so if I have to do it again after I forget everything I have done.

---

### Post by mechro on 2009-10-22
```
mechro@mechro-desktop:~$ blkid -help
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghlLv] [-o format] [-s <tag>] [-t <token>]
    [-w <file>] [dev ...]
        -a      be afraid, be very afraid
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)
```

:shock:

---

