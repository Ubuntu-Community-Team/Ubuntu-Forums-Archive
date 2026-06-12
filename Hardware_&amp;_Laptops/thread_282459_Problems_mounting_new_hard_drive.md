---
title: "Problems mounting new hard drive"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by juantovarm on 2006-10-22
Hello to all, I am a new user of Ubuntu. I have 2 hard disks installed in my pc, but only one works properly. After 3 days of repeating over and over again the instructions displayed on 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) ,  ubuntu finally mounted on boot my second disk. I have a new problem, now it only allows root to work on it. Here's my /etc/fstab entry
/dev/hdb1       /home/juan/hd2  ext3    user,rw,auto,sync,exec  0       0

once again i followed the instruction on that same page and on: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) , as adviced on the help.ubuntu page

any help will be appreciated

Thanx 
Juan

---

### Post by Jose Catre-Vandis on 2006-10-22
I have these settings in fstab for my 2nd (and 3rd) hard drives, works fine, every time...
```
/dev/hdc5   /media/apps  ext3  defaults  0  2
/dev/hdd5   /media/vids  ext3  defaults  0  2
```

Have you tried putting your mount into /media or /mnt? I think I read somewhere that mounts are "happier" in those locations, becuase the OS looks there for mounts?

---

### Post by DaveBorealis on 2006-10-22
> **juantovarm said:**
> Hello to all, I am a new user of Ubuntu. I have 2 hard disks installed in my pc, but only one works properly.

How exactly don't they work properly? 

>  Here's my /etc/fstab entry
/dev/hdb1       /home/juan/hd2  ext3    user,rw,auto,sync,exec  0       0


My own /etc/fstab for a second hard drive:
/dev/hdb1       /home           ext3    defaults        0       2

Have you tried that particular entry?

Best regards,
Dave

---

### Post by juantovarm on 2006-10-22
Following both of your comments I just changed my /etc/fstab:

/dev/hdb1       /media/hdb1     ext3    defaults        0       2

it tells me that i don't have permission to write in there.

I also had:

/dev/hdb1     /media/hdb1   etc3   rw,auto,user,sync,exec   0   0

same problem, no permission to write in there.

---

### Post by Spano on 2006-10-22
> same problem, no [COLOR="Red"]permission[/COLOR] to write in there.
Both fstab lines are fine. I believe you need to change ownership of the file.  Try this in terminal  
```
sudo chown juan /media/hdb1
```
should get you going.
Here is a link to instructions for using the chown command:
[http://wiki.linuxquestions.org/wiki/Chown](http://wiki.linuxquestions.org/wiki/Chown)

You can right click the file to check ownership and permissions.
Hope this helps.

---

### Post by juantovarm on 2006-10-23
Thank you all!
Chown did it!


juan

---

### Post by Jose Catre-Vandis on 2006-10-25
> **juantovarm said:**
> Following both of your comments I just changed my /etc/fstab:

/dev/hdb1       /media/hdb1     ext3    defaults        0       2

it tells me that i don't have permission to write in there.

I also had:

/dev/hdb1     /media/hdb1   etc3   rw,auto,user,sync,exec   0   0

same problem, no permission to write in there.

Rather than change the permissions to the fstab file, you should use sudo to edit it:
```
 sudo gedit /etc/fstab
```
(then enter password, then edit file, save, and the fstab file is safe from harm)

If you are new to things, it may be useful to back up your fstab before you edit it:
```
sudo cp /etc/fstab /etc/fstab.backup
```

---

