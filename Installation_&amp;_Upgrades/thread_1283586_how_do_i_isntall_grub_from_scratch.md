---
title: "how do i isntall grub from scratch?"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2009-10-05
[http://ubuntuforums.org/showthread.php?t=1282057](http://ubuntuforums.org/showthread.php?t=1282057)
continueing from this thread, after executing a couple of terminal commands, i got ubuntu installed on one of my harddisk partitions, except i didnt install grub (the guide in that thread was using lilo)

my /boot folder has no stage1 file for grub. it only has 4 files and no grub folder.


how do i go about installing grub on my _external harddisc's mbr_? 

how do i make sure this grub only activates when i select my harddisk from the bios boot menu? 

thanks in advance

---

### Post by Meow27 on 2009-10-06
im looking at grub4dos, but im not sure whether this grub option is looking realistic. as i want the harddisk's MBR to activate a boot loader on every computer it boots with.

would GAG work for this sort of thing? I find it difficult handling Gag because the way to figure out what boots where is confusing, and doesnt always work (for linux OSes at least)

---

### Post by lindsay7 on 2009-10-06
Take a look at SuperGrub and download it from their web site. They have good documentation and this could fix you problem.

---

### Post by Meow27 on 2009-10-06
the problem with supergrub disk is that most of the features expect you to have grub installed one way or another..... though it would be great if somebody could direct me to a specific case in thier website

thanks for the reply though

---

### Post by lindsay7 on 2009-10-06
You can install grub from synaptic or try

sudo apt-get install grub


Also see,

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Meow27 on 2009-10-06
again it requires a stage1 file... something i dont have.... should i download grub and just shove a stage1.S file in there?

---

### Post by lindsay7 on 2009-10-06
See if this helps,

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

### Post by Meow27 on 2009-10-07
yeah... im starting to think that grub isnt my solution.. it says grub needs ot adjust for the bios of whatever im installing grub in, but does grub do that automatically or is it configured to do it for a specific bios setting?


in any case, my traveling external harddisk cant use this sort of solution. 

should i try lilo? or will that give me the same problem?

will i have any problems with the bios if grub is installed in my ubuntu partition as opposed to the mbr?

i was planning to have a couple of livecd's booted in other partitions as well, does that mean my dream of a triple bootable external harddisk is an impossible dream?

edit-------
after reading a bit on lilo it seems that that is also an impossible dream...... 
.....

---

### Post by oldfred on 2009-10-07
I do not know what you mean by grub adjust for the bios setting? It would only be important for settings using the older root (hdx,y) style, since that may change if your portable is not the same x every time. You would have to use (hdx,y) for windows. But if you set it as first and in BIOS boot your USB drive first it will always be first.

But with grub you can use UUID or label partitions and use the labels to boot. UUID are not supposed to ever change and not to be duplicated but some partition copy programs also copy the UUID so it is a true copy. If you set labels you control if they are unique.

---

### Post by Meow27 on 2009-10-07
how do i label partitions?

and is the uuid of my harddisk equivalent ot its serial number?

---

### Post by lindsay7 on 2009-10-07
Type blkid in the terminal to get your uuids

You can use Gparted to label your partitions.

---

### Post by Meow27 on 2009-10-11
gparted isnt detecting anything in my harddisk for some reason, tested on my desktop as well, i dont remember having this problem..

fdisk works though...
```
sudo fdisk -l

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x515ccb5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       33387   268181046    7  HPFS/NTFS
/dev/sdf2           33388       38913    44387595    5  Extended
/dev/sdf5           33388       34024     5116671    b  W95 FAT32
/dev/sdf6           34025       34828     6458098+  83  Linux
/dev/sdf7           34829       35089     2096451   82  Linux swap / Solaris
/dev/sdf8           35090       38913    30716280   83  Linux
```

---

### Post by Meow27 on 2009-10-11
i tried this command

its a reiserfs fs

```
tune2fs -L Nomad /dev/sdg8
tune2fs 1.41.4 (27-Jan-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sdg8
Couldn't find valid filesystem superblock.
```

(in this case sdg and sdf are the same)

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> 

my /boot folder has no stage1 file for grub. it only has 4 files and no grub folder.


how do i go about installing grub on my _external harddisc's mbr_? 



I think that the **grub-install** command would install a stage1 file. Try instructions here...

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

---

### Post by Meow27 on 2009-10-11
thanks for the reply

```
sudo grub-install /dev/sdg
/dev/sdg does not have any corresponding BIOS drive.

```

---

### Post by oldfred on 2009-10-11
Herman's site says this:

[FONT=Bitstream Vera Sans Mono]sudo grub-install --root-directory=/media/disc /dev/sdf[/FONT]

---

### Post by Meow27 on 2009-10-11
> **oldfred said:**
> Herman's site says this:

[FONT=Bitstream Vera Sans Mono]sudo grub-install --root-directory=/media/disc /dev/sdf[/FONT]

am i supposed to substitute anything in that code?

thanks

edit----

what is /media/disc?

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> am i supposed to substitute anything in that code?

thanks

edit----

what is /media/disc?

Yeah, it's not clear. you have to substitute /media/disc with the path of your root directory. I'll go and have a read of the official Grub manual and see if I can work out what's required.

---

### Post by mechro on 2009-10-11
I assume you're trying to do this from a LiveCD so using Nautilus can you navigate to the folder where your / (root) or /boot folder that you want to set up is located. From the LiveCD it's probably in the /media folder. When you find it tell me the full path to the location.

---

### Post by Meow27 on 2009-10-11
i have 4 drives in that harddisk.......

but the issue here isn't much of which partition, but the mbr first.......

it differs since i have two linux filesystems......

but it would either be disk, disk-1

/media/disk/boot
/media/disk/root

---

### Post by mechro on 2009-10-11
Yes the /dev/sdf part is sorting out the MBR but you need to identify the location of where the Grub stuff is going

---

### Post by Meow27 on 2009-10-11
> **Meow27 said:**
> i have 4 drives in that harddisk.......

but the issue here isn't much of which partition, but the mbr first.......

it differs since i have two linux filesystems......

but it would either be disk, disk-1

/media/disk/boot
/media/disk/root


> **mechro said:**
> Yes the /dev/sdf part is sorting out the MBR but you need to identify the location of where the Grub stuff is going
i edited the post immediatly after posting...

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> i edited the post immediatly after posting...

What is in disk and disk-1? We're trying to find your Ubuntu installation (I think:confused:)

---

### Post by Meow27 on 2009-10-11
one has my installation, the other im planning to use unetbootin to frequently inject different livecds, DVDs into.

i know which drive to refer to.

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> 

i know which drive to refer to.

Yes, but we're trying to establish how Grub wants you to refer to it.

So the command should be...

sudo grub-install --root-directory=/media/disk /dev/sdf

or

sudo grub-install --root-directory=/media/disk-1 /dev/sdf

---

### Post by Meow27 on 2009-10-11
```
sudo grub-install --root-directory=/media/disk /dev/sdbgrub-probe: error: Cannot find a GRUB drive for /dev/sdb8.  Check your device.map.

[: 494: =: unexpected operator
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /media/disk/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

where do the UUIDs come into the equation here?

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> 

where do the UUIDs come into the equation here?

Grub uses UUID's in the /boot/grub/menu.lst file.

---

### Post by Meow27 on 2009-10-11
.. i dont have a menu.lst in the drive.....

my primary disk doesnt seem to be affected though

edit:

is there a grub option to reboot? (i dont want to 'just' type sudo reboot)

---

### Post by mechro on 2009-10-11
> **Meow27 said:**
> .. i dont have a menu.lst in the drive.....

my primary disk doesnt seem to be affected though

edit:

is there a grub option to reboot? (i dont want to 'just' type sudo reboot)

OK. I surrender! What with all the confusion over your drive/partition device labels I don't really know what you're trying to achieve. :)

Try this Ubuntu Howto for repairing Grub...

[https://help.ubuntu.com/community/GrubHowto#Backup](https://help.ubuntu.com/community/GrubHowto#Backup)

Scroll down to **Backup, Repairing and Reinstalling GRUB**

Good Luck.

---

### Post by Meow27 on 2009-10-12
thanks, but to answer your question,
please refer to the thread linked in the 1st post :3

---

### Post by mechro on 2009-10-12
> **Meow27 said:**
> thanks, but to answer your question,
please refer to the thread linked in the 1st post :3

Ahh! Right, I see. To go back to the original problem, perhaps it's because you were trying to install Karmic which is still beta. Perhaps you should have tried Jaunty.

So the manual install means Ubuntu hasn't generated a menu.lst. To generate one which fits your system is beyond my capabilities. I would go with the GUI part install solution in the Howto although that may mean you're back to the original problem.

---

### Post by Meow27 on 2009-10-12
we still aren't in the same page, the commands (ill edit this post later) installed ubuntu in my drive. i seemed to have everything BUT a bootloader.

i didn't bother installing karmic in since its incomplete. but i have installed jaunty on it. this is information i haven't bothered posting.

now i have a stage1 and a stage2 file in the /boot/grub (which exists now thanks to you :3) i just have everything but a menu.lst file. i pasted my primary one to the drive, removed most things and applied the correct UUID for the partition i installed it in. i dont know if its enough though. but again, i haven't tried yet. 

-meow

---

### Post by mechro on 2009-10-12
> **Meow27 said:**
> we still aren't in the same page, the commands (ill edit this post later) installed ubuntu in my drive. i seemed to have everything BUT a bootloader.

i didn't bother installing karmic in since its incomplete. but i have installed jaunty on it. this is information i haven't bothered posting.

now i have a stage1 and a stage2 file in the /boot/grub (which exists now thanks to you :3) i just have everything but a menu.lst file. i pasted my primary one to the drive, removed most things and applied the correct UUID for the partition i installed it in. i dont know if its enough though. but again, i haven't tried yet. 

-meow

It sounds like you're almost there.

Have you tried booting it yet?

You may still have to tweak the menu.lst and/or do a grup setup (different from grub-install)

---

### Post by Meow27 on 2009-10-12
so i loaded the disk into the drive..... AND GRUB WORKED :D

well, sort of.. grub loads but i think my menu.lst is buggy, ill post it. i get a grub 15 error (file not found)

---

### Post by oldfred on 2009-10-12
Grub error 15 is most likely a typo in menu.lst if you manually edited it,
[http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

Herman's site has several recommendations on how to fix.

---

### Post by Meow27 on 2009-10-12
still couldnt figure out whats wrong


```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		025b9b30-90d0-46aa-a3c3-14d6c51a6a32
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=025b9b30-90d0-46aa-a3c3-14d6c51a6a32 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		025b9b30-90d0-46aa-a3c3-14d6c51a6a32
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=025b9b30-90d0-46aa-a3c3-14d6c51a6a32 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5714963d-98d6-458c-b31a-1f12491db774
kernel		/boot/memtest86+.bin
quiet
```

i just realized.. that the uuid for the memtest is wrong.... will that effect the whole thing? because the main option dont work right now...

---

### Post by Meow27 on 2009-10-12
i tihnk i found the problem....
```
/media/disk/boot$ ls
abi-2.6.28-11-generic     grub            System.map-2.6.28-11-generic
config-2.6.28-11-generic  memtest86+.bin  vmcoreinfo-2.6.28-11-generic

```

is there a way i can manually insert the header files?

---

### Post by oldfred on 2009-10-13
The best way is to have the system do it itself. You have to use a liveCD and chroot or be in your system from the liveCD. You have to know what partition your system is on. Open a terminal and copy these commands. Do not copy any comments # or after # on  same line.

Of course you must first know what partition you want to mount, in this example I'm using [COLOR=DarkRed]sda5[/COLOR]:

sudo mount /dev/[COLOR=DarkRed]sda5[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
#apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
sudo apt-get install grub  #make sure grub is updated & rewrite menu.lst
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#When done:

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by Meow27 on 2009-10-13
my method of going about installing the OS on my harddisk apparently is flawed. i forgot that account needed to be created and time settings etc etc etc

im gonna need to find a way to install ubuntu to my harddisk that way (through the terminal only in a certain partition, see link in the 1st post).... or maybe do all of that stuff as is now........

ill need to take a 2 week break on this project. thanks for the help so far guys. 
the above post worked, but ubutnu wasn't installed correctly (my fualt)

thanks for everything so far guys!

---

