---
title: "HP P3005n printer doesn't work unless unplugged/replugged"
date: 2010-02-20
forum: Hardware
---

### Post by Georgesl on 2010-02-20
I have a Dell Dimension 4100 tower, Pentium 3, running Jaunty and all the latest updates.  The only thing I've had to do to get it running is one tweak to get the video card to work correctly at high resolution.

Here's the problem:

When plugged in via USB, the HP P3005n printer is recognized and installed.  A test page will not print.  

However, if the USB cable is unplugged and replugged the job prints after a delay of about 15 seconds.  Same occurs when printing from OOO and Firefox.  It needs one unplug/plug per print job.  Sometimes it will pop up a "the printer may be disconnected" message.  It seems that the printer gets "forgotten" somehow and the unplug/replug procedure gets it remembered.  Perhaps a USB issue?

I searched for a suggest and followed one where I deleted the printer from  the system-administration-printing screen then reinstalling it by typing 

sudo hp-setup -a -i 

in a terminal.

Same result, the printer wants to be unplugged and replugged before it will run a job.

I've done a search where I found the above suggested fix but I can't find much else about this..

Any suggestions for this noob to Ubuntu before I wear out the USB connectors?

---

### Post by Georgesl on 2010-02-22
I'll give this a bump.  Somebody must have had this problem before...

I'll add that the USB ports work fine with thumb drives but I haven't tried any other USB devices.  The mouse is not a USB device.

---

### Post by Scottydogg on 2013-02-05
I have the same problem, but with a different printer, in my case a Phaser 3300 MFP. 

As long as I unplug/replug it for every job, it works fine. 

I know if it needs to be unplugged because when the print dialogue comes up,under status it will say, "sending data to printer." That means it ain't gonna work and it needs to be unplugged. 

Once I figured out I just need to unplug it all the time it became more hassle than headache. But still a hassle.

---

