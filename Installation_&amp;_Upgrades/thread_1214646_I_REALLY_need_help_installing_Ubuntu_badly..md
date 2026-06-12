---
title: "I REALLY need help installing Ubuntu badly."
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Chaos Punk on 2009-07-16
I have a laptop that just happens to not have any way of booting CD's since it has a floppy drive instead. I have been racking my brain for days trying to figure out how to get Ubuntu onto it. I have managed to get Debian on it, but I want Ubuntu. The method I used to get Debian onto it was through booting from floppies that loaded the installer program and network drivers, then it proceeded to do an internet install. Basically, it was the equivalent of Ubuntu's Minimal CD, only on floppies. So that got me wandering, is there a way to make minimal boot FLOPPIES instead of the CD for Ubuntu? I know I could just put the harddrive in another PC and install, or find a CD drive for my laptop, but that's absolutely last resort. Yes I'm sure it can run Ubuntu and no, it's not an old computer, I think it's from 2004. Any other suggestions are welcome, but let me run down what I KNOW will not work.
1. Can't boot CD's, no CD drive.
2. BIOS can't boot from USB, neither will Smart Boot Manager.
3. DHCP local network installs haven't worked, I have no clue what I'm supposed to put in the fields regarding my IPs and router stuff. For some reason my ISP never told me.:confused:

Some more info that might help the solution.
1. I have multiple USB drives, so if someone can maybe help me find a way to boot from that, I'd be very appreciative.
2. I have an external CD drive, but it connects via USB.:(
3. I successfuly installed Debian via the Debian Sarge installer, if there is a simialar way to do this for Ubuntu, please let me know.
4.

---

### Post by sisco311 on 2009-07-16
[https://help.ubuntu.com/community/Installation#Installation without a CD]("https://help.ubuntu.com/community/Installation#Installation without a CD")

I would go with a hd install.

[list=i]
[*] download the alternate iso


[*] download *vmlinuz and initrd.gz* from [http://archive.ubuntu.com/]("http://archive.ubuntu.com/")

i.e. for ubuntu 9.04 Jaunty Jackalope i386 from: [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/")  


[*] create a small (800MB-1GB) ext3 partition and put these files(the iso image, vmlinuz and initrd.gz) in your newly created partition. 

NOTE: grub should recognize your usb drives, so you can create the ext3 partition on the usb drive.


[*] edit your grub menu:
```
su -c "nano /boot/grub/menu.lst"
```
and add a new entry by adding this lines to boot from the new partition:
```
title           installer
root            (hd0,0)
kernel          /vmlinuz root=/dev/ram ramdisk_size=1048576 rw
initrd          /initrd.gz 

```

where *(hd0,0)* denotes the partition.

(hd0,0) = first disk, first partition
(hd0,1) = first disk, second partition
...
(hd1,0) = second disk, first partition (assuming that you have only one disk in the laptop this should be the first partition on the external drive)
...

save the file and exit (Ctrl+x, y, Enter).


[*] reboot the computer and select the *installer* entry form the grub menu[/list]

---

### Post by snowpine on 2009-07-16
^--- sisco311 has great advice.

If you want to automate the process, check out Unetbootin, it is really easy to use:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Or you could just stick with Debian, it is a great distro. :)

---

### Post by Chaos Punk on 2009-07-16
> **sisco311 said:**
> [https://help.ubuntu.com/community/Installation#Installation without a CD]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD")

I would go with a hd install.

[LIST=i]
[*] download the alternate iso
[*] download *vmlinuz and initrd.gz* from [http://archive.ubuntu.com/](http://archive.ubuntu.com/)

i.e. for ubuntu 9.04 Jaunty Jackalope i386 from: [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/)
[*] create a small (800MB-1GB) ext3 partition and put these files(the iso image, vmlinuz and initrd.gz) in your newly created partition. 

NOTE: grub should recognize your usb drives, so you can create the ext3 partition on the usb drive.
[*] edit your grub menu:
```
su -c "nano /boot/grub/menu.lst"
```and add a new entry by adding this lines to boot from the new partition:
```
title           installer
root            (hd0,0)
kernel          /vmlinuz root=/dev/ram ramdisk_size=1048576 rw
initrd          /initrd.gz 

```where *(hd0,0)* denotes the partition.

(hd0,0) = first disk, first partition
(hd0,1) = first disk, second partition
...
(hd1,0) = second disk, first partition (assuming that you have only one disk in the laptop this should be the first partition on the external drive)
...

save the file and exit (Ctrl+x, y, Enter).
[*] reboot the computer and select the *installer* entry form the grub menu
[/LIST]

Ok, this I'll try, I'm a little fuzzy on some things though. Oh, and I'd prefer instructions on how to do these things in Windows since I'm running that right now cuz my ubuntu parition is screwing up.

---

