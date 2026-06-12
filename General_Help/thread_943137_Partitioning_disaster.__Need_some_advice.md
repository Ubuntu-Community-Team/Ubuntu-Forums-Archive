---
title: "Partitioning disaster.  Need some advice"
date: 2008-10-09
forum: General Help
---

### Post by dshuck on 2008-10-09
For the past few years I have had my single laptop drive partitioned so that the primary partition is 15GB which I mount as /, then have a remaining 135GB partition that I mount as /home.  By taking this approach, I can bounce in and out of various distros, and always keep my home directory in tact. 

Due to problems I am having with a projector at a location where I often do presentations I decided I (quite grudgingly) install Vista on a small section of that 135GB space.

I was following the *very* detailed instructions on this page ( [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm) ) which explain how to dual boot vista when linux is already installed.  

I started by shrinking my /home partition using gparted to free up 20GB of unused space.  As I walked through the steps and selected the end of my extended partition as the installation location I was prompted that I couldn't do so (as the instructions indicated would happen).  When I went into the paritioning MS partitioning app in the MS terminal it didn't let me mark that partition as active.  After doing a bit of searching it appears that it was due to the fact that it was the end of the extended partition.

At this point I decided I would move my /home partition to the end of the extended partition using gparted and try again. 

That was the end of good times as I knew it.... :(

After almost 3 hours it got to the very end of the moving process and I was prompted that gparted failed in the moving action and it allowed me to save the error.  Please take a look at this and see if it makes sense to you!

[http://dl.getdropbox.com/u/101948/gparted_details.htm](http://dl.getdropbox.com/u/101948/gparted_details.htm)

To me it appears that it moved everything to the right, but simply failed on writing the tables that describe the data.

When I attempt to log into Ubuntu at this point, the / mount is fine and it boots up to GDM.  However, it can't find /home from that point.

Interestingly enough when I log in through terminal from the GDM, I can CD to /home and can clearly see the directories that I had underneath /home.  However when I try to CD in, it says that they are not actual directories.

One other bit of info... if I boot back into a live CD and run gparted, upon scanning the drive it shows as 149GB of unpartitioned drive.

If *anyone* has any advice that can get me back to healthy I would be more grateful than words could express.

Thanks...

---

### Post by gpsmikey on 2008-10-09
Well, this is sort of a "off in left field" answer, but you may be able to do something with it.  If you can find another drive the same size, you may be able to (using dd on a Live CD) copy your entire drive over to the second drive - byte for byte.  That would let you try various recovery ideas on the second drive while not doing any more damage to the primary one.  Just a thought.  There are also other "copy disk" utilities out there that may be able to do the same thing.

mikey

---

### Post by bodhi.zazen on 2008-10-09
You may wish to see if test disk can help :

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

