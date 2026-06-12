---
title: "Acer Aspire 5520"
date: 2008-07-26
forum: Hardware
---

### Post by Mohammed Abbas on 2008-07-26
Hello,

Lately I'm considering buying an Acer Aspire 5520 laptop .. that comes with AMD processor and Nvidia video chip 7000 .. and I need to know how ubuntu (the latest 8.04 LTS release ) is gonna work under it .. so if you guys know what kind of problems and how to fix them, please tell me ..

Thanks

---

### Post by Mohammed Abbas on 2008-07-26
Any help !

---

### Post by ModelM on 2008-07-26
I have Ubuntu 8.04.1 running on one of these. It works great, imo. I'm using the Nvidia video driver & ndiswrapper for the Atheros wireless and all of that works as it should. I'm not sure if suspend works properly because I don't use suspend. The sound, ethernet, built-in card reader, touchpad, all work fine.

Even the built-in modem works using the drivers from the Dell website (one for the modem & one for the sound card).

The keyboard has a couple of special purpose buttons which do foo-foo stuff under windows like bring up a web browser with one touch. I could not care less about these special buttons & so have not tried to get them to do anything.

The CPU throttling seems to work properly out-of-the-box, dropping the cores to about half speed at idle, cranking them up during load & immediately dropping the clock speed back down again. 

My machine is a 5520-5912 and I'm very happy with Ubuntu on it.

---

### Post by Mohammed Abbas on 2008-07-26
> **ModelM said:**
> I have Ubuntu 8.04.1 running on one of these. It works great, imo. I'm using the Nvidia video driver & ndiswrapper for the Atheros wireless and all of that works as it should. I'm not sure if suspend works properly because I don't use suspend. The sound, ethernet, built-in card reader, touchpad, all work fine.

Even the built-in modem works using the drivers from the Dell website (one for the modem & one for the sound card).

The keyboard has a couple of special purpose buttons which do foo-foo stuff under windows like bring up a web browser with one touch. I could not care less about these special buttons & so have not tried to get them to do anything.

The CPU throttling seems to work properly out-of-the-box, dropping the cores to about half speed at idle, cranking them up during load & immediately dropping the clock speed back down again. 

My machine is a 5520-5912 and I'm very happy with Ubuntu on it.
That's so much help! .. Thank you :)

---

### Post by ModelM on 2008-07-26
I don't know how important the built-in modem is to you, but I wanted to clarify something I said.

The sound works out-of-the box. Sound, the volume control wheel on the side, all works fine.

The built-in modem is integrated with the sound card, as is the norm these days. Installing the modem driver from the Dell website makes the modem work (quite well, in fact), but kills the sound. There is then another driver (or driver patch) to install which restores the sound.

I don't know the URL off the top of my head but both of these are on the Dell website, as Debian packages which install with a simple double-click of the mouse (or touchpad). These are compiled during the install so the Kernel headers & build-essentials must be installed, also.

All the same, I'd recommend just buying a nice hardware USB modem & just using that. I have a USR 5637 & it works with no fuss at all. Simply plug the modem into a USB port, point wvdial (or whatever dialer you use) to /dev/ttyACM0 and you're in business.

---

### Post by Mohammed Abbas on 2008-07-26
> **ModelM said:**
> I don't know how important the built-in modem is to you, but I wanted to clarify something I said.

The sound works out-of-the box. Sound, the volume control wheel on the side, all works fine.

The built-in modem is integrated with the sound card, as is the norm these days. Installing the modem driver from the Dell website makes the modem work (quite well, in fact), but kills the sound. There is then another driver (or driver patch) to install which restores the sound.

I don't know the URL off the top of my head but both of these are on the Dell website, as Debian packages which install with a simple double-click of the mouse (or touchpad).

All the same, I'd recommend just buying a nice hardware USB modem & just using that. I have a USR 5637 & it works with no fuss at all. Simply plug the modem into a USB port, point wvdial (or whatever dialer you use) to /dev/ttyACM0 and you're in business.
I don't care much about modem because I access the Internet through my LAN or an available WiFi spot .. I also can't get it activated on my PC so I kinda gave up on the idea behind that device .. 

Thanks once again.

---

### Post by david79 on 2008-07-27
I got one of these about a month ago and installed Xubuntu 8.04.

As with the other poster all the important stuff seems to work fine
and I'm very happy, in addtion,

I've had the built in webcam working with something called "cheese" it lets you take video clips and snapshots, I haven't tried video messenging with it. 

I've been using suspend and hibernate without any issues so far. 

Battery monitor reports 1hour 35minutes of life when charged to 100%.

---

### Post by Mohammed Abbas on 2008-07-27
> **david79 said:**
> I got one of these about a month ago and installed Xubuntu 8.04.

As with the other poster all the important stuff seems to work fine
and I'm very happy, in addtion,

I've had the built in webcam working with something called "cheese" it lets you take video clips and snapshots, I haven't tried video messenging with it. 

I've been using suspend and hibernate without any issues so far. 

Battery monitor reports 1hour 35minutes of life when charged to 100%.
Thanks for sharing your experience .. I think I'm gonna have it some time this week hopefully .. but ,just a thought, which distro you think should be running on this laptop in terms of performance ? because I want to try KDE 4 out and I'm just a satisfied GNOME user ..

Kind regards

---

### Post by david79 on 2008-07-28
> **Mohammed Abbas said:**
> Thanks for sharing your experience .. I think I'm gonna have it some time this week hopefully .. but ,just a thought, which distro you think should be running on this laptop in terms of performance ? because I want to try KDE 4 out and I'm just a satisfied GNOME user ..

Kind regards
I haven't tried any of the other distros on this machine but I can report Xubuntu runs very nicely, I only choose it because I've been playing around running ubuntu in vmware and virtualbox on other machines and out the 3 (kde,gnome,xfce) it seemed to be the quickest in terms of gui responsiveness and I liked its simplicity, I may give gnome a try at some point but for the moment I'm just sticking with the one I know and like best. 

good luck,

---

### Post by jesqueda on 2008-09-16
hey could you tell me where I can get that driver for the modem. Is that on dell.com?

---

### Post by ModelM on 2008-09-17
You'll need the kernel headers & build-essential packages installed in order to install these packages.

The modem driver is [_here](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/)_.

The patch to restore the sound is [_here](http://www.linuxant.com/alsa-driver)_.

These worked for me some months ago but there have been kernel updates since I stopped using the modem. I have abandoned the internal modem in favor of a USR5637. In other words, I think these will work for you but I can't be sure.

Good luck.

---

### Post by whatme33 on 2010-04-07
> **ModelM said:**
> I don't know how important the built-in modem is to you, but I wanted to clarify something I said.

The sound works out-of-the box. Sound, the volume control wheel on the side, all works fine.

The built-in modem is integrated with the sound card, as is the norm these days. Installing the modem driver from the Dell website makes the modem work (quite well, in fact), but kills the sound. There is then another driver (or driver patch) to install which restores the sound.

I don't know the URL off the top of my head but both of these are on the Dell website, as Debian packages which install with a simple double-click of the mouse (or touchpad). These are compiled during the install so the Kernel headers & build-essentials must be installed, also.

All the same, I'd recommend just buying a nice hardware USB modem & just using that. I have a USR 5637 & it works with no fuss at all. Simply plug the modem into a USB port, point wvdial (or whatever dialer you use) to /dev/ttyACM0 and you're in business.
I have a USR 5637 too and can't get it to work. It powers up and data blinks too on start. Any ideas?
Thanks Ken

---

### Post by ModelM on 2010-04-07
Have a look at [_this thread_](http://ubuntuforums.org/showthread.php?t=1056659) or [_this one_](http://ubuntuforums.org/showthread.php?t=873268).

---

### Post by andradelipe on 2010-05-14
New  year, new ubuntu release, same old problems... 

nVidia again, don't work property!

no screen resolution, no openGL... 

alway, always the same problem in every ubuntu release that I put here.

Isn't fair.. =/

---

