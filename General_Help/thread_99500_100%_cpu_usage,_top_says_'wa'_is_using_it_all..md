---
title: "100% cpu usage, top says 'wa' is using it all."
date: 2005-12-05
forum: General Help
---

### Post by kspr on 2005-12-05
Please see attached picture.

What is wa? and how do i make it stop doing this to my poor cpu? 

i cant find any processes using much cpu.

---

### Post by kosmic on 2005-12-05
where is 'Wa' ?? I've looked at your image and only see X.org, gnome-terminal and init listed

---

### Post by kspr on 2005-12-05
it's not a process in itself, check  the line CPU(s) 1.0% us ....... 98.7% wa

---

### Post by kosmic on 2005-12-05
eheh just do a man top and see what wa is :)

---

### Post by kspr on 2005-12-05
kosmic: unix manuals seems to be written for other species than humans, so no thanks :)

Well, wa seems to have to do with hard-drives, usb-memories etc. 
i found it was my "walkman" mp3-player who made it go nuts, after copying files to it it still reports high load on wa.

---

### Post by rolfen on 2007-07-03
1.  us -> User CPU time: The time the CPU has spent running users&#8217; processes that are not niced.
   2. sy -> System CPU time: The time the CPU has spent running the kernel and its processes.
   3. ni -> Nice CPU time: The time the CPU has spent running users&#8217; proccess that have been niced.
   4. wa -> iowait: Amount of time the CPU has been waiting for I/O to complete.
   5. hi -> Hardware IRQ: The amount of time the CPU has been servicing hardware interrupts.
   6. si -> Software Interrupts.: The amount of time the CPU has been servicing software interrupts.

source:  [http://www.idealwebtools.com/blog/top/](http://www.idealwebtools.com/blog/top/)

Sorry for digging up an old thread... just thought this may be helpful for someone some day.

---

### Post by gyrfalcon on 2008-01-28
I'm copying files from my system to a USB drive (FAT32) and _70% of the system is busy with **sy**_, the _other 30% is buys with** wa**_.

I'm running Ubuntu 7.10 64bit on a dual core system.


What's going on here?  The system is basically frozen and locked up.  It took me 20minutes to switch from the X-Window console, login, and get top up and running.

kswapd is around 25% CPU, gtk-gnash is taking up 82% of memory.

---

### Post by jpeddicord on 2008-01-28
> **gyrfalcon said:**
> I'm copying files from my system to a USB drive (FAT32) and _70% of the system is busy with **sy**_, the _other 30% is buys with** wa**_.

I'm running Ubuntu 7.10 64bit on a dual core system.


What's going on here?  The system is basically frozen and locked up.  It took me 20minutes to switch from the X-Window console, login, and get top up and running.I/O on the drive could be eating all of the time, especially if the drive is slow. How much data are we talking about here?

---

### Post by gyrfalcon on 2008-01-28
> **jacobmp92 said:**
> I/O on the drive could be eating all of the time, especially if the drive is slow. How much data are we talking about here?

17gigs of data is what I'm transferring to the USB drive...  I can under stand I/O taking up CPU cycles, but this is crazy.  Maybe part of the issue is that I have Azureus open which uses a lot of "open files" in the kernel???


Not to be a jerk, but Linux seems to have a lot of "stupid" issues.  For example without the post above I wouldn't have known wa -> iowait or sy -> System CPU time.

It also appears that that info is missing from the man page for top.

Of course I'm a stupid user, but having apparently stupid documentation doesn't help.

---

### Post by stroyan on 2008-01-28
Kernel 2.6.23 and later are likely to make that situation much better.  A recent change fixed a problem where heavy writing to a slow device would slow down writing to other fast devices.  The feature was discussed on the linux kernel mailing list as "per-device dirty throttling".

---

### Post by fyo on 2008-01-28
> **gyrfalcon said:**
> It also appears that that info is missing from the man page for top.

$ man top

2c. CPU States
       The CPU states are shown in the Summary Area. They are always shown  as
       a percentage and are for the time between now and the last refresh.

        us  --  User CPU time
          The  time  the  CPU  has spent running users’ processes that are not
          niced.

        sy  --  System CPU time
          The time the CPU has spent running the kernel and its processes.

        ni  --  Nice CPU time
          The time the CPU has spent running users’ proccess  that  have  been
          niced.

        wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.

        hi  --  Hardware IRQ
          The amount of time the CPU has been servicing hardware interrupts.

 Manual page top(1) line 446

---

### Post by gyrfalcon on 2008-01-29
> **fyo said:**
> $ man top.... Manual page top(1) line 446

To be completely honest I didn't try **man top** on my Ubuntu system but I'll check it out tomorrow.  I did look for info on [http://www.rt.com/man/top.1.html](http://www.rt.com/man/top.1.html)  and on my SUSE system which doesn't have any CPU States section in man.

---

