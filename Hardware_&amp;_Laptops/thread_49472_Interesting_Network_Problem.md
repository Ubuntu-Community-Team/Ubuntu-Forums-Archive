---
title: "Interesting Network Problem"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by autocrosser on 2005-07-16
I have no problem connecting with a modem the first time, in fact, the modem dials out as I am logging into my main user account--- (any idea how to disable this?)---But, when I use the Modem Applet, Network control panel or any dialer I've downloaded--the system goes thru the motions, but will not connect. If the modem connection dies or my ISP "kills" the connection (happens after 8hrs), I can redial without problem--

Question is--is there a cron that is looking at network activity & re-sets after a certain interval? Or do I have a config problem? I have tried to re-set the network via command line, but this seems to not work---My last Distro (YellowDog 4.01), did not have this problem, so I do not believe this is a hardware issue. :-? 

Any ideas??

Cheers!!
Dean

---

### Post by autocrosser on 2005-07-16
Well--As normal, I am my own worst problem  :|  I had installed Ubuntu on my / drive & re-linked my /opt-/tmp and /home directories from Yellowdog (some things I did not want to lose)--Part of my /home config was wvdial.conf----well, to make a long hunt short, Yellowdog used /dev/USB/ttyACM0 and it seems that Ubuntu uses /dev/ttyACM0--I simlinked dev/ttyACM0 to /dev/modem and my problem "magically" solved itself--- :smile: 

Cheers!!
Dean

---

