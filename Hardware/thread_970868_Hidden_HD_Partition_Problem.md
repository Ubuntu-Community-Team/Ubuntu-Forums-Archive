---
title: "Hidden HD Partition Problem"
date: 2008-11-04
forum: Hardware
---

### Post by LenWynne on 2008-11-04
Hi,

For the last year I have been running my Dell XPS 410 with a dual boot Ubuntu/WIN (on two different Hard Drives), and finally decided that I wanted to make the switch to only linux. I started with a clean install of 8.1 on the main drive and used Gpart to clean off the old Win drive.  

The problem that I am having is that the second drive (both are Western Digital) has some sort of built in partition &#8211; which I assume are the old WD tools.It shows up in Gpart as a yellow section but cannot be accessed.  I am unable to see any way to remove this. When I mount the volume it shows a locked down Lost+Found folder that takes up about 11GB.

Is there anything I can do to completely clean off this drive? 

Thanks

I am still learning my way around these forums so I am sorry if I posed in the wrong place

---

### Post by Ek0nomik on 2008-11-04
Where are you running GParted from?  The Ubuntu Live CD?

The locks in GParted means that the partition is mounted, and so you cannot make changes to the partition.

If you are using the Ubuntu Live CD, you can unmount the partition, **or** you can download a GParted Live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) which will not mount any partitions.

You can unmount partitions by doing:

```
sudo umount /dev/xxx
```

where xxx is the proper device name.  If you don't know the device name, you can list mounted partitions by doing:

```
fdisk -l
```

---

### Post by ajgreeny on 2008-11-04
I imagine that the partition is a windows restoration system put there by Dell, and I'm surprised gparted could not do anything with it.  Are you sure it was unmounted when you tried to access it or delete it?

Aside from that it could be worth downloading and trying Duke's Boot and Nuke ([dban]("http://www.dban.org/download")), which will wipe anything from a drive as far as I'm aware. It may take a long time, however, depending on the size of your drive and you settings for dban.

---

### Post by LenWynne on 2008-11-04
I tried working with the Gparted CD and pretty much get the same results. It shows my HD or at least the one partition there as being smaller than it actually is. All that is shown in the bar is a small yellow shaded area.

When I go into normal mode and mount the HD it then shows the Lost+Found folder that shows taking about 11Gb of space. I can do nothing with this folder.   :confused:

---

### Post by Lord Xeb on 2008-11-05
Try shredding the disc (WARNING, THIS WILL DESTROY ALL DATA ON DISC AND MAKE IT LIKE YOU JUST BOUGHT IT!)
[code][B]shred -n *<number_of_times_you_want_to_shred>* -z -v [I]/dev/drive_you_want_to_shred [code]
[/I][/B]

---

### Post by LenWynne on 2008-11-05
I am still trying to resolve this issue, but no luck so far.

When I go into BIOS it shows the drives as the correct size (160G and 250G) When the system starts the boot process however the drives show up as being about 149G and 239G. Both of these drives appear to have the hidden partition with the Wester Digital recover tools, although I can no longer access them. Both drives also have the Lost+Found Folders that cannot be accessed.

I tried running the command ~$ fdisk -l and got the following
Cannot open /dev/sda
Cannot open /dev/sdb

I looked into DBAN and I am considering that option but not sure if it will work since the drive size seems to change on boot.  My other concern is the language in the information that says it will find and wipe all drives.  I want to maintain the first drive with Ubuntu installed on it first - at least long enough to get my crucial files imported from windows copied over for safe keeping.

Any other suggestions would be appreciated..

Thanks

---

### Post by zwygart on 2008-11-05
Hi, 

I had some problems with partitions. One off the tools I used wher e Gparted don't worked is fdisk (to erase partition). In a terminal  type "fdisk /dev/sdb" or what your drive is.

Then read on the scree. m for help.
Type p to see the partitions.
d to delete (it will ask you the number which was displayed by p)
w to write and exit.
May be fdisk will not work if I look at the answer off it.
But you may try it.

---

### Post by zwygart on 2008-11-05
Hi, 

I had some problems with partitions. One off the tools I used wher e Gparted don't worked is fdisk (to erase partition). In a terminal  type "fdisk /dev/sdb" or what your drive is.

Then read on the scree. m for help.
Type p to see the partitions.
d to delete (it will ask you the number which was displayed by p)
w to write and exit.
May be fdisk will not work if I look at the answer off it.
But you may try it.

---

