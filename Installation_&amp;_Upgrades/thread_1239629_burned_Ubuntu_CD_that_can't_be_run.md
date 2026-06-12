---
title: "burned Ubuntu CD that can't be run"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by asdlkj on 2009-08-13
I burned the CD [unbuntu.iso]
the usual way..
My comuter can read and open the CD.
There is absolutly no problem with the CD...
but strangly, I can't run the CD to install[setup].
I tried on a different computer.. it works.
Only my computer doesn't seem to be able to run.
It does the "sound" of loading and then.. nothing happen.
I haven't tried to run other burned iso CD recently.
But previously did and it worked.
 
Please.. hope someone can help me.
 
I have the Window XP installed on my computer.
Which was the same for the other computer I tested on.
 
Thank you in advance and again.

---

### Post by raymondh on 2009-08-13
It seems that the issue is pointing to your hardware.  

You may want to try a USB install using unetbootin.... as a workaround to the cd drive.

Just out of curiosity, how many partitions does your HD have already (primary and extended)?

Raymond

---

### Post by asdlkj on 2009-08-13
Hard Drive, I have 2 or 1.
Presently, I'm not home.

---

### Post by asdlkj on 2009-08-13
USB install : how do you do it? 
never tried... yet

---

### Post by ghpk on 2009-08-13
How about cleaning the Lens of your CDROM ?
a dirty lens can prevent the DISC to be read properly.

---

### Post by raymondh on 2009-08-13
Reading materials for your reference

[https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

1.  Back up your files.  There are no guarantees

I asked for partitions (consider them spaces inside your Hard Drive 'HD') because I have seen some installs (me, particularly) that will not install when the max limit of partitions are existing, hence requiring that the operator 'open' up a partition.  

If you are curious, in XP, open up your disk manager and it will show you how many partitions your HD has.  

I mentioned that the issue may be pointing to your hardware as your first post mentioned that you tried the liveCD in another computer, hence the suggestion to do a USB install (see unetbootin)

A USB install .... 

1.  make sure your BIOS allows you to boot into a USB otherwise this will be a futile exercise
2.  you have to create a liveUSB (I use a 4GB but I think you can get by with 2GB)

Re-reading your thread ... when you said "I burnt the CD the usual way" .... I assume that you burnt the iso image.  Sorry to ask because there have been times when the operator just copied the iso image to disk instead of burning the image.  Also, can you check the [md5]("https://help.ubuntu.com/community/HowToMD5SUM") of that disk.

Good luck.  Back up.

Raymond

---

### Post by asdlkj on 2009-08-13
it does make sense maybe...
I'll check later tonight how many partition I have.
Thank you.
 
i burned the software.
CD to CD(iso) using daemon.

---

