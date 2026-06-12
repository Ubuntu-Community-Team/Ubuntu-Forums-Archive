---
title: "[SOLVED] Grub Error 2 while trying to boot into Gentoo"
date: 2008-10-11
forum: Gentoo and derivatives
---

### Post by Morrad on 2008-10-11
Hey everyone.  I wanted to try out Gentoo to see what all the fuss was about, so I've installed it on a separate partition, and edited my menu.lst file within my Ubuntu partition.  The goal is to use configfile to launch Gentoo's grub.conf file, and launch it from there.

Here is how the relavent partitions are set up:

```
/dev/sda2   ubuntu (flagged bootable)
/dev/sda4   gentoo (tried boot flagged/unflagged)
```

Within grub, booting gentoo:
```
title Gentoo Linux
configfile (hd0,3)/boot/grub/grub.conf
```

With this, I'm getting "Grub Error 2: Bad file or directory type" when selecting that option.  I've also tried using the interactive mode in grub, and it gives the same error for trying to autocomplete "configfile (hd0,3)/".

Anyone have any idea what could be causing this?  I haven't seen anything on the web or any forums.

---

### Post by trimeta on 2008-10-11
I've never used "configfile" in Grub, so no idea here.

---

### Post by Patb on 2008-10-11
Morrad, could you please boot into your ubuntu system, open a terminal and post the output of the following commands:
```
sudo fdisk -l
sudo blkid
tail -n 40 /boot/grub/menu.lst
cat /boot/grub/configfile
```
That should provide information which will enable someone to help you. You may possibly have to get into your Gentoo partition for further information but we'll come to that. 

By the way, a very useful Australian wrote a very useful [Guide to Grub]("http://users.bigpond.net.au/hermanzone/p15.htm"). 

Cheers, Pat.

---

### Post by Morrad on 2008-10-11
Sure thing, Patb.

```
sudo fdisk -l

320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70447044

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13731   110294226    7  HPFS/NTFS
/dev/sda2   *       13732       20670    55737517+  83  Linux
/dev/sda3           26796       38913    97337835    5  Extended
/dev/sda4           20671       26795    49199062+  83  Linux
/dev/sda5           28445       38913    84092211   83  Linux
/dev/sda6           26796       27188     3156709+  82  Linux swap / Solaris
/dev/sda7           27189       28444    10088788+  83  Linux

Partition table entries are not in disk order
```

```
sudo blkid

/dev/sda1: UUID="01C74CF9D583C9A0" LABEL="DSK1_VOL1" TYPE="ntfs" 
/dev/sda5: LABEL="/home" UUID="0465644f-0560-4141-bb30-d4f46687c4be" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="a7f98cb8-6953-49a2-b8fc-8047f05ad2de" TYPE="ext3" LABEL="ubuntu" 
/dev/sda4: LABEL="gentoo" UUID="5edb7d82-75ef-428c-82af-16907d68982d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" LABEL="swap" UUID="fad1c708-6b5a-4a6c-a857-1377a0444a8c" 
/dev/sda7: LABEL="/tmp" UUID="59defd57-f7e5-4a54-8dbd-f834d293692c" SEC_TYPE="ext2" TYPE="ext3" 
```

```
sudo tail -n 51 /boot/grub/menu.lst

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
makeactive

title Gentoo 2008.0
title=Gentoo Linux
configfile (hd0,3)/boot/grub/grub.conf

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin

title Other operating systems:

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7f98cb8-6953-49a2-b8fc-8047f05ad2de ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
```

```
cat /boot/grub/configfile

cat: /boot/grub/configfile: No such file or directory
```

EDIT:
Actually, now that I think about it, I don't have any grub command files in my /boot/grub/ directory.  I know I haven't deleted anything in there, so I'm going to venture a guess that that isn't my issue then.

---

### Post by Patb on 2008-10-11
Thanks Morrad. Grub is looking for a configuration file at (hd0,3)/boot/grub/grub.conf (sorry, I didn't read your first post closely enough to work that out). This file might not exist, which would perhaps account for the grub error you are getting. To check, look in the directory where /dev/sda4 (not sda3) is mounted. If it is not mounted or you have trouble finding it try:
```
sudo mkdir /media/sda4/
sudo mount /dev/sda4 /media/sda4
cat /media/sda4/boot/grub/grub.conf
```
This will show you whether grub.conf exists where Grub is looking for it. 

Also, I've never used Gentoo but you can probably back up and edit your menu.lst file to follow the same pattern as for your Ubuntu option. 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bk1
sudo gedit /boot/grub/menu.lst
```
Edit the Gentoo entry to look something like the code below. Check the exact name of the kernel files in the directory /media/sda4/boot/ and replace the x's accordingly. (Note that I have already used the corrrect UUID). 
```
title Gentoo
kernel /boot/vmlinuz-xxxxxxxx root=UUID=5edb7d82-75ef-428c-82af-16907d68982d ro
initrd /boot/initrd.img-xxxxxxxx
savedefault
makeactive
```
In this setup, grub will ignore any /boot/grub/grub.conf file that might exist in the Gentoo partition, which might have its own problems. But at least then you can perhaps work out from the config file what Grub is trying to do; or post the contents if you can't work it out. Let us know how you go. 

Hope this helps. Cheers, Pat.

---

### Post by Morrad on 2008-10-11
Thank you, Patb, for coming back to check on me.  I believe you are mistaken about the source of my difficulty, however.

My understanding is that that (hdx,y) refers to hard drive x+1, partition y+1, so (hd0,3) really is looking at /dev/sda4 as it should.  The grub guide you shared (which is quite nice, by the way, thanks) explains this [here]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").

Previously, in my own problem solving, I have mounted the gentoo partition, and I can verify that /boot/grub/grub.conf does indeed exist and is the correct file to point to, akin to Ubuntu's menu.lst file.

I've also tried the alternative approach you mentioned, having ubuntu's grub look directly for the gentoo kernel as you've described, by I will give that a try again.  I don't think I tried the "savedefault" and "makeactive" commands previously.  I'll update in a little bit with my results.

---

### Post by trimeta on 2008-10-11
I've done a multiboot setup on my system for some time, using my Gentoo partition's grub.conf to load my Ubuntu (or Debian, now) kernel and root. Here are the relevant parts of my grub.conf:

```
# For booting Gentoo with suspend
title  Gentoo Linux 2.6.25-protect-r7 (fb+ suspend+)
root (hd0,0)
kernel /kernel-2.6.25-protect-r7.1 root=/dev/sda5 video=uvesafb:1280x800-32,mtrr:3,ywrap acpi_sleep=s3_bios fbcon=scrollback:128K splash=fadein,silent,theme:natural_gentoo CONSOLE=/dev/tty1 resume=/dev/mapper/crypt-swap-hd
initrd /boot/fbsplash-natural_gentoo-1280x800

#<snipping out some different Gentoo options>

# For booting Debian
title  Debian GNU/Linux Sid
root (hd0,7)
kernel /vmlinuz root=/dev/sda8
initrd /initrd.img
```

If the above didn't make sense, I've got my Gentoo /boot on sda1, Gentoo / (root) on sda5, and my whole Debian system (/boot and all) on sda8. Doing something like that, to have your Ubuntu menu.lst boot Gentoo directly (rather than call Gentoo's grub.conf), may be easier.

---

### Post by caljohnsmith on 2008-10-11
How about rebooting, and when you get the grub menu, press "c" for the command line, and then type:
```
grub> cat (hd0,3)/
```
Then press TAB for tab-completion, and it should list your Gentoo root directory. If that works, proceed to the boot directory:
```
grub> cat (hd0,3)/boot/
```
Again press TAB. If that works do the grub directory:
```
grub> cat (hd0,3)/boot/grub/
```
TAB, and if it shows your grub.conf, do:
```
grub> cat (hd0,3)/boot/grub/grub.conf
```
and hit enter this time. Does it show your grub.conf?

---

### Post by Morrad on 2008-10-11
Hmm.  No good trying to boot gentoo directly.  Here's what I was trying.

I appologize, I'm on my laptop staring at my grub screen, so I don't want to type in the actual numbers.
```
title Gentoo
root(hd0,3)
kernel /boot/kernel-genkernel-####### root=UUID=(hex ID for /dev/sda4) ro
initrd /boot/initramfs-genkernel-#######
makeactive
```

Interesting find while messing with grub's command line though.  I decided to see if grub could even see the linux kernel in 

```
find /vmliuz

(hd0,1)
```

So it only sees a linux kernel in my ubuntu partition then.

---

### Post by Morrad on 2008-10-11
> **caljohnsmith said:**
> How about rebooting, and when you get the grub menu, press "c" for the command line, and then type:
```
grub> cat (hd0,3)/
```
Then press TAB for tab-completion, and it should list your Gentoo root directory. If that works, proceed to the boot directory:

I get an error:
```
Error 2: Bad file or directory type.
```


EDIT:
I've gotten this error whenever trying to do any autocompletes for files not in my Ubuntu '/' partition in /dev/sda2, by the way.

---

### Post by caljohnsmith on 2008-10-11
So are you saying you can't do tab-completion for any linux partitions other than Ubuntu in sda2? Or is it only sda4 that is the problem? Can you mount sda4 OK?
```
sudo mount /dev/sda4 /mnt
cat /mnt/boot/grub/grub.conf
```
Does that show your grub.conf, and does it have all your Gentoo entries?

---

### Post by trimeta on 2008-10-11
Hmm. Did you try that same config without the makeactive? I don't think you need it, if booting one Linux distro from another. Also, it's no surprise you didn't find a /vmlinuz in your Gentoo partition; while on Ubuntu/Debian, /vmlinuz is a symlink to your current kernel, Gentoo doesn't do this by default. You could create such a symlink if you want, but it won't work until you do so manually.

Also, I'm not sure if you want to have "ro" in your kernal options for Gentoo; I'm likewise not sure if you need a space between "root" and "(hd0,3)". These may be unrelated to your problems, but it might be worth changing them briefly, to see what happens.

---

### Post by Morrad on 2008-10-11
> **caljohnsmith said:**
> So are you saying you can't do tab-completion for any linux partitions other than Ubuntu in sda2? Or is it only sda4 that is the problem? Can you mount sda4 OK?
```
sudo mount /dev/sda4 /mnt
cat /mnt/boot/grub/grub.conf
```
Does that show your grub.conf, and does it have all your Gentoo entries?

Once I'm in Ubuntu, I can mount /dev/sda4 no problem: all my gentoo files and entries are there.  I've opened and looked at grub.conf in gentoo several times.  And yes, I can't do tab-completion on any drives other than /dev/sda2 in the grub command prompt.

---

### Post by caljohnsmith on 2008-10-11
How about running an fsck on sda4 and see if that makes any difference:
```
sudo umount /dev/sda4
sudo fsck /dev/sda4
```
(Need to make sure sda4 is not mounted). Can Grub see it after that?

---

### Post by Morrad on 2008-10-11
> **caljohnsmith said:**
> How about running an fsck on sda4 and see if that makes any difference:
```
sudo umount /dev/sda4
sudo fsck /dev/sda4
```
(Need to make sure sda4 is not mounted). Can Grub see it after that?
fsck worked and was successful.  After rebooting, I tried to autocomplete:
```
find (hd0,3)/b
```
And I got bin and boot as possible options!!.

And on the second try, it doesn't work anymore.

---

### Post by caljohnsmith on 2008-10-11
How old is your HDD? I'm wondering if it is starting to flake out. Do you have a Diagnostics CD that came with your HDD? It would be good to check it I think. If you don't have a HDD diagnostics CD, you can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com") instead, because it has a whole bunch of programs for checking HDD integrity. 

Also, I would recommend doing a quick check of your HDD's partition table to make sure that's not an issue:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by Morrad on 2008-10-11
> **trimeta said:**
> Hmm. Did you try that same config without the makeactive?

Also, I'm not sure if you want to have "ro" in your kernal options for Gentoo; I'm likewise not sure if you need a space between "root" and "(hd0,3)". These may be unrelated to your problems, but it might be worth changing them briefly, to see what happens.

I did try in the past to not use makeactive, I added it after it was suggested in a previous post.  Doesn't seem to make any difference.

Trying without "ro" doesn't seem to do anything either.

Removing the space in "root (hd0,3)" causes the computer to restart.  I wasn't expecting much though, since my working ubuntu entry has a space there.

---

### Post by Morrad on 2008-10-11
> **caljohnsmith said:**
> 
Also, I would recommend doing a quick check of your HDD's partition table to make sure that's not an issue:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

Doesn't look like there are any errors to me . . . partition table is as I expected.
```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0   1  1 13730 254 63  220588452 [DSK1_VOL1]
 2 * Linux                13731   0  1 20669 254 63  111475035 [ubuntu]
 3 E extended             26795   0  1 38912 254 63  194675670
 4 P Linux                20670   0  1 26794 254 63   98398125 [gentoo]
 5 L Linux                28444   1  1 38912 254 63  168184422 [/home]
   X extended             26795   0  2 27187 254 63    6313544
 6 L Linux Swap           26795   2  1 27187 254 63    6313419
   X extended             27188   0  1 28443 254 63   20177640
 7 L Linux                27188   1  1 28443 254 63   20177577 [/tmp]





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
```

> How old is your HDD? I'm wondering if it is starting to flake out. Do you have a Diagnostics CD that came with your HDD? It would be good to check it I think. If you don't have a HDD diagnostics CD, you can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com") instead, because it has a whole bunch of programs for checking HDD integrity

I'm not sure how old the HDD is.  I don't have the diagnostic CD that came with the hard drive, but I do have [SystemRescueCD](http://www.sysresccd.org/Main_Page) which comes with [MHDD](http://hddguru.com/content/en/software/2005.10.02-MHDD/) on it.  I'll give that a whirl and see what it pops up next.

---

### Post by meierfra. on 2008-10-11
Did you upgrade to Hardy from an earlier version of Ubuntu? Then you might of have  older version of grub which cannot read ext3 partition with 256 inodes.  Try this

```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda

```

---

### Post by Morrad on 2008-10-11
> **meierfra. said:**
> Did you upgrade to Hardy from an earlier version of Ubuntu? Then you might of have  older version of grub which cannot read ext3 partition with 256 inodes.  Try this

```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda

```

I did upgrade from an earlier distro.

Before I try this, I have to ask: will this mess up my Windows MBR?  I do have windows installed on the first partition of my machine.

---

### Post by meierfra. on 2008-10-11
Yes that will install Grub to the MBR.  But isn't grub already installed in the MBR?  Or did you add Ubuntu to the Windows Boot loader ?

---

### Post by Morrad on 2008-10-11
I suppose it is.  When I turn on my computer, grub comes up, not some windows program.  Is there a way that I can check and be sure that is the case?

---

### Post by meierfra. on 2008-10-12
Copy and paste this into a terminal:

```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub

```

If it returns "Grub" you have grub installed in the MBR.

---

### Post by Morrad on 2008-10-12
I do have grub in the MBR then, thanks.

As I'm trying to install the new version of grub, I get the following error though.  (I already purged and apt-get installed the existing grub install, by the way).

```
sudo grub-install /dev/sda

/dev/sda does not have any corresponding BIOS drive.
```

---

### Post by meierfra. on 2008-10-12
Try

> sudo grub-install --recheck /dev/sda

---

### Post by Morrad on 2008-10-12
I take it back, I added a --recheck switch to the above command, and it installed.  Needed to renew the device map after I purged the old one.

I'll go test it out now.

---

### Post by Morrad on 2008-10-12
I'm happy to announce that the problem did appear to be with the grub version I was using, not my hard disk.  After reinstalling, grub is able to see all my linux partitions without any issues, and I can boot into Gentoo.

Thank you all for the suggestions and help.  Marking thread as solved.

---

### Post by meierfra. on 2008-10-12
> Thank you all for the suggestions and help

You are welcome. Have fun with gentoo.

---

