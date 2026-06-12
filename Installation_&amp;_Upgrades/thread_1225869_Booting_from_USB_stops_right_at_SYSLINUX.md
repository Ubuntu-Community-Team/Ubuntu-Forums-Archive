---
title: "Booting from USB stops right at SYSLINUX"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by ansorg on 2009-07-29
hi,

I tried two methods to create a bootable USB stick: 

[http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/](http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/) with an kubuntu ISO 

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) with the Netbook Remix IMG

Both result in the same: I reboot, set USB as boot medium. It seems that the USB drive is correctly detected. I get a line like

SYSLINUX ..................

and after that

boot:


Hm, looks like a prompt? I hit ENTER and get someting like "could not find kernel image linux" 


Why does it stop there? What went wrong? How to fix it?


thanks for any pointers

---

### Post by spcwingo on 2009-07-29
You can try unetbootin.  You can read up on it [[COLOR="Red"]here[/COLOR]]("http://unetbootin.sourceforge.net/").

---

### Post by gastly on 2009-07-29
You will need to reformat the USB (if you had ever installed any other cd image/bootloader/os in the USB). I recently had the same problem, I first had [SysRescueCD](http://www.sysresccd.org/Main_Page) installed on the USB and then I wanted to install Xubuntu in it using UnetBootin.

You first will need to format the USB drive; Choose the filesystem which you want to format with.
If you want to format it with fat32, then use:
```
 sudo mkfs.vfat /dev/sdc1 # My device was sdc1, yours may be different
```

And then use unetbootin (like spcwingo suggested) to install the iso contents to the usb.

---

### Post by dandnsmith on 2009-07-29
The SYSLINUX prompt suggests that the bootloader is in place on the USB stick, but the tables controlling it aren't (I don't think it is as helpful as GRUB).

When you install the UNR IMG file, it overwrites the whole of the stick - including any partition table - and can make the size of the stick seem wrong. After doing such an install you need to do a complete repartition and reformat for other uses.

In my experience the unetbootin method works without problems (when used from the start), but some methods can leave you with a stick which doesn't boot properly (I fixed one such by doing a reinstall with the unetbootin procedure).

HTH

---

### Post by ansorg on 2009-08-03
thank you all. I tried a few more times (including reformatting) and got one step further: the busybox prompt. And there I gave up but went a different route:

I started Ubuntu installation from the live CD and installed directly onto the USB stick - voila!

Since I will use this USB drive on two computers that are quite similar (both intel, both nvidia) I can use this system on both machines. Works great so far!

---

