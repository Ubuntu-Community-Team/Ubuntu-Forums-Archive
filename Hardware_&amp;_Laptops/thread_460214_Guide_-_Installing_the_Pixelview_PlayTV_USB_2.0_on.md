---
title: "Guide - Installing the Pixelview PlayTV USB 2.0 on Ubuntu Feisty"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by dbrunod on 2007-05-31
Dear Colleagues,

I´m recent to Ubuntu, and for that reason I find that the drivers issues are the most complacated for a novice. Myself I´m novice, and thats why I decided to create this forum. After searching the web for several days, I came up with a junction from different posts about how to setup a Pixelview PlayTV Mpeg 2.0 USB on your Ubuntu.
Most of the posts refered to the PCI card, and none of them as complete, so my intention is to create a more complete guide.

Please keep in mind, as I found out this week, that when you update the kernel, you need to to this again to get it working, since it appends several drivers to the main kernel ( please correct me if this is mistaken)

Here it goes:

First download and install the TVtime Program (use Synapitc)

On the terminal:

> 
# hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

It will take a while, because there are several drivers.


Then:

> #cd v4l-dvb-experimental
#make && sudo make install

Then
> #sudo modprobe em28xx

Then
> 
Execute -   setup.sh on the 
 /v4l-dvb-experimental/v4l_experimental/xc3028/
folder. 

> Restart the computer...

>  Access TVtime and it should be working fine. If not you will have the message:
/de/video0 not found... 

Redo the steps above.

Kind regards,
Daniel Brunod

---

### Post by toon_irc on 2007-08-13
I used your guide and my HW works, but after some time it stops.

My system: Ubuntu Gutsy  2.6.22-9-generic
When it's happening the two lights of HW are on, the modules is up, but the /dev/video0 it disappeared when I close the tvtime.

But now, after some tests, with the use of mplayer the HW is working fine!
I think that my problem is only with the tvtime.

But I have one more. The remote control isn't working!

Best,
Igor

---

### Post by lnunes.eng on 2008-05-30
I tried this, but I get no /dev/video0 device...

Any suggestions?

---

### Post by Joeb454 on 2008-05-30
Make a new support thread about it. Are even still running Fiesty?

---

### Post by lnunes.eng on 2008-05-30
I'm gonna do this right now...

I'm using Gutsy...

---

