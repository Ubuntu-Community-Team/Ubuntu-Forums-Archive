---
title: "Vista Dual boot with ubuntu"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by fergie7 on 2009-10-20
I have vista home premium

1st i dont want anything lost on vista if possible.

i have downloaded and burned ubuntu 9.04
wondering if i do the installer does it install ubuntu already??
tried that serval times and i get an error saying "no permitinon"

i want the full OS of ubuntu and want to have a dual boot or a way i can acess both OS.

---

### Post by stlsaint on 2009-10-20
> wondering if i do the installer does it install ubuntu already??
tried that serval times and i get an error saying "no permitinon"

does this mean that you are getting an error when trying to use the livecd? if so please post the entire error you are getting so we can assist and if you want access to both os than yes you are looking for a dual boot setup.
please see my signature for reference.

---

### Post by bondmatt on 2009-10-20
You have a couple of options: virtual machine in Windows (Windows program allows you to run Linux) or you can install in a separate partition on your hard drive as a second operating system. I am not an expert on these matters so there may even be other options. I have separate partitions and am very happy. One reason: Vista uses about 2GB RAM (some of that is most likely 3rd party anti-virus, HP drivers, etc - I have an HP laptop) whereas Ubuntu uses about 300 MB. The boot up time is night and day (molasses vs. speedy gonzales).

I used disk manager in Vista to shrink the Windows partition then used the installer on the live DVD to create a linux partition and install. Here is a link to the resources I used:

[http://caelinux.com/CMS/index.php?option=com_joomlaboard&Itemid=52&func=view&id=3096&catid=3](http://caelinux.com/CMS/index.php?option=com_joomlaboard&Itemid=52&func=view&id=3096&catid=3)

CAELinux is currently Ubuntu based with lots of open source engineering software installed and pre-configured. In terms of installation I dont think it is any different from stock Ubuntu (probably takes longer).

Good luck

---

### Post by Niko Johnson on 2009-10-20
setting up a dual boot enviroment is pretty easy. first you need to make a partition for ubuntu. in vista go to the disk management under administrative tools. then click on storage > disk management. when you get the screen you right click on you vista partition and choose shrink volume. after you shrunk it you will get a new partition on you disk labeled unallicted space. (then defrag is optional but recommended) after all that pop in your live cd and click install. go through the installation until you get to the disk partitioner. make sure you click on set up partitions manually, or it will wipe out your whole disk! when you get to the partition table click on your new free space parition then click on new table (or new patition i forget what is says) and make a 2 gig swap partition first ( you can have as much swap as you want but 2-4 is more than enough) after that is made go back to the free space and make a new parition. this time make it maximum size and use the ext3 filesystem ( you can use whatever filesystem you want but i use ext3 with no problems) and mount it on /. accept you changes and make sure you have swap and a mounted file system. then you are good to go, go with the rest of the installation and grub is load during the boot proccess from now on asking you if you would like to boot from windows or ubuntu...hence Dual Boot

---

### Post by Bartender on 2009-10-21
> **fergie7 said:**
> 1st i dont want anything lost on vista if possible.

None of us can offer you a guarantee.  You have to back up important personal data.  Have you made recovery discs, or did your PC come with them?

---

### Post by Mark Phelps on 2009-10-21
> **fergie7 said:**
> ... 1st i dont want anything lost on vista if possible...

That being the case, follow Bartender's advice and backup important data.

If you don't have a Vista DVD (install DVD, not recovery/restore disk that came with a PC), go to the NeoSmart Technology forums, look for their Vista Recovery CD, download and burn it to CD.  You will now have a CD to use to repair Vista boot problems -- should they happen.

Last, and MOST IMPORTANT, follow the advice several folks have given you about using the Vista Disk Management utility to shrink the OS. Do NOT use GParted or the Ubuntu installer to do this.  There are reasons why the Vista tool limits shrinkage of its partition -- to prevent damage.  Using other tools that ignore those problems is likely to result in damage to the Vista OS partition.

---

