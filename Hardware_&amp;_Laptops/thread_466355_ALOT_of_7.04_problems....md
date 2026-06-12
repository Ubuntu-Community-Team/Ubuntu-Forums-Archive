---
title: "ALOT of 7.04 problems..."
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by drluv888 on 2007-06-06
I faced alot some serious problems installing Ubuntu, and using trusty google and alot of time, solved them, resulting in me running into a few more issues with this linux distro. I'm a pretty patient person, and i really enjoy ubuntu, so i really hope a few easy things will get this working. I'm pretty new to linux/unix, and to the terminal, so i haven't any idea how to do anything myself, so here i am asking for help!

---PROBLEMS WITH MY 7.04 INSTALL---

First i ran across a problem with the 7.04 live CD i had to research how to get around the Xserver not working, and I ended up having to type a few commands;
sudo dpkg-reconfigure xserver-xorg
#set that to vesa, 640x480, hsync 36-52, vref 36-60
startx

With that settled i went on to install feisty using the partition manager and it failed, it could not automatically set up a dual boot for some reason, i ended up having to do it manualy by reinstalling windows, partitioning with the windows utility, leaving 20GB for linux and then going back to the live CD (had to use the xserver workaround again) and used manual install on that partition (setting up swap ect.).

and now i have even more problems to solve.

My windows partition is on my desktop, it wont unmount, and is also located in my places drop down and in my media folder as sda1 (see the screenshot). 

I'm not able to use the internet, my dial up modem isnt recognised, and my wireless card dosn't detect my neighbors wireless network, i'm betting normal LAN internet would work, but i dont have access to it right now.

Then theres my resolution problem, only 800x600 and 1024x768 are there, and my laptops LCD supports higher.

And last but not least, my ATI x1300 graphic card is not being recognised.+although im pretty sure i can solve that easily once i get an internet connection and can use apt-get.

------------------------------

These are pretty serious problems, and anyone with my computer looking to test out linux would probably just give up, especially by now. If it takes this much work just to get this working... well then they might as well just use windows. As far as i'm concerned, Ubuntu has a ways to go before its totally usable for the 'human being'.

however, im stubborn, and so im looking for a little help :).
if your willing to offer a hand, let me know what additional information you need, and i'll put it on up here.
and im sure some things are already slved somewhere on here, in which case im sorry for reposting, but could yu link me over?

---

### Post by Patrick-Ruff on 2007-06-06
probably full system specs would be helpful.

---

### Post by drluv888 on 2007-06-06
oh sorry, my bad :)

i have a Dell E1505
dual core 1.6 AMD's
1 gig of ram, and 60 gigs of HD
ATi X1300 video card
Dell's  Wireless 1390 WLAN mini-card
my dial up modem is a Conexant HDA D110 MDC V.92 Modem (COM 3)
and my screen is a replacement from an  Inspiron 6400
its a 15.4" WSXGA LCD with native resolution 1680x1050

and heres that screen shot of the windows partition on my desktop
[IMG]http://i23.photobucket.com/albums/b377/drluv888/Screenshot.jpg[/IMG]

thanks for the help i appreciate it!

---

### Post by elpichi on 2007-06-07
wow, and i thought i was full of issues xD

well i had the same problem with the resolutions i edited my xorg files by going to the console and typing
sudo gedit /etc/X11/xorg.conf
in there on the last lines you would see all the sets of resolutions along with their depths mines is something like this: 
my default depth is 24 so that's the only one i edited.
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768_75.00" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
you can add as many resolutions as your computer takes.

For the partitions mounts/unmounts a simple reboot ussually solves my problems

For the dial up modem, check it is not listed on the restricted drivers, i haven't got any problems with my internet connection(using ethernet)

---

### Post by merlinus on 2007-06-07
Can you post:

```

cat /etc/fstab

```

That may offer some insights.

Also:

```

sudo fdisk -l
blkid

```

l is a lowercase L.

-merlin

---

### Post by drluv888 on 2007-06-07
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=844dab97-1d73-45bf-8848-107a9b468fb5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CAAC9C80AC9C6929 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7f98a97a-f9c7-46ea-8d18-1a48dc883a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

 --AND--

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4562    36644233+   7  HPFS/NTFS
/dev/sda2            6995        7113      955867+  82  Linux swap / Solaris
/dev/sda3            4563        6994    19535040   83  Linux

Partition table entries are not in disk order


/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="7f98a97a-f9c7-46ea-8d18-1a48dc883a6f" TYPE="swap" 
/dev/sda3: UUID="844dab97-1d73-45bf-8848-107a9b468fb5" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by merlinus on 2007-06-07
I think the problem may be that your ntfs partition is read-only, and that may be why it cannot be unmounted.

You can try installing ntfs-3g from Applications/Add Remove.

Make sure Source is set to all (or soemthing like that) from the dropdown list at the top right.

That is what I have done, and I have no problems reading/writing mounting/unmounting those partitions.

Here is the pertinent line from my fstab:

UUID=1EB88F62B88F36F5 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

-merlin

---

### Post by drluv888 on 2007-06-07
alright, for wireless I'm thinking this:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
or if that dosn't work, this:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

for the dial-up modem problem:
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)
where i can get a whooping 14.4K out of my 54K modem...
any other ideas here??

for the ATI x1300 problem:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
otherwise i'll browse the ATI forums...

for the resolution problem:
i'll try what elpichi said
and use another place, which i dont have the link but it pretty much describes what you said in more detail

and for the ntfs problem:
I'll do what you said Merlinus

and yeah, i'm going to bed, and i'll give a full update tomorrow
when i get a change to connect to the web on my laptop.

thanks for the help so far guys, i think i'm almost there!

---

### Post by merlinus on 2007-06-07
I am mistaken about unmounting your windows partition.  It has to be done as root.

In a terminal:
```

sudo umount /media/sda1

```
should do it.

If you want to be able to write to your ntfs partition from ubuntu, however, then installing ntfs-3g will work.

If you want to get rid of its icon on the desktop, that can be accomplished via:
```

gconf-editor

```

apps/nautilus/desktop

uncheck computer_icon_visible and/or volumes_visible

-merlin

---

### Post by drluv888 on 2007-06-08
ahhh thats a head slapper, i was typing "unmount" into the terminal, duh! haha thanks!

---

