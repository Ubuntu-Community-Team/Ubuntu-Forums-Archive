---
title: "How To: Dual Boot Ubuntu and Vista from Ubuntu ISO"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by lvleph on 2009-02-17
Below I will give instruction for installing Ubuntu from ISO using Windows Vista.

First things first; get your self a copy of an Ubuntu 8.10 ISO and install daemon tools.

Now that you have these, let's move on. In windows vista right click on computer under start menu and then click manage. When the manage window opens click on disk manage on the left. From there you will want to right click the c:\ volume and select shrink volume. I would shrink the volume by at least 10GB. Once the volume has been shrunk we can move on to installing Ubuntu.

Start daemon tools. An icon in the notification area you will see the daemon tools icon; left click the icon and tell it to mount your iso. Once the iso is mounted you will want to run the program on the cd. A program window opens with different selections. Select install in windows. This will install wubi. Go through the process of installing wubi. Don't select an image file larger than the ammount of disk space that you shrunk the windows partition by, it will just be a waste. In fact, I would make it as small as possible. Restart your computer at the end of the install. When the windows boot menu comes up select Wubi.

Once you have logged into Ubuntu you will now want to migrate to your partition. But first we need to install GParted. To do this go to System>Administration>Synaptic Package Manager enter your password. Now do a search for gparted. Mark gparted for installation then click apply. 

Once it is installed go to System>Administration>Partition Editor. You will now see your drive with a grey area. Right click on the grey area and select New. Select ext3 for the file system and enter in the size of the partition. Don't forget you will need to leave some space for the swap partition. Now click add. There should be an additional space of grey left; right click this and then select new. Select files system as linux-swap and then click add. Make a note of the partition locations (/dev/sdaX).

Now lets move the wubi install to those partitions and install grub.
> Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

As an alternative, the following script can be used with Wubi 8.04.

Download [wubi-move-to-partition](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition)

Open a terminal and run:

sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10

Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually.

Once, that is complete you are ready to boot into Ubuntu. Restart your computer and let it boot into Ubuntu. Once you are sure you have everything set up like you want go ahead and boot into windows and uninstall wubi through the windows uninstaller.

---

