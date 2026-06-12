---
title: "Kernel update reassigning boot partition??"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by citronmg on 2006-01-19
Every time I have updated the Ubuntu kernal with the autoupdate it changes my /boot/grub/menu.lst file so that it will not reboot because it changes the root line from:   '(hd0,1)' to '(hd0,2)' 
and the kernal line from:   '...root=/dev/hda2'    to   '...root=/dev/hda3'  

The first time it happened it failed to boot but I found the problem.  I've since changed the menu.lst file back before restarting after a kernal update so that it will boot.  My partitions are 0-Windows, 1-Ubuntu, 2-Swap, 3-Data.  If anyone know's why this is happening let me know. Thanks.


/boot/grub/menu.lst  after updating kernel >>

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,**2**) 
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda**3** ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,**2**)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda**3** ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

---

### Post by lha on 2006-01-19
For some reason, your /boot/grub/menu.lst is misconfigured. First, make a backup of it and open it in gedit.
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

Find line
```
# kopt=root=/dev/hda3 ro
```
and change it to
```
# kopt=root=/dev/hda2 ro
```
Then find line
```
# groot=(hd0,2)
```
and change it to
```
# groot=(hd0,1)
```.

Whenever a new kernel is installed, a program called update-grub
 is run. It removes every entry between lines
```
### BEGIN AUTOMAGIC KERNELS LIST
``` and
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Then it creates new entries based on kernels you have on your hd and those two options we altered before. All manually added menu entries should be outside of those "### BEGIN" and "### END" lines to survive a kernel upgrade.

---

### Post by anaconda on 2006-06-20
WOw.

Thanks. this was really helpful. Now I understand why update screws my grub installation. It thinks mixes the primary disk with the secondary hd..

---

### Post by mellowb on 2007-06-04
It was very useful for me too! I started getting the same problem after moving my partitions around while resizing them. 

However, since Ubuntu is now using UUID, the kopt and  line now reads like

# kopt=root=UUID=0a1764e6-36ed-4c6b-975a-e32190475132 ro

where the UUID number above may be discovered with the command

sudo vol_id -u /dev/sda2

---

