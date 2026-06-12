---
title: "Putting music on a partition"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by qalfazarath on 2007-10-24
I have a Dell Inspiron 6400 with 120 GB drive and I am using Ubuntu 7.10.

I have about 40 GB of music on my external, and I was wondering if I can make a partition on my  Ubuntu, place all my music files, and still be able to access them from Ubuntu. 
Is it possible, what programs do I need, and how would I do this?

Thanks

---

### Post by Ek0nomik on 2007-10-24
Definitely.

I'd suggest you backup any important data onto your external hard drive before you create the partition, just to be safe.

Once you've backed up your data (or just don't wish to -- more than likely nothing will happen, but just to be safe) you will want to fire up the Gnome Parition Editor.

You could do this with the Ubuntu Live CD (although I don't recommend it -- because your current partition will try to automatically mount, thus disallowing you from making changes to it), so I will suggest the GParted Live CD:  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn the CD, boot into the CD, select your video driver, and you will now see a familiar face.

You should see your internal hard drive (with an ext3 and linux-swap partition).  Now you will want to *shrink* your ext3 partition so you have room for your new music partition.  So, shrink your current ext3 partition to whatever size you wish.  Then, you will want to create a new parition in that newly freed space.  You can make it ext3 or fat32 if you wish.  I'd go with ext3 if Linux is going to be the only OS accessing this partition.

Hit 'Apply', and GParted will shrink your current ext3 partition, and create your new one.  Upon a reboot, you should see your newly created partition.

If you have questions, just ask.  :)

---

### Post by qalfazarath on 2007-10-24
Thanks for your input. 
However, I could not get it to work. I downloaded the file, burned the ISO, and restarted my computer. After I selected language, I got an error message:

"X.org: you need graphical environment to start GParted. The graphical environment configuration should have been done automatically. Unfortunately it did not, since you are back to bash!. So please run Forcevideo script"

I had problems with X.org before; I could not install Ubuntu 7.04 because of it.

Is there any other way to get around this?

---

