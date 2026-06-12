---
title: "acer aspire one 532h-2db &amp; Ubuntu 10.10 cant get Mic working"
date: 2010-11-14
forum: Hardware
---

### Post by danielfarley on 2010-11-14
Hi fellow linux users

I have a aspire one 532h-2db and am running 10.10 on it... most things work ok... inc web cam :-) but the mic does not :-( any ideas how to solve this??? 

Other things that are not working for me is, SD card reader, and power management sometimes thinks battery is flat when it is not... but then jumps back to real reading

Any ideas on any of these frounts??? mic is most important to me so i can skype.

Thank
Daniel

---

### Post by guillelo11 on 2010-11-20
Same problem here with my Aspire One 532h, the mic and the card reader doesnt work but the card reader has an [open bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277") in Launchpad.

---

### Post by cesar.ramsan on 2010-11-21
About the sd card reader, I have an script that can fix your problem.
The problem is that the sd card reader uses proprietary drivers, but there are other drivers available from moblin that have been adapted for the latest kernel. You can see all this in this in here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277")
You can download the drivers from here:
[http://www.qylla.com/downloads/]("http://www.qylla.com/downloads/")
I have to give thanks to the guy how got the drivers and posted the instructions for compiling the driver. What you have to do is just decompress the folder and run the install.sh script and that should work :)

In the case of the of the mic the solution is also posted in the HardwareSupport/Machines/Netbooks page:
"
$ sudo apt-get install pavucontrol
$ pavucontrol

Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence."

And with the battery issue, well I havent found anything for that yet :(

hope this can help :)
Peace

---

### Post by danielfarley on 2010-11-21
OK, so i have found that the mic plug works... so if i plug a mic in its fine..... so some how we need to find a way to tell alsa to give us volume control options for the internal mic as well as the mic jack.

---

### Post by danielfarley on 2010-11-21
> **cesar.ramsan said:**
> 
In the case of the of the mic the solution is also posted in the HardwareSupport/Machines/Netbooks page:
"
$ sudo apt-get install pavucontrol
$ pavucontrol

Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence."


Hmm... this worked... as far as making it capture from the internal mic rather than a pluged in one, also seems like if you have full volume on right channel and silence on left you get input just from pluged in mic... when using the internal one like this i get a bit of static with the recording... so not ideal... if i set the volume to 80% it is ok... volume to static ratio tho.

will have a play with the sd card latter on.
Thanks Daniel

---

### Post by danielfarley on 2010-11-21
just tryed the sd card fix... still not working for me :-(...

---

### Post by danielfarley on 2010-11-22
> **danielfarley said:**
> just tryed the sd card fix... still not working for me :-(...

OK, working now...  i think it was rebooting  (cold ie turn off and on) with a sd card in the slot on boot that sorted it... now mounts and un mounts two difrent cards.. havent tested after suspend or after turn on with out a sd card in. yet... but definitely looking good.  

Just the random battery mis readings to fix now...

o and if posable the static from the internal mic...

---

### Post by luckylucky on 2010-11-26
> **danielfarley said:**
> Hmm... this worked... as far as making it capture from the internal mic rather than a pluged in one, also seems like if you have full volume on right channel and silence on left you get input just from pluged in mic... when using the internal one like this i get a bit of static with the recording... so not ideal... if i set the volume to 80% it is ok... volume to static ratio tho.

will have a play with the sd card latter on.
Thanks Daniel

sudo apt-get install pavucontrol
 pavucontrol
Thanks.  This got my audio working in my acer aspire one.  Thank you!

---

### Post by guillelo11 on 2010-12-10
> **cesar.ramsan said:**
> 
In the case of the of the mic the solution is also posted in the HardwareSupport/Machines/Netbooks page:
"
$ sudo apt-get install pavucontrol
$ pavucontrol

Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence."


In Kubuntu 10.10 it doesn't work. I still have the same problem with the mic :(

---

