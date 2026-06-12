---
title: "LXDE on an old laptop and need tweaks and advice"
date: 2011-05-23
forum: Hardware
---

### Post by vanquishedangel on 2011-05-23
Hi, this thread maybe in the wrong spot and if it is I am sorry but it seemed the most appropriate in my limited search.

My laptop is a Compaq Armada m300 plll 600 mhz, 190 mb ram, ATI 3D rage Lt pro 4mb ram.

It runs great with lubuntu installed, but a little slow. I will use it for school mostly as a word processor but may use it for other things like surfing the net for research topics and other school related things.  I may also use it for surfing instead of my main computer because it is way more efficient energy wise.

The question is how can I make it faster with even less system reasources?

I have found that this laptop works really well with epiphany and dillo for the browsers, I mostly use epiphany on it. I have tried many others but those two are best, chromium takes forever but it is the default install with lubuntu.

So here is what I am looking for advise on other than the above question:

how can I make epiphany even faster?

What are the tweaks I can apply to make the desktop faster in LXDE?(I have disabled the other desktops so I am using just one)

What other office programs do i need that will work well? (I have abiword and gnumeric but I need a power point type etc.)

Any way to speed boot times or program load times?

I couldn't get ubuntu one to work, I would just like to sign in and use it, not have it load on start up, so is there a way?

Can I edit the "other" menu or delete it all together, I don't like it?

I have got a 256mb ram stick on the way and that will be the max this netbook/laptop can handle (320mb). I bought this at a great price and I am typing this thread on it now and it is in really great shape. Any advice anyone has is welcomed and I thank you in advance.

---

### Post by kerry_s on 2011-05-23
you just need the more ram. not really much else you can do, but use the lightest apps you can find, it just so happens the apps you want are heavy apps, no real alternatives.

---

### Post by vanquishedangel on 2011-05-26
Libre office actually works quite well in this lappy, I expected it to be heavier.  for speed ups so far I have disabled ipv6 and turned off antialising. I also used bleachbit and orphan to remove unnecessary junk.

---

### Post by kerry_s on 2011-05-26
> **vanquishedangel said:**
> Libre office actually works quite well in this lappy, I expected it to be heavier.  for speed ups so far I have disabled ipv6 and turned off antialising. I also used bleachbit and orphan to remove unnecessary junk.

Becareful with those, there more for debian, while ubuntu is debian based, there are differences under the hood. ipv6 is already set to ignore by default. antialising not really any saving there.

I spent the last couple of days tweaking mine to be more usable fo me.

---

### Post by vanquishedangel on 2011-05-26
> **kerry_s said:**
> Becareful with those, there more for debian, while ubuntu is debian based, there are differences under the hood. ipv6 is already set to ignore by default. antialising not really any saving there.

I spent the last couple of days tweaking mine to be more usable fo me.

Yeah I have bricked my system with those before lol, but I learned from that.  I also used a guide here that was really helpful

[http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/)

I am also posting this to help others aswell, not all things in this guide were able to be done in lubuntu tho, like for the swappiness and the sysctl.conf one I just added a line to the bottom of the file and made sure there was no # sign in front and it worked great. nice pic btw is that also a low spec comp?

I also installed sdparm, hdparm is a default install on ubuntu systems but sdparm isn't. It is for scsi devices.  Then I used a knoppix rescue cd and resized the partitions to give me a gig swap space, I seen alot of threads about resizing a partition but pretty much everyone said to create a swap file.  I had the disk from years ago and found it and a thread somewhere said that resizing was better than creating a file.

I also edited the /etc/default/grub and took out the "quite splash", to aid in boot times,  I also installed sysv-rc-conf and edited there as well after running sysv-rc-conf in a terminal, careful though, this can be dagerous

---

