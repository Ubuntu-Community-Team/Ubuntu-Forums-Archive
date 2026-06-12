---
title: "Problems with GRUB after upgrading to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by lamps06 on 2009-11-03
Howdy, folks.  I apologize for the post I am about to make because it seems to appear several places already on this message board.  However, despite reading multiple threads and following several how-to guides I have been unable to resolve my issue so I am turning to you folks.

I recently upgraded my dual boot Windows XP/Ubuntu system from 9.04 to 9.10.  I am using a single IDE hard drive that is split into separate paritions, one for each OS (I suppose there are technically multiple partitions that Ubuntu uses).  At any rate, after upgrading to 9.10 I lost the ability to boot into my Windows XP parition.  I have spent some time reading threads and following the GRUB how-tos for properly building my menu.lst but I cannot seem to get my system to boot into Windows any longer.  Below are some more relevant details.

output of fdisk -l:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf19ef19e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18244   146544898+   7  HPFS/NTFS
/dev/sda2           18245       18852     4883760    5  Extended
/dev/sda3           18853       30401    92767342+  83  Linux
/dev/sda5           18245       18852     4883728+  82  Linux swap / Solaris


```

Here are the contents of /boot/grub/device.map:
```

(hd0)	/dev/sda

```

Here are the contents of /boot/grub/menu.lst:
```

title		Windows XP Professional SP3
root		hd(0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		b60f4ebf-467a-45ec-a412-db85b80c231c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b60f4ebf-467a-45ec-a412-db85b80c231c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		b60f4ebf-467a-45ec-a412-db85b80c231c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b60f4ebf-467a-45ec-a412-db85b80c231c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-13-generic
uuid		b60f4ebf-467a-45ec-a412-db85b80c231c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b60f4ebf-467a-45ec-a412-db85b80c231c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid		b60f4ebf-467a-45ec-a412-db85b80c231c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b60f4ebf-467a-45ec-a412-db85b80c231c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.10, memtest86+
uuid		b60f4ebf-467a-45ec-a412-db85b80c231c
kernel		/boot/memtest86+.bin
quiet

```

When I try to launch Windows from this menu.lst I get:
```
error 11:  unrecognized device string
```

I have tried commenting out "root" and using UUID instead, and finding the correct UUID from ```
ls -l /dev/disk/by-uuid

``` but this did not work either and I receive this message:  ```
error 5:  file not found
```

I am able to mount my Windows partition in Ubuntu and I can see that all my files and folders are intact.  I can access files fine on this drive I am just not able to make GRUB boot from it properly.  Does anyone have any ideas?  Thanks.

Oh, I have also noticed that since the upgrade, Palimpsest Disk Utility says that my hard drive has many bad sectors.  From reading a few threads it sounds like this is a bug but I thought I would mention it in case it is relevant.  Cheers.

---

### Post by lamps06 on 2009-11-04
bump

---

### Post by Mark Phelps on 2009-11-05
I have a similar setup and the only difference between my Windows menu.lst stanza and yours is that mine has "rootnoverify (hd0,0)" instead of "root (hd0,0)".

All I can suggest is that you try that change.

---

### Post by witeshark17 on 2009-11-05
A similar problem here. 
solution:

Ctrl-C (it may be just C !!) to enter the GRUB command line
2. Type in *insmod linux* and press ENTER

*linux /boot/vmlinuz-2.6.30-10-generic root=UUID=*     73b2b033-654b-4efa-8e11-17138c4d0333

where  **_73b2b033-654b-4efa-8e11-17138c4d0333**_   < is unique to your system (found after hitting "e" to edit in the boot options list)

then

initrd /boot/initrd.img-_**2.6.30-10**_-generic

where 2.6.30-10  <is your current (latest) kernel

boot And after booting doing a 
sudo grub-install (taget)

I will post more details and corrections as I put this together after a lot of Google!

---

### Post by lamps06 on 2009-11-05
Thanks for the suggestion Mark.  I tried changing my "root" to "rootnoverify" but I still received "error 11: unrecognised device string."

White shark, I have not yet tried your suggestion.  From what you mention it sounds like those commands would only affect how I boot into Ubuntu.  Am I mistaken?  Because I can boot into Ubuntu fine, it is the Windows partition with which I am having trouble booting.

Thanks guys.

---

### Post by lamps06 on 2009-11-09
bump...

---

### Post by oldefoxx on 2009-11-09
I don't have an exact way to deal with this, but if you have a backup of Windows handy, you may be able to restore just track o and/or the MBR.  That may seem no help, but there are a number of sources for PC Recovery tools that can go farther.

Ubuntu 9.10 uses Grub 1.97, what's called Grub2, which is something I haven't really learned yet.  But apparently it presents new challenges.  One way around this is to install Ubuntu 9.04 first, and just tell the Update Manager to Upgrade, and that way it will just grab 9.10 off the internet and overwrite 9.04.  But it will let you keep the earlier Grub 1.5, which has the more typical menu.lst file for making changes.  
And this way you skirt problems with installing 9.10 directly.

I wish I could say that the Windows install CD offered a fix for this, but it really doesn't.  It does offer some repair capabilities and a manual mode for entering commands, but you have to know what you are doing.  This is not so much a Ubuntu problem at this point but just a means of getting Windows going again, then resuming your journey on the Ubuntu trail.  So you might best be searching forums related to Windows, and how to restore the boot process.  I'm sure others have had problems in that regard.

The problem here is that you seem to be focused on the problem being in Grub itself at this point, but it could be an error that Grup is relating of what is going on outside of it itself.  In other words, Grub can't find what it needs on the first drive to get to Windows.  For one thing, there has to be a boot.ini file and for another, the file that actually launches Windows.

Hope this helps.  You are really outside the Ubuntu arena at this point.

---

