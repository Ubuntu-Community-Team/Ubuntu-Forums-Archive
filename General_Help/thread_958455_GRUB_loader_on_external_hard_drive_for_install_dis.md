---
title: "GRUB loader on external hard drive for install disks"
date: 2008-10-25
forum: General Help
---

### Post by kr4zyc1d on 2008-10-25
Hello all, I am in need of some help here as I have been scratching my head for quite a while on this problem. Here is my basic setup:
I have a Dell Inspiron E1505 dual-booting XP, and Ubuntu. Now, I have been setting those up for a while, and every so often an update or install of a new operating system will take place, in which case I must pull out a stack of CD's that I have been carrying with me for the past month or so.

I then had this brilliant idea: Take an external Hard Drive (a spare 2.5 inch that I have lying around) and break it into 4 partitions (Grub, XP, Ubuntu, and Extra). My goal is to be able to boot to the external HD and have grub control all of my partitions, in the sense that there will not be operating systems installed on these partitions but simply the Installer files on each respective partition. In easier terms, I would like to have a boot (live) cd of each operating system stored on the respective partition and be able to call it using grub. I am well aware and have successfully booted and installed Ubuntu via USB but it has always just started with that. I would like a grub loader to show me the options of installer CD's that I have to not only make it simple, but incredibly fast, efficient and no more CD'S!!!

Thus far, I have successfully copied all grub information into the grub partition and can boot to the USB, and when I do, I get the grub option list to pick from my partition (I have set up my menu.lst) I have also setup the Ubuntu partition as per a tutorial on Live USB disks. However, when I choose the grub menu item I get many errors (I change the menu.lst readily while booted and continue trying) of them [Error 17, 19, 1, 8... etc] to name a few.

Either way, does anyone know how to do this successfully. I have a good thought in mind and would really like to wrap this up soon. I have heard thoughts of using BartPE to control the windows partition, but I do not want to go filling this thing up and formatting it every few minutes just to try something new - (i.e., lets do one OS at a time to keep things simple and fast, and then put it all together at the end)

Thanks in advance for anyone who can help out with this project, it will be greatly appreciated and I am willing to write a tutorial on this subject once I can put it to bed. Thanks again.

---

### Post by kr4zyc1d on 2008-10-25
I have a few more details:
External HD is listed as sdb, hd1
Grub sdb1 hd1,0
Linux sdb2 hd1,1
Windows sdb3 hd1,2
Extra sdb4 hd1,3

Those are the labels and disk/partition numbers if they are any more help for figuring this out. Thanks.

---

### Post by caljohnsmith on 2008-10-25
Maybe you've all ready seen this link, but if not it would be a good place to start, mainly the "Manual Approach" section:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That page gives directions for booting a Live CD from a USB drive for example, so to make it work for your multi-partition setup, I think one of the crucial steps would be:
```
sudo syslinux -s /dev/sda2
```
Where sda2 is the Live CD partition for example; I think that would make the sda2 partition bootable so that you could then "chain load" the partition from Grub. Note also that you have to use a FAT16 file system for the partition, which is a bit of a limitation.

Anyway, let me know how it goes, sounds like an interesting project. :)

---

### Post by kr4zyc1d on 2008-10-26
Thanks for the reply.  I actually saw that site and that is where I got the idea.  I used that shell script to do it and it works great... Just as long as that is the only partition that you want to boot to and leave as bootable and use.

My main goal was to boot to grub and have it show my two options: 
Ubuntu
Windows
and when I went and hit Ubuntu, it would start the "live USB" and install, and when I went to Windows, it would also start the installer.

Thanks for the link though, I had actually lost it and was looking for the GUI version that they talk about in the article and couldn't find that link anywhere!  I will keep trying though!

---

### Post by caljohnsmith on 2008-10-27
How about setting up three partitions on your HDD:
```
1st partition = ~10 MB ext3 Grub partition
2nd partition = FAT16 Live CD install
3rd partition = FAT16 Windows Install CD
```
Then install the Live CD to the 2nd partition manually as that help page I linked to tells you how (don't use the generic script); then I can help you install Grub to the 1st partition and also the syslinux boot loader to the 2nd partition. If you can get as far as setting up your partitions and copying the Live CD over as per the help page instructions, I can help you with the rest I think. Once the partitions are setup, please post:
```
sudo fdisk -lu
```

---

### Post by kr4zyc1d on 2008-10-27
Ok, so I had read a tutorial a while ago that showed me how to use Grub on the external HD and it worked, as in I could boot to the hard drive and get a grub loader, but would get errors when I made any decisions.  Even though, I had used the isotosub.sh installer or whatever it is called and it worked perfectly on its own partition (just as long as that partition was marked as the 'boot')  That being said, I followed your lead and did it manually, minus grub on the second partition and changing the files to syslinux and what not did not seem to make it even boot.  So as for me, it looks like the shell installer seems to work 100% thus far unless I am doing something stupid.  As for what you asked me to print: 

```
matt@G-BoxProductions:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3bac3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sda2        52436160    62557109     5060475   82  Linux swap / Solaris
/dev/sda3        62557110   202210154    69826522+  83  Linux
/dev/sda4       202210155   234436544    16113195   af  Unknown

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f13a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       32129       16033+  83  Linux
/dev/sdb2   *       32130     4128704     2048287+   6  FAT16
/dev/sdb3         4128705     8225279     2048287+   6  FAT16

```

I feel like there is a solution out there, and we are close, it is just hard to show all of the answers at once and work through every solution!  Thanks again for looking at this!

---

### Post by caljohnsmith on 2008-10-27
OK, before you go through the trouble of installing Grub, how about we install the syslinux MBR to your external drive so that it will be bootable; since you have sdb2 marked as the active or bootable partition, that should work great to just see if booting sda2 will work. So try the following:
```
sudo apt-get install syslinux
```
Make sure you have that package above installed before doing the following:
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb bs=440 count=1
sudo syslinux -s /dev/sdb2
```
Next reboot, make sure your BIOS is set to boot the sdb drive, and let me know exactly what happens. :)

---

### Post by kr4zyc1d on 2008-10-27
Ok, here is the order of events for me:

```

sudo apt-get install syslinux mtools

mount -t vfat /dev/sda1 /media/disk

syslinux -s /dev/sda1


```

I now have a file called ldlinux.sys in that folder.  
I then reboot and see:

> SYSLINUX message and a ""boot:"" prompt. 

It then says it cannot boot from the kernel: linux (or something along those lines)

I then boot back into Ubuntu and continue on with the instructions:

```

mount -o loop ~/Desktop/Ubuntu.iso /media/disk


```

Next I get to the area where I am supposed to modify the syslinux/syslinux.cfg and cannot because it is a read-only system

> matt@G-BoxProductions:/media/disk$ sudo mv isolinux/ syslinux
mv: cannot move `isolinux/' to `syslinux': Read-only file system


In turn, I cannot do the .cfg file for the same reason!

And the last line of the tutorial says "boot from USB stick".  My BIOS is set up correctly as I have done this a bunch of times.

Out of curiosity, why is this better than the script above, near the middle of the tutorial you sent me?

Hope you can make something of this, I have tried everything I can think of on changing the file names (even breaking down the ISO, then changing the file/folder names manually, then recreating an iso file and using that, no such luck).

---

### Post by caljohnsmith on 2008-10-27
If you were able to get that isotostick.sh script to run previously with no problems, then I agree, you might as well just use that again. Have it install the Live CD to sdb2 of course, and once you can confirm that you can boot into the Live CD on the external drive fine, I can give you specific instructions for installing Grub to sdb1 and letting it take over the booting process so you can boot any of your partitions. Does that sound good? :)

---

### Post by kr4zyc1d on 2008-10-27
Ok, I used the script and have installed it to sdb2 and confirmed that it will boot at startup to the Live USB.  (sdb1 has about 15 mb of space, and sdb2 has about 1 gig, sdb2 has a boot flag on it, set in gparted)

---

### Post by caljohnsmith on 2008-10-27
Great, you can do the following to install Grub to sdb1:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb --recheck
```
Then save the attached menu.lst.txt file to your desktop and do:
```
sudo mv ~/Desktop/menu.lst.txt /mnt/boot/grub/menu.lst
```
Then reboot, and let me know what happens.

---

### Post by kr4zyc1d on 2008-10-27
Ok, I had seen something similar to that when I had set it up before and I had some issues.  But grub installed correctly on the drive.  But when I booted to it, it simply booted to the grub> bash and sat there.  I checked the root (hd0,x) and what not.  Any thoughts?  or possibly I missed something...

---

### Post by caljohnsmith on 2008-10-27
The menu.lst probably didn't get copied over, so try:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt/boot/grub/menu.lst
cat /mnt/boot/grub/menu.lst
```
If cat says "file not found", then you'll need to try and copy over the menu.lst again.

---

### Post by kr4zyc1d on 2008-10-27
You... are awesome.  I had been trying everything around that for so long (I kept using (hd1,0) and it said that it couldn't mount it, even though I thought that it was device (hd1), which it was but when it boots I suppose it defaults as (hd0) which makes sense.  

Either way.  Now that linux is done, what kind of genius are you with windows xp live USB?  I have heard of BartPE, but I am unsure of it and didn't know if there was an easier way, such as what you just did with linux.  Thanks again!

---

### Post by caljohnsmith on 2008-10-27
That's great news it works. :) I don't know about installing BartPE to a HDD to boot it, but I'll bet somebody has figured out how to do it. One place I would check would be to search the forums at:

[http://www.boot-land.net/](http://www.boot-land.net/)

And if you can't find a specific thread about it, I bet you can get help there getting BartPE to boot from a HDD. If you can get that far, I'm fairly certain we could easily add it to Grub to boot. Sorry I can't help more with that one, but keep me posted on what you come up with. :)

---

