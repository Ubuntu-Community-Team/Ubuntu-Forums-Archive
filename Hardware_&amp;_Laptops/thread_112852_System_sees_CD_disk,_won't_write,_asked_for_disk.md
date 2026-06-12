---
title: "System sees CD disk, won't write, asked for disk?"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by Nightwind on 2006-01-05
Hi Y'all
Attempted to back up my system, put the CDRW disk in, system sees it, when I attempt to write the files to the disk, it asked for a disk, so I put in another disk thinking there could be an error on the disk it's self, but same message. CDRW drive worked fine when it was under XP, wote to CDs with that drive, loaded 5.10 with that drive, plays music, reads files,so is there something I am missing here?:confused: 
Thanks

---

### Post by rjay3 on 2006-01-07
I have the same problem with my TDK CD-RW Drive trying to Write to Disk. Kept asking to 'Insert a rewritable or blank disk'.......so I tried to write to my external HP CD-RW/DVD+R there was no problem at all burning the ubunto 5.10 -live-i386.iso file. Funny you haven't gotten a reply. I hope someone sees this thread.

---

### Post by taurus on 2006-01-07
Are you trying to backup your system as a regular user or do you use sudo???

---

### Post by Nightwind on 2006-01-07
[QUOTE=taurus]Are you trying to backup your system as a regular user or do you use sudo???[/QUOTE]
As sudo. I want to back up what I have on that machine then I am going to change it to a server install only.

---

### Post by Amon_Re on 2006-01-08
Did you try it with gnomebaker or simular program?

---

### Post by Nightwind on 2006-01-09
[QUOTE=Amon_Re]Did you try it with gnomebaker or simular program?[/QUOTE]
No I haven't yet but that will be the next thing I try 
Thanks

---

### Post by rjay3 on 2006-01-09
I did an experiment. I inserted a blank cdrw into my TDK and the "Burn Audio, Photo, or Data CD" window pops up. I click on "Burn Photo CD", the CD/DVD Creator opens up. I go to my home directory, open up my photo folder and copy/paste a few photos to the CD/DVD Creator window. I then click on 'Write to Disc' and another 'Write to Disc' opens where I can choose my TDK. A " Writing Files to Disk" opens up and says it's initializing...but the "Insert a rewritable or blank disk also pops up. I click on OK a few times, click Cancel. Guess what.........the photos have been written on the disc!! Isn't this strange? Is this a bug? :confused:

Edit: Copying and Pasting works fine without having to go through all the 'write to disc' scenario......... I even went to the Help section, folllowed the Writing to CD instructions and the instructions need to be revised for Ubunto 5.10.

---

### Post by StefanoCole on 2006-01-11
rjay3, I have experienced the same (the only difference was my media being a CD-R). Since I was not able to burn the CD with Nautilus Burner I switched to GnomeBaker and I was successful!

Stefano

---

### Post by korna on 2007-06-17
I have a similar problem with DVD+RW disks. 

My very first trials I couldn't write nor format/erase with gnomebaker, brasero or graveman. Then I tried in windows and I had no problems at all. 

Second trial I managed to erase and then burn the same disks with brasero (after the first trial). 

Now the third trial I had erased the disks in windows and tried to burn with brasero and again the program refuses to burn. It does erase the disks but doesn't want to burn.
So I tried gnomebaker and (without erasing them for a 3de time) it burns the disks!

This is very confusing.. are we dealing here with bugs or with compatibility problems?:confused:

---

