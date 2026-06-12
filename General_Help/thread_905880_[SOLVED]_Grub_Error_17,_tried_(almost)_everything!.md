---
title: "[SOLVED] Grub Error 17, tried (almost) everything!"
date: 2008-08-30
forum: General Help
---

### Post by Stupojohn on 2008-08-30
So I was doing my C programming for class (baby stuff, I really don't know C at all) when my laptop became unresponsive.  I restarted and got Error 17 in the GRUB.  I booted from the live cd and tried...

sudo update-grub

...but I received the message "No GRUB directory found."  I opened...

sudo gedit /boot/grub/menu.lst

...and the file is completely blank!  Do I need to completely rebuild this?  I'm very confused.  Been using ubuntu for about a year now and this is the first really scary problem.  The problem is on an old Dell Smartstep laptop.  Thanks in advance!

---

### Post by Bucky Ball on 2008-08-30
Try (not from the live cd but from recovery):

```
locate menu.lst

```Is it anywhere? Sure it is. If it is looking for the menu.lst on the live cd, it would be blank. Are you sure you are looking for the menu.lst on your hard drives? Think that could be the problem as Error 17 indicates your grub is there and searching but not finding. So, leave the live cd out of the equation for now.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

This is an excellent page for all things GRUB and will give you a clear indication of what error 17 is all about. Fear not, your grub has gone nowhere. Unless you are willing to learn about how to manually configure grub, I suggest you try supergrubdisk to put things back in order for the moment as you have tweaked something.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You have probably changed something inadvertantly and will find this is not major so don't panic, bud (for now!)
Welcome to the forums and Good luck. :)

---

### Post by Stupojohn on 2008-08-30
I found menu.lst, but it only seems to be located in the examples folder.

/usr/share/doc/grub/examples/menu.lst

Doesn't sound too promising.  I tried...

sudo dumpe2fs /dev/sda2|grep -i superblock

...from the website [http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup](http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup) but that gives the error "couldn't find valid system superblock."  Any more ideas?  BTW thanks for the quick response!

---

### Post by Bucky Ball on 2008-08-30
This is on your hard drive? Not live cd boot?

You could try inserting your Ubuntu install cd and running 'Fix broken system' (it is called something like that), and head for the 'set up grub' section. That could fix. Can you actually get to the boot screen, or does it hit error 17 before that, which is normal for this?

---

### Post by Stupojohn on 2008-08-30
I'm using the live CD right now.  I'm not sure if this is on the CD or not.  I might be more confused than I sound haha!  Let me know if I need to give you some more info...

---

### Post by Stupojohn on 2008-08-30
Just saw your supergrubdisk link.  Checking that out now.

I can't find an option to fix a broken system or anything similar to that.

---

### Post by Bucky Ball on 2008-08-30
Okay, go the supergrubdisk.

Download, burn iso and boot from that (set in bios to boot from cd). That is good chance of reconfiguring. Once you're up again, you can work out what you have done in the first place. :)

Also, check the other link to find out exactly what error 17 is. Your grub is there somewhere it seems.

---

### Post by Stupojohn on 2008-08-30
Loaded SGD.  Tried the "Boot Gnu/Linux Directly" according to [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17) but now I'm getting error 15 instead!

I headed over to [http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5) and am jumping back into the Live CD to see if I can make any progress.  Thanks for sticking with me through this process!

---

### Post by Bucky Ball on 2008-08-30
A new error message! Excellent, we are getting somewhere (maybe). Think you need to use different option in SGD:

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

I would go directly to this link and work it from there; see if you get further. The live cd could confuse you more but you might find something I guess.

ps: no probs - I gotta nick out briefly but will check back shortly to see how things are going. :)

---

### Post by Stupojohn on 2008-08-30
Trying to follow that last link.  I guess the major problem is that I can't find menu.lst.  The only one that shows up when I...

locate menu.lst

...is the one in the examples folder.  Not sure why.  I'm running as root right now.  If I could boot with SGD this would probably work!

Should I be able to access my files from the live CD?  If so I could just backup and reinstall!

Thanks for being so helpful.  Don't let me keep you up all night!

---

### Post by Bucky Ball on 2008-08-31
Middle of the day here! lol

Yes, you could back up and reinstall but that would be last resort. How come can't boot from SuperGrubDisk? (you need to reboot then hit esc/f1/delete or whatever key takes you to your BIOS menu, then select to boot from cd - change first boot device to cd - then insert supergrub, hit f10 to save changes and exit and you are there ... no go while the machine is already up). :)

---

### Post by Stupojohn on 2008-08-31
Australia, gotcha hahaha.

I worded that last post poorly.  I CAN boot into the SGD menu and I can go through all of its options, it just never gets me back to my ubuntu...

---

### Post by Bucky Ball on 2008-08-31
* Check the link in my next post. Looks promising. How to setup grub from livecd in case it is wiped for some reason ...

Have you followed instructions for 'grub error 15' from the link? 'File not found'? SGB will not get you back into Ubuntu directly. It will do its fix then come up with a message at the end telling you it has fixed or failed. If it tells you 'SGB successful' (or something like that), you reboot, head to bios and take cd out, set to boot from you drive again then f10 and see what happens.

Have you tried rebooting lately? (no live cd). Is that giving the error 15? Try just a straight boot and let's get back to the start. What exact error are you getting (no live cd).

All a bit strange as I can't figure how you would have deleted your menu.lst without consciously doing so. And yes, the example menu list does exist on the hard drive in** /usr/share/doc/grub/examples/menu.lst** so probably wasn't coming from the live cd.

---

### Post by Bucky Ball on 2008-08-31
Incidentally, what is in your /boot/grub directory at the moment? You could re-write the menu.lst. To do so, you will need the UUID of the drive you have Ubuntu installed on and the correct kernel version. Again, can't figure how it has just disappeared.

*** Update: Hey, try this page. Just make sure to read the additions in case they apply to your situation:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

See where that takes you.

---

### Post by Stupojohn on 2008-08-31
I tried SGD and it said it had failed.  I tried to boot without the CD just for fun and it still gave me error 17.  I only got error 15 while trying to force it to boot with the SGD.

I followed your link and get error 15 when I run...

grub> find /boot/grub/stage1

...so I jumped down to this part....

sudo mount -t ext3 /dev/sda6 /mnt/root

...which seems like it should work, except I don't know what number I should put after sda!

---

### Post by Bucky Ball on 2008-08-31
Ah ha! Try

[B]sudo fdisk -l
[/B] 
That should show you what is on your hard drive(s) and you should be able to find the appropriate drive/partition. It will be one marked '**Linux'** only.

---

### Post by Stupojohn on 2008-08-31
Well, the one marked linux was sda1, so I entered...

sudo mount -t ext3 /dev/sda1 /mnt/root

...but I get the message "mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error."

I'll be off for a little while.  It's bedtime here haha.  Thanks for all your help!  There's got to be something I'm overlooking....

---

### Post by caljohnsmith on 2008-08-31
> **Stupojohn said:**
> I followed your link and get error 15 when I run...

grub> find /boot/grub/stage1

> **Stupojohn said:**
> 
sudo mount -t ext3 /dev/sda1 /mnt/root

...but I get the message "mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error."

Since you got an error 15 when searching for the stage1 Grub file in Grub's CLI, and also since you got an error when trying to mount your Ubuntu partition, I would recommend doing a fsck on your Ubuntu partition from the Live CD:
```
sudo fsck /dev/sda1
```
That assumes sda1 is your Ubuntu partition, which we don't know for sure. If you would post the output of:
```
sudo fdisk -lu
```
Then we can help figure out your Ubuntu partition.

---

### Post by Stupojohn on 2008-08-31
Here's what I got.  Thanks for your help!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdb43d6c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    76646114    38323026   83  Linux
/dev/sda2        76646115    78140159      747022+   5  Extended
/dev/sda5        76646178    78140159      746991   82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-08-31
OK, from the Live CD, first make sure your Ubuntu partition's file system is OK:
```
sudo fsck /dev/sda1
```
Let me know if it finds any errors, but keep going and post the output of all the following:
```
sudo mount /dev/sda1 /mnt
cat /mnt/boot/grub/menu.lst
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo grub
grub> find /boot/grub/stage1
```

---

### Post by Stupojohn on 2008-08-31
I ran sudo fsck /dev/sda1 and got...
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 107081, i_blocks is 128, should be 0.  Fix<y>?

```

Here's the rest.  This first command didn't give any output.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc7cb662-5396-420b-885b-73b22f23d0a3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bc7cb662-5396-420b-885b-73b22f23d0a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=bc7cb662-5396-420b-885b-73b22f23d0a3 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bc7cb662-5396-420b-885b-73b22f23d0a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bc7cb662-5396-420b-885b-73b22f23d0a3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.256136 s, 0.0 kB/s
0000000 ff00                                   
0000002
ubuntu@ubuntu:~$ 
```

```
grub> find /boot/grub/stage1
 (hd0,0)
```

---

### Post by caljohnsmith on 2008-08-31
> **Stupojohn said:**
> I ran sudo fsck /dev/sda1 and got...
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
[COLOR="Red"]Inode 107081, i_blocks is 128, should be 0.  Fix<y>?[/COLOR]

```

So did you hit return and let fsck complete fixing things? If not, please do it again and say yes to all prompts when it asks if you want to fix it. :)

Next, in the terminal, do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of everything above. After you've done everything, reboot and let me know any Grub errors you may get on startup.

---

### Post by Stupojohn on 2008-08-31
> **caljohnsmith said:**
> So did you hit return and let fsck complete fixing things? 
I got scared and hit ctrl+C!  Trying these things now...

---

### Post by Stupojohn on 2008-08-31
There were alot of y/n questions before this point...
```

Directories count wrong for group #291 (0, counted=174).
Fix<y>? yes

Free inodes count wrong (2400504, counted=2268200).
Fix<y>? yes

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 132056/2400256 files (0.8% non-contiguous), 676508/9580756 blocks
ubuntu@ubuntu:~$
```
```
 

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

It's fixed!!!  No errors!!!
Thanks to both you guys for helping me so much!  Hopefully this thread will help other people, too.

Could you explain really briefly how you fixed it?

---

### Post by caljohnsmith on 2008-09-01
I'm so glad your computer is happy and healthy again. :)

I think the bottom line is when your computer originally became unresponsive and you had to do a hard reset, that left Ubuntu's file system in a bad state. So I think that doing the "fsck" is what solved your problem; but I also had you reinstall Grub to the master boot record (MBR) with those Grub commands just to make sure that Grub hadn't some how been corrupted too. It doesn't hurt, and it removes one less variable of what might be causing your problem.

---

### Post by Bucky Ball on 2008-09-01
Fantastic news! Love it when a plan comes together and nice work Caljohnsmith. Have fun Stupojohn and remember to post if you come up against any other brick walls. Don't forget to mark your thread 'Solved' (you'll find it under 'Thread Tools' so others will check it for a fix). :)

---

