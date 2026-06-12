---
title: "Drive not detecting discs..."
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by ajack on 2007-04-29
Hi all,

I have an Acer 3624 and have Fiesty installed (clean install of Dapper and upgraded to Edgy and now Fiesty). Was wondering if anybody else has the same problem as me.  When I insert a DVD disc into the drive of my laptop, Fiesty does not seem to detect it.  Please feel free to ask me any questions or any info as I do not know where to start with this.

Thanks is advance,
ajack

---

### Post by ajack on 2007-05-08
Anybody? :-(

---

### Post by taurus on 2007-05-08
What type of DVD is it:  a movie, a data, or a blank disc?  Does it happen to all DVD and CD  discs?

---

### Post by ajack on 2007-05-08
> **taurus said:**
> What type of DVD is it:  a movie, a data, or a blank disc?  Does it happen to all DVD and CD  discs?

All types of DVDs... actually I only tried data DVDs... no joy, yet when I boot into XP it works... my setup is a dual-boot XP/Ubuntu setup...

---

### Post by taurus on 2007-05-08
And it doesn't have any problem reading CD discs!

---

### Post by DagMan on 2007-05-08
can you manually mount them?
Also, are there symlinks to the device and are they being named right? What does the following 2 commands output at the terminal? 
ls -l /dev/dv*
ls -l /dev/cd*

---

### Post by ajack on 2007-05-08
@DagMan:

> **DagMan said:**
> can you manually mount them?
Also, are there symlinks to the device and are they being named right? What does the following 2 commands output at the terminal? 
ls -l /dev/dv*
ls -l /dev/cd*

This is what I got!

lrwxrwxrwx 1 root root 4 2007-05-09 05:27 /dev/dvd -> scd0
lrwxrwxrwx 1 root root 4 2007-05-09 05:27 /dev/cdrom -> scd0
lrwxrwxrwx 1 root root 4 2007-05-09 05:27 /dev/cdrw -> scd0

@taurus:

CDs are reading fine... just DVDs... I tried both +/- and no joy... :-(

---

### Post by DagMan on 2007-05-09
I don't know any further other than to try to manually mount them and see how that goes.  It's tempting to say that it's a hardware problem but there seems to be a lot of people having problems like this so perhaps not.
Failing someone else being able to help in the thread, try searching for people having similar problems and googling for your laptop on linux specifically.

I guess there's always the restore to "Windows to test the hardware" if you need to.

---

### Post by ajack on 2007-05-09
> **DagMan said:**
> I don't know any further other than to try to manually mount them and see how that goes.  It's tempting to say that it's a hardware problem but there seems to be a lot of people having problems like this so perhaps not.
Failing someone else being able to help in the thread, try searching for people having similar problems and googling for your laptop on linux specifically.

I guess there's always the restore to "Windows to test the hardware" if you need to.

Like I said in my initial post, it works when I reboot the laptop into windoze mode...

---

### Post by wonderdrug on 2007-05-11
Could it be related to this bug?

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868)

A patch was supplied there, but the bug is still open.

---

### Post by d80tb7 on 2007-05-11
Try disabling automounting and auobrowsing in  System->preferences->removabale drives and media.  You might then be able to mount from the command line with a command similar to :

mount /dev/hdd /mnt/cdrom/

I had the same problem as you but this fixed it for me.

Chris

---

### Post by ajack on 2007-05-12
@all:

Yesterday, I was prompted with five new updates.  Mostly was the hald and hal manager components of Ubuntu.  After that update, my DVDs were detected correctly after a reboot.  Strangely, the updates didn't ask for a reboot.  Now all is fine! Thanks for the effort guys... appreciate it... Ubuntu rules! :-)

It has sure come a long way since using 5.04 some two years ago.  :guitar:

---

