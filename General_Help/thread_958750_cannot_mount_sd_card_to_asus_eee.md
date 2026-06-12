---
title: "cannot mount sd card to asus eee"
date: 2008-10-25
forum: General Help
---

### Post by jimso on 2008-10-25
Hi all. New user here, Just installed Ubuntu to my Asus eee 4G, Amazed that i managed it as I know next to nothing about op systems and other such heavy stuff. Ubuntu is definitely a big improvement on the preloaded stuff on the eee. I do have one problem however...The system wont mount any of my SD cards - says I need to be a superuser! Can anyone help?

Tried all sorts of stuff and i just can't get it to work. Answers in plain English please guys. Im a novice with a capital N!

---

### Post by jadedoto on 2008-10-25
I have an SD card  that I just got today for my Eee, and I plan on keeping it in here permanently... 

I added it to the fstab file, and it works fine for now. Not the best solution, but it works.

Go to a terminal and type in:

sudo fdisk -l 

with the card in the slot.

Look for the /dev/sdXX line that is your card (hint: if the card is like 2GB like mine, it's the one that says it's 2GB).

In the terminal type in "sudo mkdir /media/sd" or replace /media/sd with whatever folder you want to mount the sd card in (it doesn't REALLY matter for all itnents and purposes)

then in the terminal, type "sudo gedit /etc/fstab", or if you have XFCE then type "sudo mousepad /etc/fstab"

At the bottom of the line add:

"/dev/sdb1       /media/sd   vfat user,noauto,exec 0       0"

And replace /dev/sdb1 with whatever you found yours to be when you did the fdisk -l.

---

### Post by jimso on 2008-10-26
Thanks for your reply. I've managed to enter the fdisk command and have a variety of stuff on the display.

Please stick with me on this one... as I say, I really no nothing about this sort of stuff!

I have an 8Gig card in the slot so I guess the bit that refers to it is this bit:

Disk /dev/sdb 8018 MB  8018460672 bytes
219 heads, 12 sectors/track, 5959 cylinders
Units = [ various numbers]
Disk identifier 0x00000000

I've tried several further inputs trying to string together something akin to your instructions. But I'm not having any success. :confused: Based on the above, would you be so kind as to spell it out to me exactly what I should key in next? Thanks. Jim

---

### Post by jimso on 2008-10-26
Ah... I've moved on a bit...

I've got the fstab thing open and I can see that it can be edited and saved. Haven't done that yet though as im still uneasy about getting the text wrong and screwing the whole thing up!

Based on the stuff that i said was on the display in my earlier post, what should i edit the last line in fstab to read? Are all the spaces important?

---

### Post by jimso on 2008-10-26
Its done! Kept at it and got it sorted. Thanks for your help.
Jim

---

### Post by dennizr on 2008-11-06
hello, i have something to add to this. I've been searching a while for this myself.

When i connected my sd card to my ubuntu eee it said that it could not mount because it needed superuser rights.

i tried to configure /etc/fstab correctly. this helps, but now you need to mount yourself from the console, with sudo mount.

if you actually *remove* the line from /etc/fstab that configures the sd card, ubuntu eee can now mount it again, without telling you it needs superuser rights!

---

### Post by Maringouin on 2008-11-10
Thanks, deenizr and others; but I'm afraid that as a complete newbie, I'm still a bit at sea.

Going back to jimso's original query, am I correct that the line he should put in the /fstab file is:

/dev/sdb 8018 MB /media/sd vfat user,noauto,exec 0 0

and if not, what should it be?

And dennizr, what line did you remove from the /fstab file so you can mount the SD card without superuser rights?

And finally, do I need to go through this whole process every time I use a different SD card?

Thank you all in advance for your help and for your patience. I'm learning as fast as I can and I'm grateful for the terrific help provided in this forum!

---

### Post by dennizr on 2008-11-14
> **Maringouin said:**
> 
And dennizr, what line did you remove from the /fstab file so you can mount the SD card without superuser rights?


Hi maringouin,

i removed the line from /etc/fstab that begins with:

/dev/sdb..... etc

so that line that points to the sd card (explained above beginning with /dev/sdb(some number)

now the system can arrange the mounting without use of fstab. you only need to do this once.

make sure you remove the right line ;-) 

sorry cannot explain easier!

---

### Post by olskar on 2008-11-14
If your SD or SDHC card will not mount and throws an error that says “Invalid Mount Option” you will need to edit your fstab. From a terminal run the following:

sudo nano /etc/fstab

Comment out this line with a #:

/dev/sdb1 /media/cdrom0 udf,iso9600 user, noauto, exec 0 0

Your eee may have something other than /sdb1 in the line.

Once you are done, CTL + O to save. CTL + X to exit. There is no need to reboot. You should be able to insert your SD card and have it properly mount.



Does this help?

---

### Post by Maringouin on 2008-11-19
Yes thank you one and all! The problem is now solved and I can read my SD card, no problem!
Thanks again.

---

### Post by b-doherty on 2008-11-26
> **olskar said:**
> If your SD or SDHC card will not mount and throws an error that says “Invalid Mount Option” you will need to edit your fstab. From a terminal run the following:

sudo nano /etc/fstab

Comment out this line with a #:

/dev/sdb1 /media/cdrom0 udf,iso9600 user, noauto, exec 0 0

Your eee may have something other than /sdb1 in the line.

Once you are done, CTL + O to save. CTL + X to exit. There is no need to reboot. You should be able to insert your SD card and have it properly mount.



Does this help?

Yes, that sorted my EEE PC 901 out. The fstab file was telling UBUNTU to mount the /sdc1 as a CD ROM. Which in the EEE it isn´t, it´s the SD card reader. The line I had to comment out was:

/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks for your help.

---

### Post by Rushin on 2008-12-01
Great! Thanks so much. This fixed my problem! 
I am a complete noob. First time Linux user and i love it!

---

### Post by Acem on 2009-03-02
Great advice. I bought an ASUS Eee 1000/Linux, used it for a week, backed up the 32GB SS drive to a 4GB SD card and then installed Ubuntu on the 32GB drive. When I went to recover the data the 4GB SD card would not mount - wanted a super user.

I tried 
> sudo fdisk -l 
without any SD card in the slot and the result made some sort of sense. When I repeated it with the offending SD card in the slot I got "cannot mount volume".

So I tried
> sudo nano /etc/fstab
and saw the two lines that appear to refer to the card ... referring to "cdrom":

UUID= <-various characters->   none swap sw
/dev/sdc1   /media/cdrom   <-various characters->

I followed the advice above and edited a "#" at the start of the second line:

#/dev/sdc1   /media/cdrom   <-various characters->

... which seems to have fixed the problem.

I've no idea what nano is and I found it hard to use. Would gedit have done the job equally well?

---

