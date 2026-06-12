---
title: "no sound cs4281"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by ste1 on 2005-04-23
Hi!

I am new to linux and to ubuntu. I have browsed through the fourums and found out that there are many issues concerning sound cards, but I have not found any solution that has worked for me. 

My system: Toshiba Satellite 1670 cds, 550mhz celeron, 160mb ram

the sound card is a CS4281. It is recognised in the device manager, but I get no sound. In fact, the progressbar does not move in the cd player when I try to play cds (although it fetches the correct information about the artist from the internet database). 

When I try to open the volume control utility I get an error message saying something like "no devices can be found". I have read about the alsa mixer but I can not find that utility on my system. I used the synaptic package manager to re-install alsa (both types of package) and also to install XMMS. I rebooted but nothing happened. 

I have looked at the unofficial guide for beginners but failed to find information on this matter.

I would be grateful if you could spare a couple of minutes and help me to solve this problem. 

thanks!
 ;-) 
Stefan

---

### Post by frehberg on 2007-03-30
if you see the message "can't open device /dev/dsp" you have got to add your user to group "audio" otherwise your user is not able to open the sound devie /dev/dsp

MYUSER is your user login.

as "root" add your user to group "audio" and group "users".
$ usermod -G MYUSER,users,audio MYUSER

logout, and login again, now the sound should work.

---

