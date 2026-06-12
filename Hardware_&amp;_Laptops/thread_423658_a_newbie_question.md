---
title: "a newbie question"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by red777 on 2007-04-26
How can I get ubuntu to keep my 2nd slave drive mounted & recognized?For some reason it keeps un mounting on shut down,when I restart it's gone & I can't see or use it.Your advice is needed.

---

### Post by Zuph on 2007-04-26
Does the drive show up in your /etc/fstab file?

---

### Post by red777 on 2007-04-26
sorry, I'm to new at this to know how to find that sort of information,if someone can step me thru it I'll post here.

---

### Post by ubuntu27 on 2007-04-26
> **red777 said:**
> sorry, I'm to new at this to know how to find that sort of information,if someone can step me thru it I'll post here.


> **Zuph said:**
> Does the drive show up in your /etc/fstab file?



Open the terminal (Applications Menu/Accessories/Terminal)

and type ```
gedit /etc/fstab
```

A new window which is a text editor will open. There, find whatever your drive is listed.

Better Copy and Paste your contents here.

---

### Post by red777 on 2007-04-27
ok I hope this is what you want# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=20ea49ce-a892-42f2-921f-bbacbbb18cfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=181035e1-cf59-4019-8ec8-c19f33aa59a1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by red777 on 2007-04-27
then if I go into comp & re mount,every time# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=20ea49ce-a892-42f2-921f-bbacbbb18cfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=181035e1-cf59-4019-8ec8-c19f33aa59a1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I hope you can help

---

### Post by ubuntu27 on 2007-04-27
What version of UBuntu are you using? Is it Ubunt Feisty Fawn (7.04)? 

If so, follow[ this guide]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html"):

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by red777 on 2007-04-27
ok,I tried this & after going thru as described I got the message already the newest version installed.When I follow the steps as directed I only get as far as the enter password/enter & I get  enable write support for external drive only.Mine is internal & how can I tell if this is Feisty Fawn.more than likely as I D/loaded a week ago,but had a friend install it as he appeared to know what he was doing.I wanted a drive that I could use for W........ows xp pro whilst I learnt about this,but now I can't access it at all.I have/had 3 years of work on it & his so called backup discs can't be read, files are corrupted.PLEASE if anyone can assist I am getting a bit desperate to try & retrieve some/all of my work

Thanks in advance

---

### Post by JLAudioFan on 2007-04-27
Looks like the fstab file is the same in both that you posted... I'm not sure how to add new drives/partitions in there...

If you go to Places > Computer...

The window that pops up should have a list on the left side, like this:

user (your home folder)
Desktop
File System  < --- This is where ubuntu resides


If you have extra drives/partitions they should be listed underneath the "File System", and you can right click them and mount them and the files should be available to you with at least read access so you can copy them off the drive.

I hope this helps!!

---

### Post by red777 on 2007-04-27
yes I can do that but I only have a folder marked lost & found which I can't access it.I've discovered that my so called friend has formatted it to ex3g.Is there a program that will allow me to re create to NTFS on this slave drive or try & recover my data.Now I'm really desperate.

please if you can help

---

### Post by red777 on 2007-04-27
Now I'm in panic mode.Please if you know of a way to try and recover my data can you let me know

Thanks to those who have posted but I need some serious help now

---

### Post by JLAudioFan on 2007-04-27
Ouch, if he reformatted it...  

There are data recovery programs out there, but I'm not sure if they would be able to pull info from a drive that was formatted (especially one that went from one file system to a different one).  I'd google "data recovery software"...

I'd say your friend needs a good kick in the pants!

Good luck

---

### Post by red777 on 2007-04-27
Hey thanks to those who tried to help,but I'm afraid it's a lost cause now.

ouch is what he will get for sure,but i'm still left with a drive that wont stay mounted so I can even try & see what is on it, I don't have access at all now.I've even tried to re install XP Pro but it doesn't recognize any drives at all..... maybe I'll just have to dump the lot & build a new system that NO one else will have access to.
I'd rather stick it out & try & work with this but being a beginner at open source I'll probably stuff it completely.

OH well off to create mayhem in this PC, I wonder how long it'll take to destroy it,not long I imagine.

---

