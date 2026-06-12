---
title: "removed driver ati opensource by Synaptic now it wont boot"
date: 2012-01-18
forum: Hardware
---

### Post by jcer93705 on 2012-01-18
Hey guys I uncheck all the unrelated ati because i ended up having ati driver installed plus opensource so I went through synaptic and removed all the ati related. LOL now I cant boot. I missed up and I'm no expert. How can I install the opensource driver? I have a ATI Radeon™ HD 4250 built into my laptop and also I'm on ubuntu 10.10 with latest kernel. Thanks guys. Sorry for my dumb self screwing up. I just thought that if i uninstall from synaptic maybe i could install ati driver now i just want to stay on opensource. I guess i need to uninstall the ati driver too so. Can someone help me with step by step? Thanks

---

### Post by coffeecat on 2012-01-18
> **jcer93705 said:**
> LOL now I cant boot.

Do you mean that you can't boot at all, or that you can't boot into a GUI?

If it's simply that booting into a GUI fails, try booting up and when you get the xserver error, press alt-ctrl-F1 to get to tty1 and log in. You will probably need to connect your laptop to your router with an ethernet cable in case wireless doesn't connect. Now run:

```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

Now reboot.

If that's not possible, boot into recovery mode with an ethernet cable attached and choose "drop to root shell with networking". Now run the above three commands but without the sudo and then reboot.

If that is also not possible, then all is not lost. You can boot up with a live CD/USB, chroot into your hard drive Ubuntu and run those commands that way. Post back if you need help with that and give details of which partition your Ubuntu root partition is.

---

### Post by jcer93705 on 2012-01-20
> **coffeecat said:**
> Do you mean that you can't boot at all, or that you can't boot into a GUI?

If it's simply that booting into a GUI fails, try booting up and when you get the xserver error, press alt-ctrl-F1 to get to tty1 and log in. You will probably need to connect your laptop to your router with an ethernet cable in case wireless doesn't connect. Now run:

```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

Now reboot.

If that's not possible, boot into recovery mode with an ethernet cable attached and choose "drop to root shell with networking". Now run the above three commands but without the sudo and then reboot.

If that is also not possible, then all is not lost. You can boot up with a live CD/USB, chroot into your hard drive Ubuntu and run those commands that way. Post back if you need help with that and give details of which partition your Ubuntu root partition is.


Hi well no can do. One one kernel screen would be flashing single color but will be flashing different color one color to another color and wont do anything. Other kenel that is loaded which is latest kernel would be only a black screen and cant do anything. Other kernel I dubt it would work. Now what? Oh and thank you.

---

### Post by coffeecat on 2012-01-20
> **jcer93705 said:**
> Hi well no can do. One one kernel screen would be flashing single color but will be flashing different color one color to another color and wont do anything. Other kenel that is loaded which is latest kernel would be only a black screen and cant do anything. Other kernel I dubt it would work. Now what? Oh and thank you.

The next step would be to try a chroot from a live CD. Question: if you boot into a live CD (or USB) session, can you connect to the internet? Also - we need to know which is your Ubuntu root partition before I give you all the code for chrooting and reinstalling the ATI driver. Boot up a live CD/USB and post the output of this command:

```
sudo fdisk -lu
```

---

### Post by jcer93705 on 2012-01-20
> **coffeecat said:**
> The next step would be to try a chroot from a live CD. Question: if you boot into a live CD (or USB) session, can you connect to the internet? Also - we need to know which is your Ubuntu root partition before I give you all the code for chrooting and reinstalling the ATI driver. Boot up a live CD/USB and post the output of this command:

```
sudo fdisk -lu
```

Hi yes I can connect to internet with ubuntu by wired. But ubuntu latest os the wifi is sooo slow. I manually installed drivers on ubuntu 10.10 and been working well. So..... I'll boot up with live when I wake up and run you're code and I'll post back. It's 5:32am and need to head to bed but I wake up early. But thanks for taking you're time. I'll get back to you soon as possible when I wake up. Probably be the first couple things I will do when I wake up unless kids don't let me. Thanks again.

---

### Post by jcer93705 on 2012-01-20
> **coffeecat said:**
> The next step would be to try a chroot from a live CD. Question: if you boot into a live CD (or USB) session, can you connect to the internet? Also - we need to know which is your Ubuntu root partition before I give you all the code for chrooting and reinstalling the ATI driver. Boot up a live CD/USB and post the output of this command:

```
sudo fdisk -lu
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41477f0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    26626047    13312000   27  Unknown
/dev/sda2   *    26626048    26832895      103424    7  HPFS/NTFS
/dev/sda3        26832896   632928869   303047987    7  HPFS/NTFS
/dev/sda4       632930304   976773119   171921408    f  W95 Ext'd (LBA)
/dev/sda5       632932352   637136895     2102272   82  Linux swap / Solaris
/dev/sda6       637138944   679084031    20972544   83  Linux
/dev/sda7       679086080   976752639   148833280   83  Linux

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7744511     3868160    b  W95 FAT32

---

### Post by coffeecat on 2012-01-20
You have two ext3 or ext4 partitions for Ubuntu, so I'm going to have to guess which is the root partition. You have sda6, approx 21.5GB, and sda7, approx 152GB. My guess is that sda7 is your home partition and sda6 the root partition, and the commands below make that assumption. If I'm wrong you'll have to amend the first command.

OK then. Boot into your live CD or USB and make sure you are connected to the internet. Don't try to mount your hard drive partitions with the nautilus file browser. Now from a terminal:

```
sudo mount /dev/sda6 /mnt
```

That's the one you need to change if sda6 is not your root partition. Now:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
```

That does everything necessary to chroot into your hard drive root partition, and the prompt should now be a '#' one signifying that you have root privileges. Take care with what follows! Now:

```
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

For good measure, I would suggest you also run this following. The proprietary driver creates an xorg.conf file which is not necessary for the open source driver, and could be an issue. This may not be necessary but it won't do any harm to run it.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

(The X11 is capital-X, eleven.) If it returns a "file not found" error and you have typed that in correctly, that's just fine.

Now:

```
exit
exit
```

And now reboot. Let us know what happens. There is one other (small) thing that may be necessary, but let's see how your system behaves now.

---

### Post by jcer93705 on 2012-01-20
> **coffeecat said:**
> You have two ext3 or ext4 partitions for Ubuntu, so I'm going to have to guess which is the root partition. You have sda6, approx 21.5GB, and sda7, approx 152GB. My guess is that sda7 is your home partition and sda6 the root partition, and the commands below make that assumption. If I'm wrong you'll have to amend the first command.

OK then. Boot into your live CD or USB and make sure you are connected to the internet. Don't try to mount your hard drive partitions with the nautilus file browser. Now from a terminal:

```
sudo mount /dev/sda6 /mnt
```

That's the one you need to change if sda6 is not your root partition. Now:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
```

That does everything necessary to chroot into your hard drive root partition, and the prompt should now be a '#' one signifying that you have root privileges. Take care with what follows! Now:

```
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

For good measure, I would suggest you also run this following. The proprietary driver creates an xorg.conf file which is not necessary for the open source driver, and could be an issue. This may not be necessary but it won't do any harm to run it.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

(The X11 is capital-X, eleven.) If it returns a "file not found" error and you have typed that in correctly, that's just fine.

Now:

```
exit
exit
```

And now reboot. Let us know what happens. There is one other (small) thing that may be necessary, but let's see how your system behaves now.


Hi I have fedora i'm dual booting win 7 with fedora and ubuntu.

---

### Post by coffeecat on 2012-01-20
> **jcer93705 said:**
> Hi I have fedora i'm dual booting win 7 with fedora and ubuntu.

OK. You need to work out which of sda6 and sda7 Fedora is on and which Ubuntu, and amend the first command if necessary. I doubt you'll do any damage if you chroot into Fedora by mistake, so long as you don't go beyond the first apt-get command. If you run "apt-get install xserver-xorg-video-ati" in Fedora, you'll simply get an error message. Probably one of stunned disbelief! :wink:

If you do need help distinguishing which partition is which, then run the boot info script, either from Fedora or from an Ubuntu live CD. Here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you do, post the the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by jcer93705 on 2012-01-21
> **coffeecat said:**
> OK. You need to work out which of sda6 and sda7 Fedora is on and which Ubuntu, and amend the first command if necessary. I doubt you'll do any damage if you chroot into Fedora by mistake, so long as you don't go beyond the first apt-get command. If you run "apt-get install xserver-xorg-video-ati" in Fedora, you'll simply get an error message. Probably one of stunned disbelief! :wink:

If you do need help distinguishing which partition is which, then run the boot info script, either from Fedora or from an Ubuntu live CD. Here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you do, post the the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

Oh sorry for the mistake I forgot to correct myself yesturday but I was busy drinking. But anyways it's opensuse instead of fedora and yes I'll check soon. Thanks man.

---

