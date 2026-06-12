---
title: "How can I Dual Boot Windows XP"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by fatty on 2006-01-26
I installed Ubuntu Gnome about a week ago and was and am very pleased with it.  But, because I still want to do some Windows applications I decided to set my computer up to dual-boot with Windows XP.  I made a partition for Windows and installed it fine.  I probably should have figured this would happen, but now I can only boot into Windows and can't access Ubuntu at all.  I did some research on how to dual-boot and it seems like Grub would do the job but I don't know how I could install it without Linux, and as it is, I can't even access my Ubuntu system.  Can someone please tell me how to set up dual-boot from Windows XP, or atleast get into my Ubuntu installation so I can set up dual-booting from there?

---

### Post by Koobi on 2006-01-27
if you have the CD you installed Ubuntu from, you can boot your computer with the CD and at the prompt type:

```

rescue

```

and follow the instructions...it will probably ask you for the language you want to use, the kyeboard type, etc. at the end of all this, it will give you a shell prompt.

this is the part where you install GRUB because it seems that installing windows will erase your MBR, but first, you should know where to install it.
to find this out do:
```

sudo fdisk -l

```

this would show you which is the boot partition indicated by the Asterisk under the boot column. the corresponding row is the boot partition. so, assuming /dev/hda3 is your boot partition, you would do this:
```

grub-install /dev/hda3

```

this will install grub for you.


at this point, you have to edit a GRUB file that will show you Windows in the menu as you boot so that you can choose it.

to do this, do:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo vim /boot/grub/menu.lst

```
the first line creates a backup (just in case) and the second line opens up the file menu.lst in vim editor...if you're uncomfortable with vim, try "nano" instead.

n your menu.lst, towards the bottom,you should see a list of boot menu options. add this to that list: (i will assume you have windows on /dev/hda1...if your windows is not on the first partition, you will have to "map" the drive apparently...see [Install Windows XP on GRUB with Ubuntu already on it](http://ubuntuforums.org/showpost.php?p=683997&postcount=9))

```

title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

```


this part: (hd0,0) simply means the first first partition of the first disk.
the 3rd partition of the first disk would be (hd0,2)
the 5th partition of the second disk would be (hd1, 4)

if you'll notice the pattern, you have to start counting your partitions from zero.

now reboot your PC and try booting to windows, let me know if this doesn't work.
hope this helped.

---

### Post by BenWilson on 2006-02-01
[http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)

Dual boot without affecting the native MBR.

---

### Post by hen3rz on 2006-02-02
> [http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)

Dual boot without affecting the native MBR.

This howto presumes you already have windows installed.
> Your machine already has Windows installed, and you are installing Linux as a second operating system,

fatty is installing windows with linux already on it.

---

### Post by frodon on 2006-02-02
[QUOTE=fatty]I installed Ubuntu Gnome about a week ago and was and am very pleased with it.  But, because I still want to do some Windows applications I decided to set my computer up to dual-boot with Windows XP.  I made a partition for Windows and installed it fine.  I probably should have figured this would happen, but now I can only boot into Windows and can't access Ubuntu at all.  I did some research on how to dual-boot and it seems like Grub would do the job but I don't know how I could install it without Linux, and as it is, I can't even access my Ubuntu system.  Can someone please tell me how to set up dual-boot from Windows XP, or atleast get into my Ubuntu installation so I can set up dual-booting from there?[/QUOTE]You just need to re-install GRUB : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

