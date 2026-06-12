---
title: "Über noob question about ati 200m xpress"
date: 2008-10-15
forum: Hardware
---

### Post by Chaize on 2008-10-15
Hi everybody!

Okay im am the biggest Linux noob ever. But nontheless ive managed to get my wifi working and my ati 200m. ALmost! Because when i activate the driver from hardware drivers, i get: laggy video (even worse when i full screen), scrolling in Firefox and other places is a joke, meaning very sluggish and unresponsive, and xMAME games and ZSNES games blink in openGL mode and sound is crappy.

Now ive search and read around on the net, and my initial conclusion is, that the current driver for ati express 200m and other ati cards, is heavily bugged and the "only" thing to do is wait for new release. The alternative way is turning off the driver and restarting. But then theres no compiz or desktop effects = no fun and Windows like...

So my plea for you guys is; Is there any way, any way, to rool back the driver or install a different one, so that video and scrolling etc. will be back to snuff?

Im running Ubuntu 8.04 Hardy on: Acer Travelmate 2440 p4 1.5 2g ram and ati radeon express 200m

Thanks in advance! And i am super noob and understand very little of programming and the likes, so please, if you can answer in the most idiot freindly way it would be greatly appreciated.

---

### Post by markginter24 on 2008-10-15
I would honestly suggest just waiting for Ibex.  I'm running an updated-every-day Ibex on an HP Pavilion with the Xpress200M chipset.  The real issue is not the driver - it's the version of Mesa.  If you disable using the fglrx driver (I assume that's the one you 'enabled') and then enable backports -- you can see if the 7.1 (I believe) version of Mesa has been backported.  That's the first version of Mesa that allowed the 3d stuff of the Xpress200M to properly work.

---

### Post by ideefixe on 2008-10-15
The best idea is to wait for the next release as markginter24 suggested.

If you really want it in hardy, you can try to install (experimental) updated opensource driver:
add the following line to your /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/stikonas/ubuntu](http://ppa.launchpad.net/stikonas/ubuntu) hardy main

And then check & install updates.

---

### Post by Chaize on 2008-10-16
Okay guys, thanks for the answers

I think im just gonna wait then, i can live with it until then

---

### Post by Chaize on 2008-11-23
Hey guys!

Okay, so now the updates here and i just dl'ed Ubuntu 8.10. Sound working, wireless working, but guess what?
No graphics drivers working!
In Hardware drivers I get, under my "ATI/AMD proprirtary FGLRX graphics driver" a green light after enabelling it. But the text in front of the graphic representation reads; "This driver i activated but not currently in use"

So how do i make come in use? I am, as stated above, a complete noob at Linux, and understand very little. I googled around and havent found any answers. So please help me!!

Best regards

---

### Post by Chaize on 2008-11-24
Hey Guys, again!!!

Now ive got everything working great. But guess what? Laggy scrolling og laggy video is back as in 8.04...

So is it me doing something wrong, or am i just doomed with having the ATI card in my comp?

Please help and answer.

best regards

---

### Post by zombiepig on 2008-11-24
You shouldn't have to use the proprietary fglrx driver (the one under hardware drivers) for compiz to work with ati x200m using intrepid. My wife's laptop has one of those cards, and using the default open source drivers compiz, video playback and firefox scrolling all works nicely. Well, as nice as you'd expect from the very weak x200m hardware :P

My advise is to avoid ati's driver and stick with intrepid's built in driver.

---

### Post by Chaize on 2008-11-24
Hi zombiepig!

Thanks for the reply, ill uninstall thoose drivers then. But where can i find some help to install the open source drivers then?
Cant really find anything on it

Best regards

---

### Post by zombiepig on 2008-11-24
If you remove the ati driver from hardware drivers, ubuntu should fall back to using the open source driver. You'll know it's all working if you can enable visual effects under system->preferences->appearance :)

---

