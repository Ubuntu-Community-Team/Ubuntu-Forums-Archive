---
title: "Move /Home to a New Machine?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by notyou on 2009-02-24
Just ordered some parts from Newegg (Shuttle case, HD, CPU, RAM, Vista) for a desktop I plan to dual boot Vista and Ubuntu. I'm currently dual booting Win2k and Ubuntu on this old machine.

My plan is to install Vista first followed by Ubuntu with a separate partition for /home. Having installed and reinstalled Win2k plenty of times, I'm comfortable with that bit of the transfer. I'm less certain about the Ubuntu side of it, however. 

I'd like to keep as much of the data and configuration settings in my current Ubuntu install as I can without cloning the disks. Will simply copying the /home folder over to the new partition on the new machine do the job?

---

### Post by ddrichardson on 2009-02-25
Why not use tar?
```
cd /
tar cfvz home.tar.gz home
```Then you can untar the file to the root of the new drive:
```
cd /
tar xvfz home.tar.gz
```
Then you have a backup too.

---

### Post by apmcd47 on 2009-02-25
> **notyou said:**
> 
My plan is to install Vista first followed by Ubuntu with a separate partition for /home. Having installed and reinstalled Win2k plenty of times, I'm comfortable with that bit of the transfer. I'm less certain about the Ubuntu side of it, however. 

I'd like to keep as much of the data and configuration settings in my current Ubuntu install as I can without cloning the disks. Will simply copying the /home folder over to the new partition on the new machine do the job?
Definitely a good idea to keep a separate partition for /home. It will insulate it from system directories if you ever need to reinstall again, for instance. Just one word of warning: make note of uid/gids and usernames on the old /home and use these when creating new users. Use ```
ls -ln /home
``` to find the uid/gids.
> **ddrichardson said:**
> Why not use tar?
Then you can untar the file to the root of the new drive:
Then you have a backup too.
In my opinion (not the best;)) this is probably the best way of copying /home over to the new partition. Tar up before you start and untar after the new users have been created on the new partition.

Andrew

---

### Post by notyou on 2009-02-26
Thanks for the advice.

I ended up copying the old /home to a USB hard drive (in the terminal: sudo cp -a) along with file-save markings from Synaptic  (as advised here: [http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)). 

After I installed Vista and Ubuntu (with a /home partition and a user with the same name and password as the old), I copied the old home off the USB HDD. Seems to have worked pretty well. I lost some tweaks to the display (font appearance). And I've forgotten how I got the logitech bluetooth keyboard and mouse to work on the old system (for the moment, disconnecting and reconnecting the BT dongle seems to work), but otherwise... a mostly painless operation.

---

