---
title: "GRUB error 17/ ubuntu  9.04 full install fail"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by ihabelnaccash on 2009-08-11
I have an older Dell Inspiron 8000 PIII 1000, 512 Mb RAM. I was running XP pro (upgraded from Win2000Pro. Initially I Installed a dual boot of Ubuntu 9.04 Desktop edition from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
The Dual boot was to see how well everything would run (and it ran great!) The only hitch was bootng off the CD didnt work until I installed Grub through windows IIRC.Once I determined that everything was working OK - screen/ audio/ etc- I backed up my photo's and audio files from the XP side and tried to reinstal Ubuntu 9.04 *using the whole disk*
The install started OK , but then while it was writing to disk it took a power hit and the laptop powered down. At this point I can still get into the BIOS and still have the laptop set to boot off of the CD rom first- figuring I would just start the install again, but now everytime it gets out of the POST it says :
'Grub loading
error 17'
then it just hangs...
For whatever reson now despite the BIOS saying to check the CD drive first - it still seems to be going to my HDD. My thoughts for tonights attempt after wor would be to re burn another copy of Ubuntu to see if the CD is damaged (but it didnt work with an XP disk either, and I may have to do some serious digging to find the original y2k disks) If that doesn't work then I can take the hard drive out, reformat using a usb case, and then put it back into thte laptop and try a fresh install again...
Am I overlooking something obvious? Ive done some searching through the archives here and most solutions seem to be assuming I can get to boot off of the cd (which doesnt seem to eb working)
Thanks for any help in advance...

---

### Post by running_rabbit07 on 2009-08-11
You should be able to put th eLiveCD in and hit whichever takes you to the boot drive selection screen. May be ESC, F2, F8, F10, or F12. Then select the CD drive. 

You are getting the grub error because it never got to finish installing.

---

### Post by ihabelnaccash on 2009-08-11
It's F2 on the machine and I have my CD as the first boot drive already...

---

### Post by Yvan300 on 2009-08-11
Yeah maybe it is the Live cd itself, did you say if you are able to boot from the xp cd?

---

### Post by running_rabbit07 on 2009-08-12
> **ihabelnaccash said:**
> It's F2 on the machine and I have my CD as the first boot drive already...

I have mine set the same way and it never boots that way unless I go int and tell it to.

---

### Post by madhavhmk on 2009-08-12
Please boot using live cd and post output of 
sudo fdisk -l

---

### Post by ihabelnaccash on 2009-08-12
I couldn't get it to boot from either optical drive from either xp, or the livecd... The Grub error 17 kept popping up no matter what the boot order I selected so I pulled the HDD and popped it into a USB enclosure. I was able to see the disk volumes, but unable to format the drive using regular means through xp (it wouldnt see the drive - except when I looked in the device manager- where it did see the disk volumes and partitions) so in frustration I decided to wipe it clean with a low level format tool. At this point I could either put it back in the laptop when I get back from work tonight, and try the live CD again for a re install, or is it possible to do the install from my other machine onto the drive (laptop 2.5" 60 GB IDE in a usb enclosure) first, then install it into the laptop ready to go?

---

