---
title: "Ubuntu on the Raspberry Pi platform"
date: 2011-11-03
forum: Hardware
---

### Post by Walther -FI- on 2011-11-03
Hello folks,

(First of all, a disclaimer: I am not affiliated with the company behind, this is just out of my personal interest and the possible interest of the community)

I would like to drag some attention onto the RaspberryPi - a new mobile development platform that is actually capable of most of the common desktop computer tasks rather decently with a surprisingly low price tag.

[ http://www.raspberrypi.org ]( http://www.raspberrypi.org )

Based off an ARM processor, knowing that Ubuntu is being developed / ported to the ARM architecture (ready builds of 11.10 exist already), I see a great opportunity to get an affordable, powerful, portable, tiny-wattage computer system for those of us who are monetarily restricted or just want a cool DIY pocket computer.

I would like to know if Ubuntu's ARM version will install on this device and will it be supported by default - or will we be restricted to individual ported and patched versions?

Some of the impressive specs include the capability to run Quake III Arena at 1920x1080 resolution with 4x antialiasing at playable 20fps. At 4W power consumption and with a price tag of 25 USD, who wouldn't want one of these running Ubuntu natively?

(If you ask me, this could be a great opportunity for Canonical too - to buy these 25 USD computers and give them to charity with Ubuntu preinstalled... Or just support the platform when they start giving away the chips for charity, great media coverage for Ubuntu... or something similar. But that's off the topic.)


EDIT:

Apparently there has been support before:

[https://bugs.launchpad.net/ubuntu/+bug/848154](https://bugs.launchpad.net/ubuntu/+bug/848154)

"It was there up til Karmic, then it was pulled. This is a bug, the compilations need to be made for V6 and above, not the latest and greatest and slickest and for ONE DEVICE, Beagleboards." -rec9140

---

### Post by Evil-Ernie on 2011-12-22
I hope it all works out with Ubuntu and Raspberry Pi, I really want to experiment with these little gems but there is still uncertainty if Ubuntu will work on it.

---

### Post by akauppi on 2011-12-24
I'm also hopeful of running Ubuntu on these devices, one day. I've used Fedora enough to know I wouldn't really enjoy it on my own hardware.

There's two clear and well described (in the link above, at Ubuntu Forum) sides to this case. Thanks Canonical for the description of why Raspberry Pi (being ARM V6, not V7 or later) would not be supported. Makes sense. But so does the counter-argument that this really could be the hardware to spread Linux to the masses in the non-western world.

Time will tell.

---

### Post by schurtek on 2012-03-06
I would really like to see a lite version of Ubuntu running on the Raspberry Pi. It truely is a remarkable little device and thus should be embraced by the Ubuntu Forum.

Sadly, I am not going to be running Ubuntu on my Raspberry Pi due to the lack of support, but will be looking to other linux versions. 

I want to build a Media Player that can link into a Media Server. Myth will be my app of choice to start.

---

### Post by freakalad on 2012-07-25
Created a brainstorm ticket: [http://brainstorm.ubuntu.com/idea/29991/](http://brainstorm.ubuntu.com/idea/29991/)

Please add your 2c to get some traction/motivation behind the idea

---

### Post by Beechy on 2012-07-27
Hi Guys,
If we all email  Canonical do you think it will do any good ?
I am most definately going to try :D.
Maybe they have a heart.

---

### Post by SteveDee on 2012-08-16
Why all the fuss about getting Ubuntu onto the RPi?

The RPi is an experimenters single board computer, not a replacement for your laptop.

As an experimenter with 'Buntu experience, you shouldn't have too much trouble finding your way around Debian (with or without the LXDE desktop), installing applications using DEBs as you do on 'Buntu, and tweaking the system.

Hopefully you may even be tempted to write a few lines of code.

---

### Post by Terrum on 2013-01-16
I'm really sorry for bumping an old post but...

If it's not meant to be a replacement for a laptop, then why does the description on many sites for the raspberry pi say: > The Raspberry Pi is a credit-card sized computer board that plugs into a TV and a keyboard. It’s a miniature ARM-based PC which can be used for many of the things that a **_desktop PC does_**, like **_spreadsheets, word-processing and games_**.

A laptop/PC is mainly used for office work and gaming generally. So I'm pretty confused now. I know the Pi is meant to be for experimenting and coding etc, but if descriptions say it's for office work and games too, then why don't OS' like Windows or Ubuntu work on it? Or am I completely misunderstanding the concept here?

---

### Post by SteveDee on 2013-01-17
> **Terrum said:**
> ... why don't OS' like Windows or Ubuntu work on it? Or am I completely misunderstanding the concept here?

I wouldn't want you to buy a Pi thinking its a cheap alternative to your Windows laptop...and then be disappointed.

Its true that the Pi will run the general apps listed. But it only has a 700MHz processor, so it needs a light-weight operating system.

Microsoft Windows 7 is a heavy-weight operating system. Even the old Dell computer I'm writing this on would not run Excel 2010 + Win7. That's just one of the many reasons I'm "here" (on this forum) and running Lubuntu.

Also, the Pi is not an Intel compatible system, so x86 software will not run on it (software must be compiled for the Arm processor).

The original Raspberry Pi concept was to provide a very low cost single board computer for educational purposes. It was not intended to sell in large numbers and make a lot of money for the designers. The design team are part-timers (i.e. almost all of them have full time day-jobs doing something else). The Raspberry Pi foundation is a charity. The 2 companies distributing the Pi are large commercial enterprises.

The software is in a continual state of development (both by the foundation and the open source community) and the system certainly runs a lot faster (and smoother) than it did even just a few months ago. I expect the extra RAM in the new version of the Model B board will also help.

So, is the Pi right for you?

I suggest you do a bit of research before you decide. The real cost of a Pi is the basic quoted cost ($35) + power supply + sd card + keyboard + mouse + video/HDMI cable + shipping + tax. That's assuming you already have a TV or digital monitor that you can use.

Take a look at the forum: [http://www.raspberrypi.org/phpBB3/index.php](http://www.raspberrypi.org/phpBB3/index.php)

You may also be interested in my stalled projects: [http://www.raspberrypi.org/phpBB3/viewtopic.php?f=41&t=25292](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=41&t=25292)

...and this excellent article on the concept: [http://www.zdnet.com/we-thought-wed-sell-1000-the-inside-story-of-the-raspberry-pi-7000009718/](http://www.zdnet.com/we-thought-wed-sell-1000-the-inside-story-of-the-raspberry-pi-7000009718/)

Happy Hacking!

---

### Post by Terrum on 2013-01-17
Appreciate your great and detailed response. Thank you! I however already have a Pi with Debian so I'm happy either way :D I just wanted that cleared up.

---

