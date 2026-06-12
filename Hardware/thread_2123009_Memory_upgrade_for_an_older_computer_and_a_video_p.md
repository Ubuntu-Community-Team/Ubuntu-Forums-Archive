---
title: "Memory upgrade for an older computer and a video problem"
date: 2013-03-06
forum: Hardware
---

### Post by johnu1960 on 2013-03-06
Hi.  

I have a computer that my friend was throwing out since she got a new one from work.  I am a long time Windows user, but I thought I'd give Linux a try  as a hobby using this computer.  Everything is basically working fine with Ubuntu 12.10 installed.  The only problem I have is that the login screen displays the message "Input Not Supported" on a small screen that bounces around within the big screen.  Once I log in the little screen goes away.  The computer is an HP Compaq Presario SR5030NX with an Acer monitor.  

The computer has 1.5 GB of memory and I'd like to upgrade it to 2GB.   The lowest price quote I got was for $15 from a website called memorystock.com.  Does anyone have experience with this company?  I am just a little uncomfortable using a company I stumbled across through Google, so I wanted to know if they are legitimate.  Thanks.  

Other than the minor login hicup mentioned above I'm loving Ubuntu! :) I have been at it about 2 weeks and have already loaded lots of apps.  I hope to some day ditch Windows at home.

---

### Post by Kixtosh on 2013-03-06
Is this your model?

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00874655&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_caen_c-001_title_r0004#N296](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00874655&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_caen_c-001_title_r0004#N296)

It would seem to have two slots, but with the existing memory you describe, both are occupied already, so to get 2GB, you need to add 2 x 1GB and sell the existing ones on eBay or something. In any case, for dual channel, identical DIMM pairs are recommended. In that case, the memorystock.com solution seems acceptable, but not any cheaper than a $30 solution from anyone else (for 2 x 1 GB), and they may be offering a different speed than your current modules. Have you opened up the case to see what is already installed yet? It's usually very simple to do, but disconnect your power cord first.

I would not think that the difference between 1.5GB and 2.0GB would be very noticeable in any case. It's probably worth doing on an old machine, and I'd probably do the upgrade myself with the same machine, but the first thing I would do is check if I'm using much swap memory or not. Check the System Monitor utility for that. I don't think it will solve your quirky behavior (which I cannot explain, unfortunately), and that is what would bug me most. Solve that, and maybe then decide if the machine is worth the extra $30 investment.

Worthy of note also is that for a similar investment, you could probably upgrade the hard drive to a 30GB solid state drive (check for offers under $50), for just the O.S., and keep your existing mechanical hard drive as a slave for extra storage of documents. It is likely to yield much more spectacular results than the extra 512MB of RAM, especially in boot and halt times, as well as speed of opening applications. Once again, though, I would want to solve the quirky behavior first.

---

### Post by legion05 on 2013-03-06
Thinking one thing might be the wrong driver for the lame ass acer monitor. Goto system, additional drivers and let it scan what you have for a monitor and video card. It should suggest the most recent driver to load

---

### Post by DuckHook on 2013-03-07
I work with lots of old boxes and find that it's generally not worth investing further money in them. Replacing memory will only show up further bottlenecks elsewhere. A much better option is installing a lighter weight flavour of 'buntu or a different distro altogether. In your case, I would recommend Lubuntu. The 2-D aspect of the Lubuntu desktop will work nicely with your older video card, and Lubuntu will work with system RAM as low as 512 MB, so you will have plenty of headroom. Xubuntu is also a reasonable choice. If you want to really minimize resource usage, try bodhi or Crunchbang.

Floating window might be your monitor complaining that Ubuntu login is trying to draw with monitor settings that are out of your Acer's range.

---

### Post by johnu1960 on 2013-03-15
Thanks for all the advice.  It didn't occur to me to look into a solid state drive.  Based on the responses it doesn't seem worthwhile to upgrade the ram, but I enjoyed researching the solid state drives.  If anything I will probably get one of those and try it out.   Appreciate the advice.

---

### Post by Kixtosh on 2013-03-15
Thanks for the update johnu1960.

In your shoes, if that is your machine in the link I posted earlier, I would try the latest Long Term Support version of Ubuntu, which is Precise Pangolin 12.04 LTS. It is supported until April of 2017, and you just might find that your graphics will behave differently (the bouncing box error message), and you'll also have the option to use Unity 2D, which is probably far better suited on older hardware like that anyway. All you have to do is log out of your session, and choose Unity 2D from the options available before logging back in, but Unity 2D was removed from the 12.10 release and later. If the LTS release improves your performance, then once you've got used to it after six months or so, you can still decide if you want to dive into some troubleshooting for newer releases, but I don't really think Unity 3D is ever going to be ideal on that machine.

In terms of performance from a SSD, using Precise Pangolin 12.04 and the Unity 2D desktop, I would expect your machine to boot in about thirty seconds, and to halt in about five seconds. Firefox should open in just one or two seconds. Solid state hard drives of 64MB and less are well under $100 now, if you search carefully. Smallish drives with just 30MB will be far more than you need for running Ubuntu (10MB is plenty for the system, standard applications, and swap memory). My guess is that it's taking that machine close to one minute to boot up currently, and maybe as much as twenty seconds to shut down.

---

### Post by johnu1960 on 2013-03-18
Kixtosh,

Thanks for the info.  Yes the computer you provided the link for is my computer.  I now have things running pretty well with unubtu and downloaded **tons** of software.  So I think I'll keep it this way and spend time learing software instead of installing other versions of ubuntu.  If I do a reinstall at some point I'll keep your advice in mind.  Before installing Linux, this computer had MS Vista on it.  What a difference!  It is far faster in every way now.  :)

---

