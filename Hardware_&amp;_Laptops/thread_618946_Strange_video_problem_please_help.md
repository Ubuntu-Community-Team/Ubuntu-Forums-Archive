---
title: "Strange video problem please help"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by monkeymartin on 2007-11-20
Strange problems My TravelMate 2300 laptop has been running great. The other day I booted PCLinuxOS the the screen went black and flikerd
I thought it was a software problem with PCLinuxOS,  so I burnt a Ubuntu 7.10 CD but the same thing happens 

I put my puppy Linux 3.00 in,  and everything works great.

what could be the problem?
what would be the difference between Puppy Linux (works) & Ubuntu, PCLinuxOS (Not working)?

All operating systems seem to have the same Xorg version

I downloaded and burnt many Ubuntu disks with different computers.  All the disks boot to the Ubuntu progress bar.  everything seems to work.  Just as the bar finishes the screen goes black.  I can hear the startup music in the background. It seems like everything is working I just can't see it.  The only thing that I can think is that it must be a bug in a a peace of software that is in PCLinuxOS and Ubuntu (older versions of Ubuntu and PCLinuxOS work)  

Thanks for your time

---

### Post by Grafster on 2007-11-21
My travelmate's video also completely punked out recently. I've tried different operating systems but everything that uses the most recent kernel and xorg seems to not work.
Older stuff, including live CDs, works fine.

---

### Post by uktedc on 2007-11-21
I have had a similar problem trying to boot the active disk system onto a Del Inspiron 2500. In my case the problem was due to the hardware not setting up the file /etc/X11/xorg.conf. correctly. Xubuntu does not seem to have the same problem. If you have an xorg.conf that works on your hardware copy it to a floppy.
Boot and wait for the music
ALT+CTRL +F2 to get you into terminal mode
mkdir /floppy
sudo mount /dev/fd0 /floppy
sudo cp  /floppy/xorg.conf   /etc/X11/xorg.conf
ps all
look a list of processes for the pid of /usr/bin/X
sudo kill  pidnumber

At this point the user logon screen appears and after a few seconds signs on as Ubuntu
and if this as worked you should see the gnome desktop appear.

---

