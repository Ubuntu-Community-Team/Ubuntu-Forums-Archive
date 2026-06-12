---
title: "Kubuntu not in boot menu"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by ckmccoy on 2009-09-28
I've been using ubuntu for almost a year, and i have been liking it very much.  I have one hard drive with ubuntu, and one hard drive with vista on it, which i installed kubuntu on a partition on the vista hard drive.  When I restarted, my boot menu only shows ubuntu and windows vista (loader) and no kubuntu.  I'm very lost as to what my problem is here? helpppppppp please!

---

### Post by rreese6 on 2009-09-29
Kubuntu need to be added to the Grub menu..
Download the script in my Signature called BootScript
and run it.```
cd <to where you downloaded script file>
sudo ./boot_info_script032.sh
```

Then post the contents of the Readme.txt file produced by the script here.

---

### Post by slakkie on 2009-09-29
You don't need a separate install for Kubuntu..
In ubuntu, install the kubuntu-desktop package:

sudo aptitude install kubuntu-desktop

logout, and hit session type and select kde. Voila.

---

### Post by rreese6 on 2009-09-29
True, but maybe he wants to run the 3.5 desktop of Kubuntu 8.04LTS...

---

### Post by slakkie on 2009-09-29
8.04 doesn't have KDE4.x desktop last time I checked..

---

### Post by rreese6 on 2009-09-29
My point  exactly :)

---

### Post by Merlion on 2009-09-29
There are ISO-images with KDE4 at here: [http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/](http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/)
If I remember good, there was in Hardy KDE4, I installed it, but it was very-very early to use:D

I use Kubuntu since Gutsy released. If you install it on the entire disk (no other operating system), in the Grub there won't be Kubuntu: only Ubuntu (however it is Kubuntu).

---

### Post by ckmccoy on 2009-09-29
> **slakkie said:**
> You don't need a separate install for Kubuntu..
In ubuntu, install the kubuntu-desktop package:

sudo aptitude install kubuntu-desktop

logout, and hit session type and select kde. Voila.


i've decided to do this, so i can save my other hard drive for windows completely and keep U/K on their on hard drive. how do i get rid of the partition i made on my windows hard drive, and turn it back to its full 500GB???

---

### Post by rreese6 on 2009-09-29
Run gparted on the drive, delete the linux partition and resize the windows one. it will take a while to complete so be patent.
Remember with gparted after you do the delete and resize, hit the apply button and wait for it to finish.

---

### Post by ckmccoy on 2009-09-29
while in gparted, the lunux partition has locks next to it, and it won't let me remove delete, or, as far as i can tell, do anything to that partition. how do i get rid of the little lock symbol next to the partition?

---

### Post by Bucky Ball on 2009-09-29
> **ckmccoy said:**
> i've decided to do this, so i can save my other hard drive for windows completely and keep U/K on their on hard drive. how do i get rid of the partition i made on my windows hard drive, and turn it back to its full 500GB???

It is best. You can install Xfce also and a bunch of other desktop environments. Just go to 'Sessions' at the login screen and choose KDE or Openbox or Xfce ... whatever you feel like.

---

### Post by ckmccoy on 2009-09-29
scratch that last post. i learned i had to unmound the drive first. which removed the lock. i deleted the linux partition and now i have a 300.06 partition which is my windows, and an unallocated 165.69GB partition.  The resize option is grayed out and I can not figure out why.

---

### Post by oboedad55 on 2009-09-29
> **ckmccoy said:**
> scratch that last post. i learned i had to unmound the drive first. which removed the lock. i deleted the linux partition and now i have a 300.06 partition which is my windows, and an unallocated 165.69GB partition.  The resize option is grayed out and I can not figure out why.

At this point it sounds like a question for windows forums. Maybe you can get Partition Magic or Acronis Disk Director.

---

### Post by rreese6 on 2009-09-29
This might be because you dont have the right drivers installed to modify NTFS file systems.
I like to use a CD just for system rescue. It has all the programs needed to read and write NTFS and also a graphical gparted.
the welcome screens explains this.

it is called System Rescue CD and you can find it here:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

I have used their CD for years to fix systems and resize windows partitions.

---

### Post by ckmccoy on 2009-09-30
yup! all i had to do was boot back into windows, and extend my partition over the blank one.  thanks for ya help!

---

### Post by rreese6 on 2009-09-30
SO if that is done, Mark the post as SOLVED

---

