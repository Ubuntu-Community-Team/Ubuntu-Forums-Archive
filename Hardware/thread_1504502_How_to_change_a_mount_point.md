---
title: "How to change a mount point?"
date: 2010-06-08
forum: Hardware
---

### Post by iflanery on 2010-06-08
Hey, all.

I don't know if this has been addressed elsewhere, but I'm in kind of a unique situation.

Last night, I decided to do a clean install on my "/" partition. When the disk partitioning section came around, I was presented with the usual options of creating a new partition, installing onto an existing partition, or erasing the entire disk. I chose the second option, but chose not to set the mount point for my "/home" partition as "/home", as I feared this would force me to have to format that partition, causing me to lose all the data on it.

So, I chose not to.

This is where the problem comes in. Though Lucid installed successfully, my "/home" partition now shows up under the "/media" directory, under a long alpha-numeric string.

So, here's my question: is there any way to set that partition to mount at "/home" after the fact, or will I just have to do another clean install?

My system is a Dell Inspiron 530n with a 250GB HDD, 1GB of RAM, 1.3 GHz P4, and nVidia GeForce 8300GS.

---

### Post by GaryUK on 2010-06-09
Mounting is controlled by the fstab file  - please post contents of your /etc/fstab file.

---

### Post by iflanery on 2010-06-10
Very well. Here is how my /etc/fstab file looks:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on **/dev/sda3** during installation
UUID=e292a8f5-1baf-4447-b227-618aa49485eb /               ext3    errors=remount-ro 0       1
# swap was on **/dev/sda5** during installation
UUID=baa05a08-8479-403b-8774-333420bf53c8 none            swap    sw              0       0

Not listed is **/dev/sda1**, which is where my /home partition resides.

---

### Post by irv on 2010-06-10
> **iflanery said:**
> Very well. Here is how my /etc/fstab file looks:



Not listed is **/dev/sda1**, which is where my /home partition resides.

Maybe you can  try adding.
If you look at my screen shot I have my fstab file opened and gparted with the information displayed on my mount point showing my UUID number. If you find your mount point for your home directory and added it to this fstab it might mount. Before doing this I would read this blog:
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")
[ATTACH]159952[/ATTACH]

---

### Post by iflanery on 2010-06-10
> **irv said:**
> Maybe you can  try adding.
If you look at my screen shot I have my fstab file opened and gparted with the information displayed on my mount point showing my UUID number. If you find your mount point for your home directory and added it to this fstab it might mount. Before doing this I would read this blog:
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")
[ATTACH]159952[/ATTACH]

Here's the problem, though: /home is still in its own partition, but it doesn't mount automatically. And when it does mount, some applications (like Amarok) refuse to recognize it, claiming that "it does not exist."

What I'm trying to do is to get Ubuntu to automatically mount an *already existing* partition, not to create a new one.

---

### Post by irv on 2010-06-10
> **iflanery said:**
> Here's the problem, though: /home is still in its own partition, but it doesn't mount automatically. And when it does mount, some applications (like Amarok) refuse to recognize it, claiming that "it does not exist."

What I'm trying to do is to get Ubuntu to automatically mount an *already existing* partition, not to create a new one.

The point I was making is why don't you enter the /home in you fstab so it will mount when you boot up. As far as the apps that don't run just completely remove them with there directories and then re-install them. You may have to look for hidden directories with the "." before the name.

---

### Post by quadproc on 2010-06-10
> **iflanery said:**
> Here's the problem, though: /home is still in its own partition, but it doesn't mount automatically. And when it does mount, some applications (like Amarok) refuse to recognize it, claiming that "it does not exist."

What I'm trying to do is to get Ubuntu to automatically mount an *already existing* partition, not to create a new one.
I run a system where /home is on its own drive which auto mounts at boot time.  Here is the relevant part of my fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=df533fe8-68c3-41f6-b030-e955feb580d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b071f4d5-5384-4267-9f78-99e163d6ea4a none            swap    sw            0       0
#/dev/sdc1
UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home        ext3    relatime,errors=remount-ro    0    2
The relevant line is the last one.  Please note that it is assigned level 2; it won't be mounted until after the other file systems are mounted.  Also, please note that it is the filesystem (sdc[COLOR=Red]1[/COLOR] in my case) that is mounted, not the disk or a partition.

quadproc

---

### Post by iflanery on 2010-06-10
Looks like that just might work for me. I'll try it when I get back home from work tonight.

**UPDATE:** Well, quadproc's solution appears to have worked. Many thanks, though, for whomever had advice. :D

---

