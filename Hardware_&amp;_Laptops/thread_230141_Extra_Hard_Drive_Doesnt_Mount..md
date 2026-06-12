---
title: "Extra Hard Drive Doesnt Mount."
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by khughes on 2006-08-05
I hope someone can help me because I have no idea whats going on here.

I have a Dell Poweredge SC430 server that I have dapper installed on. I operates off of a SATA drive listed as /dev/sda. I installed a pci ide controller to add an additional drive which shows up as /dev/hda. What I am trying to do is have this drive mounted permanently.

The problem is that I cant mount it at all. If I go into System>Administration>Disks, it shows me a Hard Disk 232.89 GB. It tells me it is formatted with ext3 and its access path is /media/storage. It also tells me it is inaccessable and if I click enable it just flashes but nothing changes. Then if I go to Places>Computer, I have 2 cdroms, a filesystem icon, and an icon for that drive saying 232.9 GB Volume. If I double click on it there, I get an error saying:

error: device /dev/hda1 is not removable

error: could not execute pmount

I had dapper on this once before and the hardware setup was the same and everything worked without any additional configuration so I dont know what happened here. If anyone could help it would be great.

---

### Post by adhuvi on 2006-08-06
Hi, I have the same problem, except that i don't want to format the hd but to acces the info i have there. 
Hope someone can answer this one.

---

### Post by adhuvi on 2006-08-06
A friend of mine helped me in this one. 

sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1

worked for me.

---

### Post by khughes on 2006-08-06
Well, that seemed to do it. Thanks alot. I dont know why I never thought about mounting the drive before. Now the only thing I need to figure out is how to get this into my /etc/fstab correctly so it will automount every time. I read the man page on fstab but after editing it and rebooting, I locked up on boot. I had to boot from a livecd to change the file back. Anyone have any suggestions?

---

### Post by adhuvi on 2006-08-08
Solved it already? I added at the end (the order is importante if i underestood well) of my /etc/fstab file something like:

/dev/hda1	/media/hda1	ext3	defaults	0	0

hope it helps.

---

### Post by khughes on 2006-08-08
> **adhuvi said:**
> Solved it already? I added at the end (the order is importante if i underestood well) of my /etc/fstab file something like:

/dev/hda1	/media/hda1	ext3	defaults	0	0

hope it helps.

Yeah, I just kind of looked at the other entries in there and read the man page for fstab and figured it out. Now my problem is that the hard drive, now permanently mounted, shows up on my desktop all the time. I want volumes like usb drives and cd's to show up on the desktop, but not that permanent drive. Do you know how to fix that?

---

### Post by pyman on 2006-08-09
This worked for me...
have a look at your fstab file.
sudo gedit /etc/fstab
see if your /dev/hd?x has **noauto **in the mounting syntax
if it does change it to **auto **and that will automatically mount on bootup
be sure to backup the /etc/fstab file first :-P

---

### Post by BRD on 2006-08-09
I have this problem to but it wont let me edit it

---

### Post by khughes on 2006-08-10
> **BRD said:**
> I have this problem to but it wont let me edit it

You have to have root priveledges.

```
sudo gedit /etc/fstab
```

Then you should be able to edit it.

---

### Post by adhuvi on 2006-08-10
I don't know how to make it disapear from my desktop. already tried to mount it in a diferent folder. Any ideas?

---

### Post by khughes on 2006-08-10
All I did was mount it to a folder in /mnt instead of /media. I still mounts, but doesnt show up on the desktop.

---

### Post by adhuvi on 2006-08-11
Didn't work for me, if I mount on /mnt It appears on my desktop like: /mnt/hdxx

---

### Post by Torstein_V on 2006-08-24
I had the exact problem described from the thread's starter, and I successfully mounted my hdb5 with ext3 on my desktop. I also edited the /etc/fstab. But despite of all this, it wouldn't let me write to the disk.

So I **chmod 777 /media/hdb5** the whole volume. 

So, now I'm able to write to it again, but is this chmod step really necessary?

The disk has also an unreadable directory called "lost+found". Can someone be so kind and explain me what this directory is for, and if I can delete it?

---

