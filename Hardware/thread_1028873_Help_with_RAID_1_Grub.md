---
title: "Help with RAID 1 Grub"
date: 2009-01-02
forum: Hardware
---

### Post by yochaigal on 2009-01-02
Hi all,

I recently installed ubuntu 8.10 desktop on a mirrored 1TB raid array; I used the alternate cd, which correctly identified the raid volume and installed without problems.
On reboot my BIOS reports no media found, however using super grub disk I can boot without any problems into the OS (I am sure grub is correct).

What am I doing wrong, here?

Thanks

---

### Post by bsmith1051 on 2009-01-02
the installer identified an *existing* RAID volume?  When you boot normally do you get the Grub Loading message, because if not Grub never got installed to the drive.

From there, all Grub does is request an 'md' device.  You need to have mdadm configured correctly.  I've never installed to an existing volume, I've always created everything anew during the install; I don't know how to do it manually, sorry.

---

### Post by yochaigal on 2009-01-02
I'm sure grub has been installed. I even popped in the livecd and reset grub up (after installing rmraid in the enviroment, then chrooting to the system partition).

The installer recognized my Volume as the only volume there (created by the RAID array BIOS utility).  
I do not get the grub loading text at all though. Since grub is stored on the hard drive either then the problem must not lie in grub being configured wrong but rather in the partition table itself (or the MFT, or whatever) being "wrong."
I am able to pop in super grub cd and it reads my menu.lst file and lets me boot with no problem from there.

---

### Post by bsmith1051 on 2009-01-03
RAID setup through your BIOS is considering "FakeRAID" by Linux.  Search for that term and you'll find lots of info on using it.  But, long term, it's usually better to use Linux's built-in software RAID.

---

### Post by hotweiss on 2009-01-03
If all else fails, try using the LIVE CD and following these instructions:

1. Go into your motherboard’s BIOS and turn on the RAID support

2. Go into your RAID’s BIOS and set-up your RAID partition

3. Boot the Live CD

4. Open Terminal and type the following:
sudo apt-get install dmraid

5. Once completed the above installation, type the following:
sudo modprobe dm-raid4-5

6. Now it’s time to install Linux Mint

7. Upon reaching the partition menu, select your RAID partition

8. Upon reaching the install confirmation menu, click on the Advanced button and uncheck install boot loader

9. Once the installation is completed, check your partitions by typing the following in Terminal:
cd /dev/mapper
and then:
dir

10. Copy the partition without a number; I will use dabdgddgLinuxFTW as an example

11. Now we have to see how the partitions are set-up, so type the following in Terminal:
sudo fdisk dabdgddgLinuxFTW

12. Type p in Terminal to see the actual partitions:

13. Note and copy which partition is the Linux partition (the other ones you will see is extended and swap); I will usedabdgddgLinuxFTW1 as an example

14. Type q in Terminal to exit fdisk

15. Now we have to mount the RAID partition in order to set-up grub by typing the following in Terminal:
sudo mount dabdgddgLinuxFTW1 /target
and
sudo mount –bind /dev /target/dev
and
sudo mount -t proc proc /target/proc
and
sudo mount -t sysfs sys /target/sys

16. Now we have to set-up grub by typing the following in Terminal:
sudo chroot /target
and
apt-get install dmraid
and
apt-get install grub
and
mkdir /boot/grub
and
cp /usr/lib/grub/i386-pc/* /boot/grub
and
grub –no-curses
and
device (hd0) /dev/mapper/dabdgddgLinuxFTW
and
root (hd0,0)
and
setup (hd0)
and
quit
and
update-grub
(press y when asked to confirm)

17. Finally reboot.

I wrote the above guide for Mint, but it should also work for Ubuntu:

[http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/](http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/)

---

### Post by yochaigal on 2009-01-03
Yes I'd actually tried installing it that way after the alternate install didn't work.  I followed basically the same steps (taken from the ubuntu fakeraid wiki) and did everything listed there.  Same problem!  I actually did it twice but used an ubuntu 8.10 desktop lived.
Still no deal!

---

### Post by bsmith1051 on 2009-01-03
well at least you know what you're trying to accomplish -- install to an existing FakeRAID array.  That's a better description than the original title, i.e., it's not really a GRUB issue.  Maybe post a new question re "Unable to boot reinstalled FakeRAID"?

---

### Post by hotweiss on 2009-01-03
> **yochaigal said:**
> Yes I'd actually tried installing it that way after the alternate install didn't work.  I followed basically the same steps (taken from the ubuntu fakeraid wiki) and did everything listed there.  Same problem!  I actually did it twice but used an ubuntu 8.10 desktop lived.
Still no deal!

I would now try to delete my old RAID partition and create a new one.

---

