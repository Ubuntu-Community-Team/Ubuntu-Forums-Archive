---
title: "Change to a Larger Hard Drive"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by CHFFriday on 2007-08-14
Ok everyone it’s time to teach me some things about Linux hard drive partitioning.
I have an 8 gig hard drive and on it I have install Ubuntu. Everything is working Great!

I decided I would upgrade to a new Bigger hard drive. So I used a drive copy program (Acronis)to clone the old to the new. During the operation I got a warning about the Linux file system boot loader and some hints on how to fix it after the cloning operation was completed. This program was set to expand the partitions to reflect the original ratio. All went fine!

Put the new hard drive in the PC thinking that I would not be able to boot BUT to my surprise I was able to boot!! Happy Days. 

Check the drive size and found my EXT3 Partition drive was the same size and the swap file was increased to a size that used the rest of the disk space.

I thought NO problem! I will resize all the partitions the way I want them to be but I could only resize the swap partition. I can not resize the EXT3partition. Who needs a 46 gig swap partition?

What can I do to get this back to the right ratio? Also give me some pointers on Linux Partitions.

CHFFriday

---

### Post by matburton on 2007-08-14
How are you trying to resize the partitions? Using gparted on the Live CD?
What is the error you get when you try to resize the ext3 partition?

---

### Post by CHFFriday on 2007-08-14
matburton,
I use Acronis.

First I resized the swap to 960 mb. That gave 46 gigs of unallacated space. I then tried to resize to ext3 partition but it just would not do anything no matter how hard I tried.

CHFFriday

---

### Post by merlinus on 2007-08-14
gparted live cd may work:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by matburton on 2007-08-14
Sounds like Acronis (I'm not familiar with it) can't resize ext3.

Like merlinus says I'd use either the gparted live cd or the ubuntu edgy live cd and start gparted from there.
(Edgy because feisty seems to have a few problems with partitioning from the live cd, it automounts stuff at dangerous times and the drives should not be mounted during partition alterations)

Hope that helps!

---

### Post by CHFFriday on 2007-08-14
Sorry I have not got back to everyone. Will try as recommended.

CHFriday

---

### Post by CHFFriday on 2007-08-14
No GO! Using gpartitioner I still can not increase the size of the ext3 partition. I can do what ever I want to do to the swap partition but No Go to the ext3 partition.

There must be something I don't understand about Linux partitions or I'm doing something incorrectly.:confused: 

Can  anyone help?

CHFFriday

---

### Post by ramjet_1953 on 2007-08-15
Ghost for Linux will make a perfect 1:1 clone of your HDD.

It is an iso file that you burn to a CD and then boot from it.

You just choose the local clone option.

You can get the G4L iso from here: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

After that just use the gPartEd LiveCD to expand your partitions.

Regards,
Roger :cool:

---

### Post by CHFFriday on 2007-08-15
Ramjet_1953,
Thanks for the get-back.

I will try your suggestion but what I have been reading on the Net about this procedure has caused some confusion.

Here is the jest of it. It seams that you do some sort of copying of the contents of the ext3 file to an ext3 partition no the new drive. Then expand it. Then fix Grub.

This is the year 2007. This sounds like stuff we used to do in the old DOS days. It seams to me that there should be a program that would make this project work just as if you where doing a Windows disks upgrade. No mess. No fuss.

What do you think or for that matter what does anybody think? Or I’m I going down the wrong path here?

Linux and Ubuntu have become an obsession with me. I have learned allot but this has really got to me.

CHFFriday

---

### Post by CHFFriday on 2007-08-15
Thanks to everyone for the help.
I used a deferent version of Acronis and re-cloned the drive. This time it worked. :)

CHFFriday

---

