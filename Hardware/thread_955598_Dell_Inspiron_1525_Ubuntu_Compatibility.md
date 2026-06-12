---
title: "Dell Inspiron 1525 Ubuntu Compatibility"
date: 2008-10-22
forum: Hardware
---

### Post by jwhal on 2008-10-22
Hi there. I am thinking of buying a Dell Inspiron 1525. Here are the specs:
Processor Intel® Core™ 2 Duo T5800 (2.0GHz/800Mhz FSB/2MB cache) 
Operating System Genuine Windows Vista® Home Premium Edition SP1 - English 
System Color and LCD cover Pattern Jet Black 
Memory 3GB Shared Dual Channel DDR2 at 667MHz 
LCD Panel Glossy, widescreen 15.4 inch display (1280x800) 
Video Card Intel® Graphics Media Accelerator X3100 
Label Windows Vista™ Premium 
Hard Drive 250GB SATA Hard Drive (5400RPM) 
Network Integrated 10/100 Network Card 
Modem Integrated Modem 
Adobe Software Adobe® Acrobat® Reader 8.1 
Optical Drive 8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability 
Sound Card High Definition Audio 2.0 
Wireless Networking Cards Dell Wireless 1395 802.11g Mini-Card 
Integrated Webcam Integrated 2.0M Pixel Webcam 

I'm curious to know if either Hardy or Intrepid will play nice with this system? 

I'm going with this system because of a) the price, b) the fact that I don't think Dell Canada sells pre-installed Ubuntu lappys. If I'm wrong, please correct me.

Any thoughts?

Thanks,

Jon

---

### Post by phidia on 2008-10-22
If this > Wireless Networking Cards Dell Wireless 1395 802.11g Mini-Card is really an intel wireless card and I think it might be then you should be good to go with that system.

Actually for laptops going all intel makes sense for getting suspend and everything working together correctly.

---

### Post by strixy on 2009-01-30
That's the system I'm running Intrepid on right now (8.10) and wow, am I ever happy. 8.10 works out of the box.

Dell Canada doesn't ship with Ubuntu pre-installed, or they didn't when I got mine 4 months ago. I had to buy the Vista version and install Ubuntu myself (easy). I actually picked mine up at Staples on sale for $400.

8.04 required a couple of hours of hacking to get wireless and sound to work, (Check the dell linux wiki to find the dell specific PPA's to get the drivers).

8.10 has 1 huge issue, but it's easily solved. Hardware monitoring  is not installed by default. So you might notice your laptop shuts down after about 3-5 minutes. It overheats. Search Synapic for inspiron and you'll find the i8k packages and GKrellM. It still runs a little hot, but at least the fans kick in before it shuts down.

In Ubuntu, sound is a little quiet compared to windows and the volume touch keys need to be tweaked, somehow... I haven't figured that out yet. Overall, I would go with Interpid over Hardy. Kubuntu 8.10 runs as well, but I can't get behind the new KDE4

I've also noticed that getting wireless to work with this laptop under other distributions (I've tried Fedora, Suse, Debian, Mepis and CentOS) is a huge PITA.

I'm running dual boot with Vista, no problem.(If I can use Vista and 'no problem' in the same sentence).

Bluetooth works under both Hardy and intrepid, if your cell phone supports OBEX. Getting a BT headset to work is almost impossible though.

Wireless on this box is pretty good. I can connect two blocks away.

Any other questions? I've subscribed to this post.

---

### Post by Yasho on 2009-02-01
Thanks a lot guys. I too run a Dell inspiron 2GB ram, dual core. I had similar problems with Fedora about getting the wireless network running. I had to pull the wire from the LAN card of my desktop and after plugging in the net on the LAN card on my laptop, managed to find the right drivers to get it up. but still, a PITA, as you put it. I've switched back to Ubuntu 8.10 and quite happy. Only, like you suggest I will try to get the fan working and am still trying to work out how to get the sound card to give me some sound !!!

Thanks a lot

---

### Post by tomaasj on 2009-02-10
Like to share my experience with Inspiron 1525.

Bought an Inspiron 1525, 3 weeks ago, for my parents.  Removed preinstalled Vista home edition and installed Hardy (no dual boot).  Thought I would get problems with wireless, as happened on my Inspiron 6400 previously.  This time everything worked immediately after installing 8.04: wireless, sound all OK.  Maybe, the brightness control panel does not allow as many brightness "settings" as on my 6400 laptop.

My parents are not the youngest (70 plus), but seem to have no problems sofar to access internet and to use the OS on a daily basis.

My mother was able to crash the system once (which I found impressive).  But after I disabled the clickable touchpad, she is not able to inadvertedly activate all the buttons on the screen and popping up windows etc.  No freezes up till now.

They are happy with it and so am I.

A disadvantage of the 1525 is the location of the speakers.  They are located above the keyboard.  This in contrast to the Inspiron 6400, which has them located up front so closing the laptop does not affect the sound.  The 6400 laptop has a much richer sound as well.  I should have realized this before buying the Inspirion 1525, but other than that, the laptop works very well with 8.04.

Maybe this information could be helpfull to those considering getting an Inspiron 1525.

Tomaasj[LEFT][/LEFT]

---

