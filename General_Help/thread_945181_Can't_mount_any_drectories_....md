---
title: "Can't mount any drectories ..."
date: 2008-10-12
forum: General Help
---

### Post by ashkev on 2008-10-12
At some point some time ago, I lost the ability to mount any directories in Gnome.  

I installed KDE and everything looks ok there... I can navigate to my home directory etc, but in Gnome, when I click on Places then anyplace.... nothing happens.

If I try to mount a directory I get this:```
kevin@kevin-desktop:~$ pwd
/home/kevin
kevin@kevin-desktop:~$ mount /home/kevin
mount: can't find /home/kevin in /etc/fstab or /etc/mtab
kevin@kevin-desktop:~$ sudo mount /home/kevin
[sudo] password for kevin: 
mount: can't find /home/kevin in /etc/fstab or /etc/mtab
kevin@kevin-desktop:~$ 


```

Any Idea how yo fix this?

---

### Post by ajmorris on 2008-10-12
> **ashkev said:**
> At some point some time ago, I lost the ability to mount any directories in Gnome.  

I installed KDE and everything looks ok there... I can navigate to my home directory etc, but in Gnome, when I click on Places then anyplace.... nothing happens.

If I try to mount a directory I get this:```
kevin@kevin-desktop:~$ pwd
/home/kevin
kevin@kevin-desktop:~$ mount /home/kevin
mount: can't find /home/kevin in /etc/fstab or /etc/mtab
kevin@kevin-desktop:~$ sudo mount /home/kevin
[sudo] password for kevin: 
mount: can't find /home/kevin in /etc/fstab or /etc/mtab
kevin@kevin-desktop:~$ 


```Any Idea how yo fix this?

hi there,
not sure about your GUI 'places' in the gnome menus,
however, for your mount commands, if you have not added an entry to /etc/fstab for your physical device (in /dev) or the mount point (e.g. /home/kevin), then you need to specifiy a block device also, i.e. ```
mount /dev/sda1 /home/kevin
```
you can find the block devices that belong to partitions with the ```
fdisk -l command
```
and you can find your root partition, and other auto-mounted partitions in /etc/fstab.

AJ

---

### Post by ashkev on 2008-10-12
> **ajmorris said:**
> hi there,
not sure about your GUI 'places' in the gnome menus,
however, for your mount commands, if you have not added an entry to /etc/fstab for your physical device (in /dev) or the mount point (e.g. /home/kevin), then you need to specifiy a block device also, i.e. 
you can find the block devices that belong to partitions with the ```
fdisk -l command
```
and you can find your root partition, and other auto-mounted partitions in /etc/fstab.

AJ

OK, so when i tried ```
mount /dev/sda1 /home/kevin
``` an icon appeared in the control panel at the top of the desktop.  It was an unkown icon, just a square box.  When I click on it, it acts as though something is happening but nothing opens.

Also when this all began, I also noticed that all of the icons and shortcuts on my Desktop are gone.

I have tried removing and reinstalling gnome-desktop, but this has not helped anything.

Thanks

---

### Post by bodhi.zazen on 2008-10-12
usually you mount a partition in /media or in a dirictory within your home directory such as /home/kevin/data

I think a part of your problem is your mount point.

See this link:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you are trying set up a separate home partition see this one :

_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_

---

### Post by ajmorris on 2008-10-12
as well as taking a look at the above links, bodhi posted, if you would like some help with your partitions, could you please post the output of ```
sudo fdisk -l
```  Running the command 'sudo mount /dev/sda1 /home/kevin' was just an example, i doubt sda1 is your home partition.

AJ

---

