---
title: "[SOLVED] Intrepid Desktop Install Problems, reboot = flashing cursor"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by BassKozz on 2008-12-02
I just installed Intrepid (8.10) Desktop 32-bit on an older machine I have.
The machine spec's:
**MoBo:** [Intel D865GBF Desktop Board]("http://www.intel.com/support/motherboards/desktop/D865GBF/")
**CPU:** P4 3.0Ghz
**RAM:** 4x1GB G.Skill Sticks
**IDE1:** Seagate 250GB (ST380013A)
**IDE2:** Maxtor 250GB (Diamond Max Plus9)
**SATA1:** Western Digital 320GB (WD3200JD-22KLB0)
**SATA2:** Seagate 200GB (ST300822AS) - ******UBUNTU INSTALLED ON THIS ONE******

My plan is to run IDE1+IDE2+SATA1 in a RAID 5 config using mdadm, and I installed Intrepid on the SATA2 HD.  Before the install I checked the iso file's md5 hash ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) and it checked out.  I also checked the CD via it's "Check CD for defects" function, and it checked out OK without any errors.

I installed using the "Guided - use entire disk" install on the complete the install on my SATA2 drive.

Now after the install I reboot and all I get is a blank screen with a blinking cursor and nothing else](*,)
What's going on?
TiA,
-BassKozz

p.s. I setup my BIOS to boot from SATA2, so that's not the issue

---

### Post by BassKozz on 2008-12-02
**_Update_**:
I just downloaded the latest version of [SeaTools]("http://www.seagate.com/www/en-us/support/downloads/seatools/") (Seagate Diagnostic BootCD) to check the hard drive for errors, and it passed a Long (2hr) test sucessfully.
So I can rule out the HardDrive for being the culprit...

Can someone point me in the right direction here, I've never had this sort of problem with any Ubuntu Desktop Installs in the past.[-o<

---

### Post by the lush on 2008-12-03
Could be a problem with your graphics card/chip. 8.10 is VERY fussy about what it will work with, but you haven't listed it.

---

### Post by BassKozz on 2008-12-03
> **the lush said:**
> Could be a problem with your graphics card/chip. 8.10 is VERY fussy about what it will work with, but you haven't listed it.

Thanks for the suggestion **the lush**,

My Mobo has integrated Intel 865G chipset (Intel® Extreme Graphics 2), but I was using a **MX4000** AGP card... Since you mentioned it I had a extra **FX5200** AGP card laying around so I went ahead and replaced the MX4000 and booted up. This time the cursor started blinking and then dropped down two lines, as if someone pressed RETURN twice.

I then reinstalled Ubuntu thinking that the w/ the new card the install would make some changes... I rebooted, and the same thing, blinking cursor, 2xreturn, blinking cursor. #-o

What I don't understand is the install (LIVE BootCD) gUI works fine, but after install I can't get anything :-(

---

### Post by BassKozz on 2008-12-03
**Update**:
Apparently the FX5200 is not supported in the latest linux Kernel, but a patch does exist: 
[http://ubuntuforums.org/showthread.php?t=957629](http://ubuntuforums.org/showthread.php?t=957629) 
& 
[http://www.nvnews.net/vbulletin/showthread.php?t=121295](http://www.nvnews.net/vbulletin/showthread.php?t=121295)

My question now is, how do I install this patch if I can't even boot up?
Can I use the BootCD to boot and then install the patch on the already installed Ubuntu?
Or is this not even my problem?

---

### Post by BassKozz on 2008-12-03
**Another update**:
I gave up waiting for a solution for Intrepid and I downloaded Hardy (8.04) [besides I am going to use this box as a NAS server anyways, so I could prolly use the LTS] checked MD5 sum and the CD, and then installed it...
Wouldn't you know it **_[SIZE="4"]EXACT SAME PROBLEM !!! [/SIZE]_**](*,)
Something tells me this isn't a video card issue...

Any idea's anyone? [-o<

---

### Post by BassKozz on 2008-12-03
{Delete - DOUBLE POST}

---

### Post by gspat on 2008-12-03
I am having the exact same issue...

Live CD boots fine and the install goes well (it seems)... then... nothing!

Also will not boot when using the "Boot from first hard drive" option on the live cd either.

Tried the grub re-install from this post, [http://www.ubuntuforums.org/showthread?t=224351](http://www.ubuntuforums.org/showthread?t=224351) but no joy...

Using:

ASUS P4B motherboard w/P4 1.4GHz - 384 MB Ram
IDE1 - master - 500GB (seagate) <-- this is the boot drive
IDE1 - slave - 300GB (WD)
IDE2 - master - DVDROM
IDE2 - slave - 250GB (WD)
SATA1 - 500GB (WD)
SATA2 - 500GB (WD)

Tried both hardy and intrepid live CD's with same results!

IDE1 master is brand new, replaced 160GB seagate that died

when booting to live CD, the ide 500GB shows up mounted as sdc, even though it is first... why would this be? 

Also, while doing the grub re-install, the list command shows grub at hd2,0... shouldn't it be at hd0,0?

---

### Post by gspat on 2008-12-03
Should also mention that my graphics card is a nvidia 7600gs

Also should mention that my partitions on the boot drive are as follows:

sdc1 set to "\" - 20GB (ext3)
sdc2 (extended partition)
sdc3 set to swap - 6GB
sdc4 set to "\home" - 20GB (ext3)
sdc5 empty (ext3)

Is this a correct configuration?

The primary use of this machine will be to serve files to other machines on my home network using SMB.

---

### Post by BassKozz on 2008-12-03
gspat,
I know this doesn't help, but I wanted to say: "I am glad I am not the only one"

I was beginning to worry.  I spent the last few hours swapping out SATA cables, Power Cables, etc...  I've been racking my brain on this one.
I've never had trouble with Ubuntu installs like this in the past, usually it's as easy as 1-2-3.  I don't understand why I am having this hangup now...
Hopefully we can get some feedback from the community here soon to point us in the right direction.

---

### Post by BassKozz on 2008-12-03
**_UPDATE_**:

For Sh*ts & Giggles I tried installing Hardy to my Primary IDE HD (IDE1 from original post), and wouldn't you know it, **[SIZE="4"]IT WORKED[/SIZE]** !!!\\:D/

But this makes it kinda hard to run a RAID5 array using IDE1,IDE2,SATA1 since I am using IDE1 for the OS... So I need to figure out what is wrong with booting from my SATA drive.  My assumption is that there are some sort of drivers I need to install in order for Ubuntu to boot from my SATA drives...

Could this be the case, does Ubuntu need drivers to see my SATA controller on my [Intel Desktop Board D865GBF]("http://www.intel.com/support/motherboards/desktop/D865GBF/")?
The chipset of the board is **865G [Intel 82801EB I/O Controller Hub (ICH5) with AHA bus]**, is there a driver for the SATA controller I need or something?

gspat, you may want to try and install Ubuntu on one of your IDE drives to see if it works for you too.

**_Edit_**: Seems Similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/26940](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/26940)
But that bug has been fixed since 2005

---

### Post by gspat on 2008-12-04
Glad you are able to boot!

Actually, I am trying to boot off my primary IDE drive, I believe my partitions come up as sdcx because of the live CD. ( I could be totally wrong on this though).

Basically, I just replaced the dead 160GB drive with a new 500GB one. (Same number of partitions, etc.)

---

### Post by BassKozz on 2008-12-04
Everything is working now thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1001779](http://ubuntuforums.org/showthread.php?t=1001779)

_Synopsis:_
I had to remove all of the drives except the one I was going to install on (SATA2), then perform an install, then reconnect the other 3 drives and it works !!! :D

---

### Post by gspat on 2008-12-06
OK, here's an update...

did what you did... disconnected all but boot drive, installed again and it worked! reconnected the other drives and no joy!

It seems that when the 160GB drive failed, it did something to the 300GB drive as well... I can boot to the live CD and use the 300GB, but not from the boot drive! So, I copied everything off of it and put it on the dead drive pile with the 160GB drive, guess it's off to the store for another drive to fill it's spot... oh well, wanted more space anyways!

no idea why the 300GB drive acted up though... never heard of that happening before!

---

### Post by BassKozz on 2008-12-06
gspat,

Did the new HD fix your problems?

---

