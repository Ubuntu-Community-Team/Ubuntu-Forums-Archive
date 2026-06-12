---
title: "Updated menu.lst does not work. Can't boot to new kernel."
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by JacobSteelsmith on 2009-01-29
I had posted this in [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009) but was told the forum would be a better place. I am running Kubuntu 8.10 and recently upgraded to KDE 4.2. 

I had been affected by a bug and had removed the splash option from /boot/grub/menu.lst for the 2.6.27-9 kernel. There was a recent upgrade to 2.6.27-11. When I installed this upgrade, it said the maintainers version of menu.lst was different than the installed version. Knowing what I had done, I choose to install the maintainers version. 

When I rebooted, the menu options had not changed (after hitting esc to view the grub boot options) and the new kernel was not there, even though /boot/grub/menu.lst does show the updated listings. In fact, the splash option is there for 2.6.27-9 in menu.lst, but during boot, there is no splash. Basically, the menu at boot time does not reflect what is in /boot/grub/menu.lst

I then removed linux-image-2.6.24-22-generic and got the same prompt about menu.lst. I chose to keep the maintainers version. I rebooted with the same results, and 2.6.24-22 was still in the boot menu. In fact, I was able to boot to the 2.6.24-22 kernel even though I removed the image, although the nvidia kernel module had been removed so I had problems booting into X, although I did confirm the kernel version by booting to a root shell.

I run software raid using mdadm and the array is in good condition. I do not have a separate boot partition. I have 3 identical disks with two partitions each. Two of the disks are part of a raid 1 array and the third disk is a spare. One partition is root and one is swap. 

I attached some files. If anyone needs to see anything else, let me know. Thanks in advance for the assistance.

---

### Post by JacobSteelsmith on 2009-01-29
My buddy Alex helped me fix this. I had to use Grub to write the new /boot/grub/menu.lst to the MBR.

So:

First, get into grub

jacob@jakes-desktop:~$ grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

Now look for menu.lst

grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
 (hd0,0)
 (hd1,0)
 (hd2,0)


Make sure the menu.lst is the one you want.

grub> cat (hd0,0)/boot/grub/menu.lst                       
cat (hd0,0)/boot/grub/menu.lst                             
# menu.lst - See: grub(8), info grub, update-grub(8)       
#            grub-install(8), grub-floppy(8),              
#            grub-md5-crypt, /usr/share/doc/grub           
#            and /usr/share/doc/grub-doc/.
...


Make sure stage1 is on the same partition you're going to use

### END DEBIAN AUTOMAGIC KERNELS LIST
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd2,0)
grub> root (hd0,0)

grub> setup (hd0)

I rebooted and it works fine. Thanks!

---

