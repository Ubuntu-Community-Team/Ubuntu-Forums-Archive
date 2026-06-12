---
title: "NTFS external drive not detected"
date: 2012-01-02
forum: Hardware
---

### Post by redaxe90 on 2012-01-02
Hi there, I'm back with a different problem

First off, I'm running Ubuntu 11.04, using the Lubuntu desktop environment. Also sometimes going to the LXDE environment for variety. Same problem is showing everywhere.

I've already got 3 internal hdds, taking up sda1, sda5, sdb1 and sdc1.

I have a recently acquired USB control box, with the S-ATA drive from my old laptop. I plugged it into my oldish computer and for some reason it won't show up anywhere, not in GParted, nowhere that I can spot in the terminal and of course won't mount at all.

I tried searching for it in GParted, without success.

I tried the following:


**cat /etc/mtab**
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/sdb1 ext3 rw,errors=remount-ro,user_xattr,commit=0 0 0
/dev/sdc1 /media/sdc1 ext3 rw,errors=remount-ro,user_xattr,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tommi/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tommi 0 0

I can neither make heads nor tails on what this means, so that's why I come back to you people.

Is there anything I can do to detect that external storage box and if there is, what the smeg is it??:confused:

The hdd inside the box has a lot of valuable data, so I have no intention of formatting it or deleting partitions, I just want to review the contents and see if I can use it as an extra storage box, in case I ever run out of space.

---

### Post by redaxe90 on 2012-01-03
I'm bumping this to see if anybody knows what can be done

---

### Post by BLTicklemonster on 2012-01-03
Just for the heck of it, try installing pysdm and see if it shows up then. 
sudo install pysdm
then 
sudo pysdm 
to run it.

---

### Post by redaxe90 on 2012-01-03
Sorry to be so dim, but this is the response I get to the first sudo command


**install: missing destination file operand after `pysdm'**

I'm sure I missed something, but I'll be damned if I have a clue

---

### Post by BLTicklemonster on 2012-01-03
I'm sorry, it's 
sudo apt-get install pysdm

---

### Post by redaxe90 on 2012-01-04
It turned out that I already had it installed, but it didn't show me anything out of the ordinary. Next step is to reboot with the external drive already hooked up and see if it makes any difference

---

### Post by redaxe90 on 2012-01-05
Well, it turns out that the BIOS of my old computer probably can't handle an external storage device being hooked up before booting, since it froze before even trying the POST. Thanks for trying to help, I reckon I better upgrade as soon as my finances allow for it.

---

### Post by dandnsmith on 2012-01-05
It may well be the PSU unable to handle the current load for the usb stuff at bootup - this has been a problem with things like usb modems, printers ...

As to the failure to detect the external HDD, have you tested it in the usb connection with any other system? Some usb enclosures fail to handle HDDs, being intended for other devices.

---

### Post by redaxe90 on 2012-01-05
> **dandnsmith said:**
> It may well be the PSU unable to handle the current load for the usb stuff at bootup - this has been a problem with things like usb modems, printers ...

As to the failure to detect the external HDD, have you tested it in the usb connection with any other system? Some usb enclosures fail to handle HDDs, being intended for other devices.

I've plugged the external drive to 2 other computers in the household and both read it without any problems at all, so it's obviously something on my computer. The PSU is new, 300 or 350 Watt with very low use, because the GFX card is a 64MB Nvidia card made by Siluro and then I have one optical drive and 3 internal hard drives. I have an expansion card for one more hdd, but since I'm lacking in electrical cables, that drive isn't in use.

So the load shouldn't be a problem at all.

---

### Post by dandnsmith on 2012-01-06
OK, so you've covered the enclosure compatibility.
To complete that side of things I can see 2 more loose ends:
a) the particular rails on that PSU not providing the current (not sure what happens if it falls short)
b) a BIOS limit on the current for each USB socket

I forgot to ask whether that enclosure has its own power supply, or relies on current down the USB lines.

---

### Post by redaxe90 on 2012-01-06
> **dandnsmith said:**
> OK, so you've covered the enclosure compatibility.
To complete that side of things I can see 2 more loose ends:
a) the particular rails on that PSU not providing the current (not sure what happens if it falls short)
b) a BIOS limit on the current for each USB socket

I forgot to ask whether that enclosure has its own power supply, or relies on current down the USB lines.

The enclosure has to rely on current down the USB cable, but it's also the only USB peripheral I'm trying to use. The keyboard is the old style PS/2 variant and same goes for the mouse.

So my final conclusion has to be that the motherboard just doesn't support this external enclosure, it's quite an old motherboard anyhow, AMD Tbird 1GHz CPU is quite old and probably not supposed to support this type of USB 2.0 connections anyway. The built in USB ports are both of the 1.0 variant, so I might actually need an expansion card to support USB 2.0, not even mentioning 3.0 :)

---

### Post by dandnsmith on 2012-01-06
You're probably right there. There might be a BIOS update, or there might be some special drivers from the manufacturers which would do the trick. Otherwise the expansion card sounds likely.

Good hunting.

---

