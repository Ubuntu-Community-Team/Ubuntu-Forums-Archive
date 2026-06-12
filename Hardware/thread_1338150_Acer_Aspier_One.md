---
title: "Acer Aspier One"
date: 2009-11-26
forum: Hardware
---

### Post by Czubek on 2009-11-26
Hi,
my name is Damian, and I'm Ubuntu user for nearly five years. I think it's brilliant distribution but I have a problem.

I'm using Ubuntu Netbook Remix 9.04 on Acer Aspire One (AOA110), and I suffer from poor performance. I guess that I should upgrade hardware to solve that problem but I don't really know to what.

As far as I know, I can upgrade:
- ram (add 1024 MB)
- battery (more cells to extend lifetime on battery)
- disk (now: P-SSD1800)

I think that disk is causing most of problems because, when I'm working, netbook is freezing with hdd light in state "in use". Now I have ext2 filesystem, and when I had ext3 it was even worse.

So now my questions:
Is disk cause of my problems?
If it is, which one can You recommend me to replace old one?

Thanks

---

### Post by klemes on 2009-11-26
That the HDD light stays on when Ubuntu freezes is not an indication that it is a hard disk failure.Your configuration wit 1GB RAM seems more than adequate so definately no need to upgrade if anything is not broken.
Why dont you run the Memtest from the grub menu while booting and leave it for a while at least until when it has completed a full pass and see if it is a memory/CPU related problem.
That is what I have to recommend for now.
And also have a look at the system logs for indication for a software/hardware error by giving : less /var/log/messages in the console.Look the at the time stamp in the left column and scroll to the last message from the previous boot when you encountered the freeze.It may give us some information about the nature of the problem.

---

### Post by Czubek on 2009-11-26
When I was writing freeze I was thinking about something like that:

1. some normal work.
2. open terminal emulator from GnomeDo.
3. ~ 5-10 seconds of complete unusable system (can't even move cursor), with disk "in use".
4. unfreeze and ability to normal work.

This netbook never troubled me with kernel panic, lost data and any possibly hardware related error. It seems to me that, if I run Firefox or something ram consuming, system uses swap partition which is so slow that I can't use netbook until writing is compete. 
Or I am wrong?

Oh, and I have 512 MB ram, and I can add 1024. I know it's minimum and I'm wandering which upgrade will bo0st performance more, ram or disk.

Thanks.

---

### Post by klemes on 2009-11-26
Maybe then you should try to make a file system check on your harddrive by booting with a LiveCD.Just a thought.
An other idea is to minimize swapping on and off the hard disk by adding the vm.swappiness = 20 line in your /etc/sysctl.conf and rebooting.
Sorry I completely misunderstood your statement about RAM in your first post.Of course if you have the opportunity to upgrade to an other 1 GB of RAM do it by all means.There is no such thing as too much RAM when it comes to computers!!!!

---

### Post by Czubek on 2009-11-27
That's very interesting:
after addition: vm.swappiness = 20 line, my system runs smoothly almost all the time. So I guess that buying more RAM should guarantee me stable, freezes free work.

Thanks for help :D

---

### Post by wilee-nilee on 2009-11-27
I have a aspire one not sure which model I bought only about 2 months ago. I found the netbook remixes problematic in Jaunty and Karmic and just installed the regular desktop and bumped the ram to 2 gigs it runs very fast with a W7 dual boot.You might download the regular desktop ISO and put it on a thumb with usb creator and set the persistent almost all the way to the right and boot from it and do all the updates and see if it runs better. Ram is cheap so that may be the answer.

---

### Post by 3rdalbum on 2010-03-03
The SSD has very low performance - it can be up to nine seconds before data gets written to it, which is incredibly bad. There are visual guides out there about how to remove the SSD and add a 1.5 inch HDD. Bear in mind that those 1.5 inch HDDs are not really intended for running your computer! (you can, though).

I bought a newer Aspire One with a hard disk and I don't have those speed issues anymore.

---

