---
title: "Installation problems"
date: 2008-11-30
forum: General Help
---

### Post by -Cluster- on 2008-11-30
I have tried on several occasions, unsuccessfully, so rather than giving up I decided to come get some help. The basic problem is that once I install it I can't run it;

I install using a burnt DVD, once the installation is complete try and boot from HDD and I get an error message;

 "ERROR: GRUB error 2.0"

I tried to have a dual boot and this error seemed to have some how delete my windows. I think that my have something to do with how I installed it. 

I believe the problem has something to do with the fact I have to install 3rd party RAID drivers to install windows but I can't seem an option to install them? This could be the problem or I could be totally wrong, this is why I came to you!

---

### Post by -Cluster- on 2008-12-01
Just an update managed to mess about probably not for the better now i get a grub error 22

---

### Post by -Cluster- on 2008-12-01
More good News! What ever i did to make error 22 appear is fixed as now i get error 2 again :)

---

### Post by -Cluster- on 2008-12-01
Well the good news keep rolling in!! I have a new grub error.....drum role.....21!!!

---

### Post by caljohnsmith on 2008-12-01
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by -Cluster- on 2008-12-02
Right i am on it!

---

### Post by -Cluster- on 2008-12-03
I am guessing these are to check my HDD i would just like to say there is nothing wrong with them: but any how;

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa75e8e96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sda
33c0

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0000

---

### Post by caljohnsmith on 2008-12-03
OK, according to those commands you ran, it looks like your internal sda Windows drive has a Windows MBR (Master Boot Record), so can you still boot into Windows OK? Also, you have sda and sdb in a RAID array? If you want to install Ubuntu and keep your two drives in their current RAID configuration, you could give this tutorial a try:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I should mention though that it is far easier to install Ubuntu when there is no RAID configuration involved, but it can be done in most cases if you want to go through the trouble (as the above link shows). Let me know how that goes.

---

### Post by -Cluster- on 2008-12-03
> **caljohnsmith said:**
> I should mention though that it is far easier to install Ubuntu when there is no RAID configuration involved, but it can be done in most cases if you want to go through the trouble (as the above link shows). Let me know how that goes.

Ok what is this easier way, I have windows installed now in this way as its the only way it will install. If there is a way to install ubuntu with windows still on thats ideal. if not then ohh well how do i install ubuntu

---

### Post by caljohnsmith on 2008-12-03
If you disconnect your sdb drive, does Windows on your sda drive still boot? Is your RAID entirely software based or do you have to configure your BIOS too? Can you disable the RAID drivers in Windows and still get Windows to boot? 

Another option is to install Ubuntu inside of Windows via Wubi. If I remember correctly, you can do that by choosing the second "Install Ubuntu" option from the Live CD, instead of choosing the first "Try Ubuntu without making changes" type option. But if you can break your drives out of their RAID configuration and still get Windows to boot OK, then I think installing Ubuntu to its own partition is more ideal than Wubi.

---

### Post by -Cluster- on 2008-12-03
OK, I can't Disconnect the HDD's as its a laptop and i still have a little warranty left.
 I don't do anything in BIOS just when i am prompted i press f6 (in windows installation) and select the drivers i have. The RAID drivers have to be installed to run windows otherwise the HDD aren't detected and i can't install on them.
  I have tried installing Ubuntu in many ways, one of which is off the cd the "install Ubuntu" option. I also have tried installing it like a program in an open windows OS. I have also installed it on its own partition. All these fail.

Its not keeping windows running (although that would be handy) its the actual installing of ubuntu, i haven't been able to load a running version of it apart from running from cd.

---

### Post by utnubuuser on 2008-12-03
I suppose running Ubuntu from an external disk is not an option?
How about usb-flash?

---

### Post by -Cluster- on 2008-12-04
I have a 1 GB usb pen drive

---

### Post by -Cluster- on 2008-12-06
Excuse me what am i doing?

---

### Post by -Cluster- on 2008-12-06
Ok something new. When I install it using the cd while running windows it sort of works!!!

One problem when i launch ubuntu it only shows a command prompt
The CMD prompt title is:
(initramfs)

Before it it says something like busybox v2.1(Ubuntu....) in built shell ash

---

### Post by -Cluster- on 2008-12-08
So can any one help me?

---

### Post by -Cluster- on 2008-12-11
I've done it!!!!

And it was really simple as suspected!

all you need to do is download the alternative CD and use that as an installation CD. It ask you if you want to sort out the RAID devices and does it all for you....here is a link

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

