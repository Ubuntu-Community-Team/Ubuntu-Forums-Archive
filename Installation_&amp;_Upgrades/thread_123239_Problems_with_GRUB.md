---
title: "Problems with GRUB"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by DaneelS on 2006-01-29
So I thought I'd give Linux a try and once again I stumble at the first hurdle.  The objective is dual boot with XP.

I have 4 HDs, 1 on mobo IDE, 2 on mobo SATA (one has windows install the other has the ubuntu install) and 1 on mobo RAID SATA (configured as just another drive, there is no array setup).

I cleared some space on one of the SATA drives attached to my mobo and proceeded to install.  I put on GRUB when it asked.

Following the reboot, my machine went straight into windows.

I rebooted and selected the correct HD to boot from, this time GRUB sat there for a whie then came up with error 17 and nothing else.

I restarted again and switched the boot HD in the BIOS to the one with ubuntu on it, it didnt go anywhere, just said HD not bootable.

I've just finished downloading the nbuntu live CD, burning as I type, not sure what I'm going to do with it though.

Help appreciated, I'd really like to get linux to work this time.

File contents:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



Device.map
> (hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc

There is no grub.cfg file as far as I can see.

---

### Post by DaneelS on 2006-01-29
To make HD setup clearer.  I wonder, is it because the partition with ubuntu on it isn't first on the HD that it won't boot?

[www.megapleb.com/partitions.png](www.megapleb.com/partitions.png)

---

### Post by dickohead on 2006-01-29
You need one of two things:

The boot loader on the MBR of your first Hard Drive, or a Partition at the beggining of your first hard drive mounted as /boot to point to the linux system and grub.

---

### Post by lha on 2006-01-29
[QUOTE=DaneelS]To make HD setup clearer.  I wonder, is it because the partition with ubuntu on it isn't first on the HD that it won't boot?

[www.megapleb.com/partitions.png](www.megapleb.com/partitions.png)[/QUOTE]
Haven't seen any problems caused by that.

Poor grub-install may get confused when you install on a computer with multiple hds. I guess it is hard for it to find out the mappings between bios disk numbers and os drive names. This is probably where it failed.

When you boot from hda, how far does it get? What do you see? Can you enter grub's command line? Other way to do this is to make a grub floppy. In grub's shell you could find the real mappings of your drives and fix your issues.

Maybe easiest solution would be this: Plug out all other drives except for the one with Ubuntu. Set bios to boot from Ubuntu's drive. [Use these instruction to reinstall grub]("http://ubuntuforums.org/showthread.php?t=76652"). When you reboot, you should find yourself in grub's menu. This shows you are a bit further. You can't use those menu entries to boot Ubuntu because they become obsolete after reinstallation, but they aren't hard to fix. If you want, you can press 'e' to edit them. Try changing 'root (hd2,1)' into 'root (hd0,1) and see if it boots. Now you can plug in your other drives and set bios to boot Windows. If you get this far, come back and we'll fix that menu.lst, too.

ATM, I'm too tired to write the rest of those instructions. Hey, I don't even know if you are going to them. But if you get into that grub menu/command line, the hard part is over.

---

### Post by DaneelS on 2006-01-29
Thanks guys.

I moved the partition so ubuntu is now installed at the start of the HD space.

That allowed me to access the grub menu, even though it doesn't work.

Using the command line I did:

root (hd0,1)
find /boot/grub/stage1
kernel /boot/vmlinuz-2.6.12-9-386
initrd /boot/initrd.img-2.6-12-9-386
boot

That gets to trying to do something with CD-ROM drives where it falls overand leaves me with Busybox (ash) and a # command prompt.

No idea what to do from here.

---

### Post by DaneelS on 2006-01-29
Hitting e to alter the line to (hd0,1) lets it say it's booting, but it doesn't actually do anything.

The rest of the kernel line is root=/dev/sdb2 ro quiet splash

I'm not sure that is correct.

---

### Post by DaneelS on 2006-01-29
I seem to be getting good at guessing.

I tagged back on the root=/dev/sdb2 line at command prompt and things started to happen.

root (hd0,1)
find /boot/grub/stage1
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sdb2 ro quiet splash
initrd /boot/initrd.img-2.6-12-9-386
boot

It spent a number of minutes installing and now I have a login!

It seems to be working, but if I log out I'm not sure how to get back in again!

---

### Post by DaneelS on 2006-01-30
As I feared, I can't get back into ubuntu.

The same commands I used above hang at initializing /dev

:(

---

### Post by lha on 2006-01-30
[QUOTE=DaneelS]As I feared, I can't get back into ubuntu.

The same commands I used above hang at initializing /dev

:([/QUOTE]
Changes you made in grub menu using 'e' were temporary. Did you edit /boot/menu/menu.lst the same way you edited options earlier? Are you sure booting failed while using the exact same options that worked earlier?

---

### Post by DaneelS on 2006-01-30
Using e to edit then booting never worked.  It would just sit there saying bootig but never go anywhere.

Instead I hit c then typed in the command listed above.

As I said, it worked once, finished installing all the packages and let me into desktop.  I didn't alter menu.lst as I didn't have the time (had to go to bed it was 4am!).

I hoped I would be able to hit c again next time and type in the same commands, but now it just hangs at initialising /dev with the ubuntu loading screen showing.

GRUB still doesn't run by itself, I always boot straight into windows, but my Asus K8N mobo lets me hit f8 and pick a boot drive.  I pick the one with ubuntu installed and then proceed as above.  This doesn't really bother me at all, I am happy to select OS in this way and do away with GRUB altogether if I can.

Right now though, I'd just like to get back into ubuntu.  It was working quite well.

---

### Post by DaneelS on 2006-01-30
BTW, I have the Live CD as well, so i guess I can use that to access the install by mounting it.

At this point though, I don't know what I would do to try and fix things.

---

### Post by lha on 2006-01-30
[QUOTE=DaneelS]Using e to edit then booting never worked.  It would just sit there saying bootig but never go anywhere.

Instead I hit c then typed in the command listed above.

As I said, it worked once, finished installing all the packages and let me into desktop.  I didn't alter menu.lst as I didn't have the time (had to go to bed it was 4am!).

I hoped I would be able to hit c again next time and type in the same commands, but now it just hangs at initialising /dev with the ubuntu loading screen showing.

GRUB still doesn't run by itself, I always boot straight into windows, but my Asus K8N mobo lets me hit f8 and pick a boot drive.  I pick the one with ubuntu installed and then proceed as above.  This doesn't really bother me at all, I am happy to select OS in this way and do away with GRUB altogether if I can.

Right now though, I'd just like to get back into ubuntu.  It was working quite well.[/QUOTE]

Usually bioses have option to choose which drive is booted as default, so when you get Ubuntu and Grub working, look for that option to avoid pressing f8 every time you boot.

So now you can use Grub to start Ubuntu, but Ubuntu hangs somewhere down the road. => Grub's not your problem.

Said that, try this, just to be on the safe side. Use grub's command line and type
```
cat (hd
```, then press <tab>. It'll list all your drives. Add a '0' (zero) to that line to make it like this:
```
cat (hd0
``` and press <tab> again. Grub will list all partitions on that drive. Use that information to find out how drives are mapped. (Find out which one of sdX/hda is hd0.) Do the same for each of your drives. Mappings should be the same as in that device.map you posted earlier. If they are, besides changing hd2 to hd0 in menu.lst, I see nothing wrong with your grub setup. I'm starting to believe your problem may be something else...

---

### Post by DaneelS on 2006-01-30
What I don't understand is why it worked once but won't  now, I didn't change anything other than screen refresh which worked perfectly.

Are my kernel and initrd commands correct?

I'll be home in an hour or so to try things out but I don't know where to start.

---

### Post by lha on 2006-01-30
[QUOTE=DaneelS]What I don't understand is why it worked once but won't  now, I didn't change anything other than screen refresh which worked perfectly.

Are my kernel and initrd commands correct?

I'll be home in an hour or so to try things out but I don't know where to start.[/QUOTE]

```
initrd /boot/initrd.img-2.6**-**12-9-386
```
should be
```
initrd /boot/initrd.img-2.6**.**12-9-386
```
Maybe it was just a typo here. The rest looks good to me.

---

### Post by DaneelS on 2006-01-30
It was a typo.

If I remove the quiet command from kernel will I get verbose output that might help pin down the problem?

How long should a boot up take, I must admit I didn't give it ages before restarting.

---

### Post by lha on 2006-01-30
[QUOTE=DaneelS]It was a typo.

If I remove the quiet command from kernel will I get verbose output that might help pin down the problem?

How long should a boot up take, I must admit I didn't give it ages before restarting.[/QUOTE]
Removing quiet will give you more info. Replacing it with debug will give even more. See [http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html") Haven't got the slightest idea if those messages will help you.

Ubuntu takes ~1-2 minutes to boot. (Usually)

---

### Post by DaneelS on 2006-01-30
Yay!

I'm in ubuntu :)

I'm not sure what I did differently.  I took out the quiet and splash and it worked, very strange.

Now I'm trying to get GRUB to work properly, for ubuntu at least, I don't really care about windows as I can just let it boot to that by default.

---

### Post by DaneelS on 2006-01-30
BTW, I only have a 5GB root partition atm.  How do I go about adding a swap partition and home partition?  A FAT32 would be good for transfering files as well.

Do I have to do a reinstall?

I assumed I could just get away with the simplest config to get things working then add what I needed.

---

### Post by lha on 2006-01-30
[QUOTE=DaneelS]BTW, I only have a 5GB root partition atm.  How do I go about adding a swap partition and home partition?  A FAT32 would be good for transfering files as well.

Do I have to do a reinstall?

I assumed I could just get away with the simplest config to get things working then add what I needed.[/QUOTE]

Nice to hear it finally booted. First, fix menu.lst. Open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Replace every hd2 with hd0, including '# groot=(hd2,1)'. If you want to, remove those splash and quiet bits if you think they prevented your computer from booting. (I doubt that.)

You don't have to reinstall to make those partitions. Now you've got good use for that live cd. :) It's not recommended to partition a hd that is in use, so boot with live cd and open gparted. It's a partitioner with a nice gui. Or use my favourite, cfdisk. (Open a terminal and use command 'cfdisk /dev/sdX' where X is the letter of the drive you want to partition.) There are many good guides on partitioning. Try searching forums or with google. (I'm too lazy to find a link for you. ;) )Those partitions would've been a bit easier to set up during install, but you can do it at this stage, too. A word of advice on making fat32 partition: Use windows to do that. This will give you best compatibility. Basically, you have to make the partitions you want and create filesystems. If you make a separate /home, you'll need to copy files from your old home folder to the new partition, rename old home directory (or delete it, I prefer former because it provides a backup), make a new /home directory and edit fstab to use new partition. All other partitions you make also need to be added in fstab.

Hope this helps you forward.

---

