---
title: "Proper fstab code"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Rhemat on 2006-08-29
I recently installed the newest Ubuntu on my 10.1gb hard drive, and have my 72.8gb (though the sys detects it as 80gb) set as slave.  I found out, though, that because I left my old Ubuntu install there, I have to change fstab.  I found the file, and I see that /dev/hdd1 isn't listed there.  I just want to be certain that I list it as /dev/hdd1, and what parameters I give it for [type] [options] [dump] and [pass].

Thank you for your help

-Rhemat

---

### Post by meng on 2006-08-29
If it's ext3, then the following options should work
ext3  default  0  2

---

### Post by Rhemat on 2006-08-29
I followed those parameters, and put the mount point at /.  I got this error message

mount: according to mtab, /dev/hda1 is already mounted on /

mount failed

-Rhemat

---

### Post by meng on 2006-08-29
Are you trying to mount TWO devices to the same place? You can't do this. Pick another folder.

---

### Post by Rhemat on 2006-08-29
Okay, I have access.  I just need to clean up the remnants of the old system now.  Thank you.

-Rhemat

---

### Post by Rhemat on 2006-09-07
I recently had to (once again) reinstall Ubuntu.  I've followed the same steps to make the drive user mountable, and it just tells me that only root can mount it.  I've chowned the drive, the folder I put the mount in, changed fstab the way you mentioned before, but it just tells me, that nothing is in it, and only root can mount it.

-Rhemat

---

### Post by dannyboy79 on 2006-09-08
please post the results of this command below:
sudo fdisk -l
and also please copy and paste what is inside of your /etc/fstab file. I will try to help you once you post this info for me. Can't help you otherwise though.

---

### Post by Rhemat on 2006-09-08
I hate to say this, but I decided to just toss the old master, and just use the larger drive as master.  Sorry.

-Rhemat

---

### Post by dannyboy79 on 2006-09-08
so you are saying that you don't want to be able to get your config files, your contents from your /home/username folder and such from your old ubuntu install that's on that smaller hd before you wipe it clean and use it as a spare hard drive? If not than ok but if you do want to get some stuff off if it, just post what I asked and I will be happy to help you.

---

### Post by Rhemat on 2006-09-08
All the files I wanted to access, were on the larger drive, the one that has been formatted and become master.  The only thing that was on the small drive, was the installation, and I accidentally dropped the smaller drive.
I'm sorry I didn't keep this thread up to date, but I'm a scatter brain.

-Rhemat

---

