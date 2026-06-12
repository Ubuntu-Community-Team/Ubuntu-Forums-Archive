---
title: "Toshiba Satellite T215D-S1150RD"
date: 2010-12-28
forum: Hardware
---

### Post by SkylinesSuck on 2010-12-28
Fresh copy of 64 bit 10.4 installed dual boot with Win 7.  Proprietary ATI/AMD FGLRX drivers up and running.  I can't seem to get smooth 1080p playback (tried about 6-7 different movies.)  Everybody says this netbook has the horsepower to play them with out too much trouble.  It's a dual core AMD K325 with a ATI HD 4225 GPU.  They play smoothly in Win 7, but not Ubuntu.  Any ideas?  If I can get this working I can yank Windows 7 from the machine all together :D

---

### Post by SkylinesSuck on 2010-12-28
[http://ubuntuforums.org/showthread.php?t=1389943&highlight=smooth+1080p+playback](http://ubuntuforums.org/showthread.php?t=1389943&highlight=smooth+1080p+playback)

Maybe?

---

### Post by SkylinesSuck on 2010-12-29
Okay, from the thread I linked above...........

> **VertexPusher said:**
> Have you installed the ATI display driver (fglrx)?

Have you disabled Compiz (i.e. desktop effects)?

Have you enabled XVideo hardware overlay? This is required for smooth  video playback without tearing. When I had ATI graphics a while ago,  XVideo had to be enabled manually in the driver by running "sudo  aticonfig --ovt Xv" at least once. This may also be the reason why  MPlayer does not work at all. See the driver's README file for details.

As far as I know (ATI users correct me please) there is currently no  hardware acceleration for H.264 playback available with ATI cards on  Linux. Right now it works only with Nvidia. Your CPU should be able to  decode 720p H.264, but 1080p may continue to be a problem.

If you consider switching to Linux, you'll definitely want Nvidia graphics.

> **VertexPusher said:**
> run "sudo aticonfig --initial" first, then "sudo aticonfig --ovt Xv". Then reboot.

> **VertexPusher said:**
> aticonfig seems to be confused because the  fglrx device section already exists. Delete xorg.conf (but keep a backup  copy), then run the two commands again.


So I did all of this and got it to say something about Xv is being used (in terminal) and rebooted.  Still "rips" the screen and/or plays jerky.  Any inputs?  Like I said, this thing plays the same movies fine in Win 7.

---

