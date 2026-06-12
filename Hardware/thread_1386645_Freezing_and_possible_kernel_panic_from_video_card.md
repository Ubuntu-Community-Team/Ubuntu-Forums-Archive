---
title: "Freezing and possible kernel panic from video card"
date: 2010-01-20
forum: Hardware
---

### Post by Codey D. on 2010-01-20
Long story short- I tried Linux mint 8 and the most recent release of ubuntu out on my computer. They work just fine running off my 64mb integrated video card, but after I get the option to download drivers for my nvidia 8400 gs video card, it either freezes before it boots or I get some text on a black screen that keeps flashing. I tried setting the onboard as the main video card in bios, and same with the new card. Am I doing something wrong? Or does ubuntu and linux fail and windows is just destined forever to not be a pain in the hind end?

---

### Post by Codey D. on 2010-01-21
Sooooo, this is the support you get from a support forum? Wow, Windows 7 for the win :/

---

### Post by gear.h34d.2012 on 2010-01-21
Chill dude. A lot of the people here work, go to class, etc. Personally I can't help. I have no experience with Mint. For the time being till more experienced guru's get in here, have you fully utilized your Google-Fu?

---

### Post by azagaros on 2010-01-21
What you experienced may be not related to the nvidia driver.  I noticed the same issue with Fedora on this older laptop with a Ati chip.  It might be an issue with X itself or how the different distributions handle certain handle graphics drivers. Its in the base driver stuff of X not the driver.  

My suggestion, is to try a different distribution and see if the same issue exists.

I wish there were alternatives to windows and linux out there.  Wheres OS/2?? Alas we are stuck until the someone steps up and gets the driver sources open source.  Ati and Nvidia have a nasty habit of being protective of their chip interfaces rather than making things work nicely on non-windows platforms.

---

### Post by Codey D. on 2010-01-21
I tried this on linux  mint 7 and 8, along with Ubuntu (Most recent release, I don't like memorizing version numbers lol)  All gave me the same issue. I install the driver using a pop up window saying proprietary drivers are available. I get the Nvidia drivers and on reboot it freaks out. I reinstalled ubuntu (I like it MUCH more than linux) about 4 times today trying to get the drivers to work. I JUST bought the video card a few weeks ago and I'm not keeping ubuntu if it's not going to work, even though windows is annoying me too. I need my games!

---

### Post by Codey D. on 2010-01-22
Ugh. Screw it. Windows it is. It might have some issues, but at least they're not too major, AND I can easily get answers if I do get an issue. If this is the official support forum, OH GOD..... Ubuntu users, good luck.

---

### Post by Redsandro on 2010-01-22
You need a chillpill. This is no official support forum. Free software has no official support. Have fun chipping in $200 for Windows. Although their 'support forums' suck even more.

Anyway about your issue, it is possible that you bought a broken video card. I have an nVidia FX series that worked fine for a few years, but now it is partially broken.

This means, it works with the open driver because it does not access the low level internal functions of the card. If I install the proprietary driver, Linux freezes on boot. Sometimes I see random text AND noise on screen.

Fun detail: I have the same in Windows unless I install a crappy non-hardware acceleration driver.

It took me some time to figure out that it was my videocard, because I've always been using it with linux.

---

### Post by drworm01 on 2010-01-23
> **Redsandro said:**
> it works with the open driver because it does not access the low level internal functions of the card. If I install the proprietary driver, Linux freezes on boot. Sometimes I see random text AND noise on screen.

This is the situation I've been facing. I have an nVidia 8400M card on my laptop and no problems until 9.10. I reinstalled 9.04 for a variety of reasons, but these video card issues keep arising when I run the proprietary drivers. 9.04 recommends 180, but also offers 173. Both result in versions of the same problem as described in the initial post. I was going to install the latest driver from nVidia itself, but it sounds like my issue is the card. Is there a way I can test that to make sure? Obviously I'd like to avoid having to get a new card and there are a few compositing functions I enjoy that don't run on the open driver.

Thanks for your time.

---

### Post by Codey D. on 2010-01-23
> **Redsandro said:**
> You need a chillpill. This is no official support forum. Free software has no official support. Have fun chipping in $200 for Windows. Although their 'support forums' suck even more.

Anyway about your issue, it is possible that you bought a broken video card. I have an nVidia FX series that worked fine for a few years, but now it is partially broken.

This means, it works with the open driver because it does not access the low level internal functions of the card. If I install the proprietary driver, Linux freezes on boot. Sometimes I see random text AND noise on screen.

Fun detail: I have the same in Windows unless I install a crappy non-hardware acceleration driver.

It took me some time to figure out that it was my videocard, because I've always been using it with linux.
I'm not really sure what you mean by broken. It's only been less than a month since I bought it. And there's no need for me to spend any money on windows- I have a legal copy of both xp and vista. And I get GREAT support for both. I'm not sure what your experiences were with windows, but all the problems I get with it are from user error (AKA I screwed something up and I'm not so full of myself that I blame the OS instead of admitting I screwed up) I guess me and Ubuntu and Linux aren't meant to be. It's a shame. If only more people actually knew a bit more about the OS they use.

---

