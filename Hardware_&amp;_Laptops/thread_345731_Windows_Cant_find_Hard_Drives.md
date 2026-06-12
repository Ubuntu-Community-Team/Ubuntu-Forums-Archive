---
title: "Windows Cant find Hard Drives"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Frazer on 2007-01-24
I am having a problem with installing windows xp home on my Laptop, hp nc8430.

The windows 'recovery' partition (they did this instead of giving me a windows install cd, it installs a fresh copy of windows without giving any options) that came on my laptop decided one day to just 'recover' randomly.  I was running the laptop triple boot with Ubuntu, MAC OSX and Windows Home.

I turned the laptop on and went to get a cup of tea, thinking it would boot straight to Ubuntu like normal.  The windows recovery started while I was away.

The first partition was 7 gb for OSX and the widows recovery decided to just erase it and replace it with windows (diddnt even warn or ask :@ or even let me choose a partition, just attacked the first one)

I came back just as it was finishing, very annoyed too.
 
The windows install booted fine and all of my other partitions were still there.

Obviously windows decided to get rid of grub so I decided to stick my Ubuntu Live cd and fix it.

Once it had booted I decided I may as well use gparted to kill off the recovery partition and stop this happening again.  I decided because I had lost OSX anyway and everything else was backed up id just format and start it all again.

I got rid of everything and installed Ubuntu leaving some space for windows later.

When I came to install windows a week later (I need it for some software for my final year project at uni) It says It cant find a hard disk.

I am using a windows home cd I copied of someone and was going to use the cd key printed underneath my laptop.

I have tried a few times and cant seem to see a problem.  Could this be to do with deleting the recover partition?

Has anyone got any sugestions on how to fix this, because im stuck.

---

### Post by linuchsan on 2007-01-24
Can you show us, your partition table?

---

### Post by teitunge on 2007-01-24
yes, do as linuchsan suggested.

sudo fdisk -l (this is an L) in the terminal.
then paste the answer you get.

---

### Post by Frazer on 2007-01-25
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 


I just did a format using my bios disk sanitation utility, i diddnt help :@

All I can say is bleh stupid windows and thanks for trying to help me :)

---

### Post by Nik_Doof on 2007-01-25
> **Frazer said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 


I just did a format using my bios disk sanitation utility, i diddnt help :@


Yup, that formatted your drive alright... I guess the disk sanitation is equiv of the secure format / low level format.

---

### Post by Frazer on 2007-01-25
could it be a driver problem with with windows not finding the hd?

This is how i would like my system (just partitioned while installing ubuntu)

Im going to query the hp website, see if they have anything I can use, but at the moment im still totally stuck.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        2805     7173022+  83  Linux
/dev/sda3            2806        5354    20474842+  83  Linux
/dev/sda4            5355       12161    54677227+   5  Extended
/dev/sda5            5355        5627     2192841   82  Linux swap / Solaris
/dev/sda6            5628       12161    52484323+  83  Linux

1 windows xp (only for 2 programs and eve online)
2 OSX
3 Ubuntu root
5 SWAP
6 Home (going to be shared with windows, I have a driver to read)

---

### Post by Frazer on 2007-01-25
I think I have found a way to fix it, I slipstreamed my windows xp cd along with the SATA drivers.  Lets hope it works :) just going to try it now.

[http://www.nliteos.com/]("http://www.nliteos.com/")

This thing lets you mess with the windows install files and create an iso (work from inside windows though :( )

I have added my drivers to it and deleted a lot of the crap.

I cant wait till I can just forget about windows now.  As soon as my project is finished ill just be pure Linux, Im so fed up of windows related problems, I can even live without playing eve online and ill start UT or somthing.

---

