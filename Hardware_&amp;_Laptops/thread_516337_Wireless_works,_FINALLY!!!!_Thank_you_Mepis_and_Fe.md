---
title: "Wireless works, FINALLY!!!! Thank you Mepis and Feisty Fawn!!!"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by seismicmike on 2007-08-03
I hacked Mepis to make Feisty work!

I really really really liked Mepis b/c my wireless worked, but it had outdated software, and wouldn't let me upgrade on the feisty repositories... grrrr... and I really wanted ubuntu Christian Edition for the DansGuardian and the e-Sword and all that....

SOOO.... I just decided to force wireless to work in ubuntu feisty fawn. If you're at your wits end here's some things you can try.

Install SimplyMEPIS 32 linux on your computer, and decide whether you like it or not. I like it but I knew Ubuntu with working wireless would be the perfect fit for me, so I wasn't quite comfortable with Mepis. Anyway, it serves it's purpose. Here's what you need to do:

Use a thumb drive and save the entire contents of the /etc/apt folder onto your thumb drive.

Install Ubuntu... It's ok to overwrite Mepis, you don't really need it any more.

Copy the stuff from Mepis off of your thumb drive into your home folder. So for me it's now in /home/seismicmike/from\ Mepis/

Open synaptic and click Settings>Repositories. Go to the authentication tab and click "Import Key" down at the bottom. Navigate to the folder from Mepis in your home drive and double click on the file called "trusted.gpg"

Then gksudo open your /etc/apt/sources.list file and the sources.list file from Mepis side by side on your desktop. In the one from Mepis, copy the two lines of Mepis repositories and paste them into the /etc/apt/sources.list file.

Close synaptic and open it back up. Reload repositories if necessary and you should see all the packages from Mepis. I installed the following packages & their dependencies:

mepis-network-6.0
bcm43xx-firmware
knetworkmanager
ndiswrapper-utils1.9
ndiswrapper-source
ndiswrapper-common
wlassistant

If in the installation process it asks you about replacing files (such as /etc/network/interfaces) say "Yes" (you actually click "Replace").

Reboot.

Go System>Preferences>Main Menu and navigate to the Applications>Internet>Wireless Assistant entry. Right click and select "properties". On the line that says "command:" it will say "wlassistant" add "gksudo" before it so it now says "gksudo wlassistant". 

Reboot or log out and log back in.

Now every time you boot up you have to run wireless assistant either by going to in through the menus (Applications>Internet>Wireless Assistant), typing the command directly into terminal, creating a shortcut on the menu bar, or by configuring it to run automatically when ubuntu loads up. At any rate, once it's loaded, it'll search for available networks an show them to you. You select one and it'll connect. The first time you connect to each network you have to tell it whether it's static IP or DHCP and provide the WEP/WPA key if applicable and then voila, enjoy wireless!

There's no guarantees that this will work. There have been other things that have worked for other people that haven't worked for me. This is just what worked for me. If it works for you, let me know. If not, then I sincerely hope you find something that does. I'm really sorry I couldn't. Really. I feel your pain. Seriously!

Oh btw... Sound works too, in case anyone was wondering. All I had to do was open up the sound mixer and go to Edit>Preferences, select External Amplifier and OK, then go to that tab and untoggle External Amplifier and sound worked.

I finally have the ubuntu distribution that I've always wanted.

THANK YOU FEISTY AND MEPIS!!! KEEP THE GOOD TIMES ROLLING!!!!

---

### Post by seismicmike on 2007-08-03
By the way, for the record......

1) If anyone encounters problems or has questions, ask them. I may not be able to give you and answer, but if it's a simple matter of omission - like accidentally forgetting to tell you to copy one file or something, I'd be happy to correct my error.

2) It should be obvious, but just in case.... While you're doing the install of Ubuntu and using synaptic to download/install the sweet packages that made my wireless work... you're going to need a physicaly eth0 connection to do all that.. u know... b/c you're wireless doesn't work yet... if it does, WHY ARE YOU DOING THIS??? :tongue: :lolflag:

---

### Post by Azoix on 2007-08-03
> **seismicmike said:**
> By the way, for the record......

1) If anyone encounters problems or has questions, ask them. I may not be able to give you and answer, but if it's a simple matter of omission - like accidentally forgetting to tell you to copy one file or something, I'd be happy to correct my error.

2) It should be obvious, but just in case.... While you're doing the install of Ubuntu and using synaptic to download/install the sweet packages that made my wireless work... you're going to need a physicaly eth0 connection to do all that.. u know... b/c you're wireless doesn't work yet... if it does, WHY ARE YOU DOING THIS??? :tongue: :lolflag:

Having read the above, i would suggest you add one or two things, can you add the type of wireless adaptor used, the make and model of pc, and anything else hardware related , so other's with similar hardware may benefit from your workaround.
Also do you mind if i copy and insert this in my list of workarounds and shortcuts i'm preparing as a guide for hopeless NOOB's like me ?

---

### Post by seismicmike on 2007-08-03
Yeah yeah... Sorry. I kinda assumed anyone reading this would have connected it with my previous impassioned pleas for help, but good point.

I run a Gateway m320s laptop with a built in Broadcom Corporation BCM4306 802.11b/g Wireless card. I also have one of those Air Force One cards from Belkin that I never have made work. I don't even mess with it now though b/c I have the built in one working.

As far as copying it, go right ahead! If this gets out there and helps other poor saps like me, then I'll be even happier!

---

### Post by pbcartwright on 2007-08-03
so, did you get the CE Christian edition working?? Did you just install ubuntu then add the extra software?

---

### Post by stchman on 2007-08-03
I recommend anyone with a Broadcom card that they get an Intel 3945 wireless card.  They can be had for around $25 new on ebay.

Until Broadcom starts fully supporting Linux I will botcott them.  Intel or Atheros are the only wireless cards I will use.

---

### Post by seismicmike on 2007-09-10
Actually, pb, I've run this configuration on a fresh install of both straight up feisty and CE and it's worked in both cases.

---

### Post by meindian523 on 2007-09-10
Please help others.

Refer this thread:
[URL="http://ubuntuforums.org/showthread.php?p=3340200#post3340200"]
http://ubuntuforums.org/showthread.php?p=3340200#post3340200[/URL]

---

