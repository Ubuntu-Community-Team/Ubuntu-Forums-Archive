---
title: "Hardy + Nvidia GeForce 6800GT = GLITCHTASTIC"
date: 2009-01-15
forum: Hardware
---

### Post by sarith on 2009-01-15
Hey all,

First off, I'm definitely somewhat of a n00b so my sincerest apologies in advance for any ignorance.

So I'm setting up my old PC to be an Ubuntu + [XBMC]("http://xbmc.org") based HTPC.  I successfully installed Ubuntu 8.04.1 (Hardy) -- everything was pretty much a breeze.

It was obvious that I needed to install the drivers for my video card -- an Nvidia Geforce 6800GT (PCI-E) -- but I just cannot get it working correctly.  

First, I enabled the restricted drivers through the "Hardware Drivers" panel.  I restarted and logged back in.  Basically what I see is artifacts all over the screen and, more prevalently, redraw problems.  It's very hard to describe how insane and glitchy all the graphics look, but everything is just breaking up at sharp angles.  Text is illegible unless I drag the window around until it cleans itself up off screen and I drag it back on.  It's a mess. I've attached a picture of it. 
[IMG]http://ohmatic.com/sarith/hardy.jpg[/IMG]

So, I disabled the drivers through the Hardware Drivers panel and restarted.  Next step was to try Envyng.  Installed the drivers through there, and on restart saw the NVIDIA screen at boot (cool!).  Logging back in -- and SAME graphics issues.  Uninstall via Envy.

Everytime I uninstall the drivers, everything works fine -- but it's on generic settings, no hardware acceleration (which I need since I'll be watching HD video eventually).

Next up, I tried the drivers from the Nvidia website. Downloaded the shell script, killed gdm, ran the installer from terminal, everything went fine, restarted.  Now it's weird again, on logging in I get this guys's exact same problem: [http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html]("http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html")

And just selecting whatever default options the dialog has in there, and actually logging in, I'm getting the same glitchy problems as before.  Ran the shell script again, this time --uninstall.

So I'm totally stuck here, can't seem the get any drivers working.  Thank you so much in advance for any all aid.

Here's my relevant system specs:

OS: Ubuntu Hardy Heron (8.04.1) 32-bit
Motherboard: MSI K8N Neo4 Platinum/SLI
Processor: AMD Athlon64 3500+
Video Card: Nvidia GeForce 6800GT (PCI-Express)

---

### Post by soulmatic09 on 2009-01-15
> **sarith said:**
> 

Next up, I tried the drivers from the Nvidia website. Downloaded the shell script, killed gdm, ran the installer from terminal, everything went fine, restarted.  Now it's weird again, on logging in I get this guys's exact same problem: [http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html]("http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html")


So I'm totally stuck here, can't seem the get any drivers working.



I had the same problem. not only that, I could never change to the nvidia driver, all that showed up was the vesa driver which gave me a low resolution screen. i couldn't see my emerald themes, or get the right resolution on my flat panel monitor, either.

I checked my xorg.conf file, and it was defaulting to the nv driver, which didn't make any sense either.

BUT

i got it to work by doing this:

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

apparently, there is a bug with the restricted drivers manager.

by doing this, i got the proprietary nvidia video card driver to work, but now i can't  watch streaming .asf files. :(

---

### Post by sarith on 2009-01-15
Thanks for the reply. I'm definitely going to give it a try right now and i'll post back if I get it working.

> **soulmatic09 said:**
> 
by doing this, i got the proprietary nvidia video card driver to work, but now i can't  watch streaming .asf files. :(

That's pretty strange... is it only .asf's streaming from the web? or any .asf at all?  I can't imagine that this problem has anything to do with your video driver .. are your other video formats playing correctly? I'm concerned because as I said earlier I'm using this machine primarily as a media center..

S

---

### Post by sarith on 2009-01-15
So unfortunately that didn't work -- still getting all the glitchy-ness.

What version of the drivers from Nvidia are you using?

If I uninstall the drivers and re-install a much older version via Envy, no more glitches (but also no hardware acceleration)..

I just need to be able to playback HD video... ARGGH!

---

### Post by soulmatic09 on 2009-01-17
> **sarith said:**
> Thanks for the reply. I'm definitely going to give it a try right now and i'll post back if I get it working.



That's pretty strange... is it only .asf's streaming from the web? or any .asf at all?  I can't imagine that this problem has anything to do with your video driver .. are your other video formats playing correctly? I'm concerned because as I said earlier I'm using this machine primarily as a media center..

S

I'm using the very latest driver. I can play regular asf files off my hard drive, but I can only get audio from a live video stream. Flash video works fine though. 

Good luck using this as a media center, media is this OS's weak point IMHO. Media in ubuntu drives me nuts.

---

### Post by sarith on 2009-01-18
> **soulmatic09 said:**
> I'm using the very latest driver. I can play regular asf files off my hard drive, but I can only get audio from a live video stream. Flash video works fine though. 

Good luck using this as a media center, media is this OS's weak point IMHO. Media in ubuntu drives me nuts.

i really gave it a shot... but i just switched to opensuse.  out of the box, everything worked beautifully.

as a side-note: the artifacting i was getting, i think had more to do with my card overheating than any driver issues.  i ripped my card out and toothbrushed off at least a quarter-inch layer of dust from the fan grill. eek!

---

