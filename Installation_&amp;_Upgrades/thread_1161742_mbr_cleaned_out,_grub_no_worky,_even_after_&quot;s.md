---
title: "mbr cleaned out, grub no worky, even after &quot;successful&quot; reinstall"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by tiehn on 2009-05-17
Okay so long story short is the title of this thread.  Below is a post I made from another forum that has more details:

> So my compootar stuff: Windows XP all updated on a 40 gig hard drive C. 'attached' to it is a 200 gig HD, both of which are on one IDE ribbon cable as master/slave.
I also have Ubuntu, now 9.04 on a separate 250GB hard drive on a SATA cable using what I believe is the latest kernel.

Up until yesterday everything was fine, when I had a bright idea of going from ubuntu 8.04 to 9.04 because it sounded shiny and I was bored. So first ubuntu decides to update to 8.10, it throws a fit while updating because I had a newer version of pygame installed and so my ubuntu crapped out. No big deal, I boot into windows, grab a 9.04 liveCD, do a clean format and wipe that second hard drive and put 9.04 on it.

No problems so far.

So today I decide I should boot into windows to make sure it's all fine, and it gives me a fancy "cannot find NTLDR please restart" message. After running through 6 different "possible solutions" the one that fixes it is going into recovery mode with my XP disc and doing: bootcfg /rebuild ; fixboot ; fixmbr.

So I run those they go without a hitch and no problems, except one: I no longer have GRUB and this machine starts into XP automatically. Blegh, fixed one to screw up another.
So I do some searching and find that with the LiveCD I can reinstall grub by doing these commands in a terminal:

sudo grub
find /boot/grub/stage1
>returns (hd0,0)
root (hd0,0)
setup (hd0)
quit
reboot


all that runs fine, says it was successful. Except, my computer still wont load GRUB. Ok, so apparently I can reinstall grub from windows (sort of) using this "Auto Super Grub Disc" program. So I install that, reboot and boot with "unetbootin", and after some ascii flashes by, I am greeted with a giant ASCII sadface saying that it couldnt fix GRUB.


So I try going back to the livecd, and running grub again but instead I ran setup (hd0,0) instead to see if anything would change, and it complained about something that wasnt fatal but was otherwise successful. Except still I am greeted by no grub. Likewise, after running grub -> find /boot blah blah blah, ubuntu's docs say to edit /boot/grub/menu.lst to make sure windows is there--except even after running grub's setup command, it still does not even have a boot/grub directory, let alone a menu.lst.

Halp?

And if its worth anything, when I run fdisk -l in the terminal, it gives me my linux HDD as /dev/sdaX, windows drive as /dev/sdb1, and my other drive as /dev/sdc1. But from what I hear, sdX's are reserved for sata cables, of which only my Linux drive uses SATA, and my windows drive should be labelled hda. o_O


Slightly more additional information:

I also read that I have to "run "grub" not from the Ubuntu Desktop/Live CD, but from your disk installation to make it work. To do this mount your root partition" and so on from that site and run these commands first:

sudo mkdir /mnt/linux
sudo mount /dev/hda1 /mnt/linux
cd /mnt/linux/sbin
sudo ./grub


Well, first it tells me hda1 doesnt exist--probably because all my drives are sda/sdb/ instead. Since Ubuntu's boot folder is on my sda1 (according to fdisk), I mount sda1, I go into linux/sbin, and then it tells me it cannot find ./grub.

 Heres what I type into the terminal to install grub from a LiveCD:

Alt F2 -> gnome-terminal
```

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```But it does absolutely nothing, as even after running that, trying to "cd /boot/grub" from the livecd terminal makes it just complain that it cant find the directory.  I'm tired and not thinking straight now, so I'll check this thread tomorrow morning to see if there's any responses, if you guys need any more info I'll gladly share more.

Also, here's what fdisk -l spits out:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f206

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09110911

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a7a2c93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS

```

I believe "sdb1" is my windows hard drive, which happens to be attached to an IDE ribbon cable.  I'm not sure if that's worth noting or not though.

---

