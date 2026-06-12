---
title: "Clean Install"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Holden99ca on 2009-05-20
Hi,

I can't find a way to do a clean install of ubuntu on a dual boot machine. I'm fine with just booting from live cd, formatting the ext3 drive (and swap?) and then rebooting from live CD and installing but would that mess up GRUB? Would it just successfully install on top of my existing (but empty) partitions?

I can reset things to factory default but that would also clean all my windows settings which would bum me out. I'm not worried about documents because I have everything backed up.

Can anyone provide guidance here please?

---

### Post by cybrsaylr on 2009-05-20
I've dual booted since 2006 with no problems.
Just did a clean install of x64 Jaunty from x32 Intrepid recently.
All I did was select the partition Intrepid was on to install Jaunty with Live CD and Jaunty installed and overwrote Intrepid. Even selected to 'save' favorite settings and they were carried over to Jaunty...took about 15 minutes. 

My Windows partition was not touched and left intact, although Windows is seldom used anymore.

---

### Post by ghreyzeus on 2009-05-20
):P[FONT=Georgia][SIZE=3]Hi! i just brought a Toshiba NB100 at first glance everything is working including the gstreamer but when i totally used the net, i ask for updation so eventually i end up updating everything. as of the moment i'm using Orca as terminal  and then got eakiga and when i tried to used to rhytmatic box, totem and surprisingly it wasn't work and i notice in tool bar that speaker mark out as ex red mark eventually i remove it to the panel. and i was left out as clueless to work on those speaker. Could anyone can suggest to figure out on this (i'm just average user and first timer on linux and ubuntu, i'm used to a microsoft.) thank you so much. [/SIZE][/FONT]

---

### Post by Holden99ca on 2009-05-21
That totally did the trick. Thank you. The only thing I needed to know that wasn't sure about was, after I choose the option to manually select the partitions, I select / as the boot mount.

---

