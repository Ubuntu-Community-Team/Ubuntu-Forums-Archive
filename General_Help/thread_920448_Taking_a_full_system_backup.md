---
title: "Taking a full system backup"
date: 2008-09-15
forum: General Help
---

### Post by Armaron on 2008-09-15
I'm trying to get a full system backup, but it doesn't seem to be working.

I've tried several things:

Using Simple Backup Tool
Using Keep
Trying to put all the folders under / in a .tgz archive (except /proc, /mnt, /sys, /lost+found and /home (got it on a diffrent drive atm, so no need for backing up all those big files in there))

But every option seems to fail me. Do you have any suggestions?

---

### Post by phidia on 2008-09-15
[This]("http://mondorescue.org/") is a good tool IMO. 
There is potential for [time vault]("https://wiki.ubuntu.com/TimeVault") too but I think it's still beta.

---

### Post by Bucky Ball on 2008-09-15
Try partimage.
[B]
sudo apt-get install partimage[/B]

Then:

**sudo partimage**

... to run it. Runs in the terminal but there is a gui. :)

---

### Post by kokkus on 2008-09-15
Or you can try Remastersys.
With Remastersys you can create a full system backup bootable installation live CD. 
2 kind of different backups. 
With or without private data.

If you don't want the iso image cd file, you can simply compress the temp files to an archive or covert the iso image file and delete the boot files.

---

### Post by Armaron on 2008-09-15
> **kokkus said:**
> Or you can try Remastersys.
With Remastersys you can create a full system backup bootable installation live CD. 
2 kind of different backups. 
With or without private data.

If you don't want the iso image cd file, you can simply compress the temp files to an archive or covert the iso image file and delete the boot files.

I tried it with Remastersys and it just spend 3 to 4 hours making a file. Now it's finished. But I can't find the file anywhere. I just ran the command:

> 
ken@computerken:~$ sudo remastersys backup ubu_080915.iso


Where would Remastersys normally put the output?

---

### Post by Bucky Ball on 2008-09-16
Try:

**locate ubu_080915.iso**

... if that is the name of your file. Should find it.

---

