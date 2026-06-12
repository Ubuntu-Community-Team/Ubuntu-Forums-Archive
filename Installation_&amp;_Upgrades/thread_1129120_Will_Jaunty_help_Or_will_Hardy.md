---
title: "Will Jaunty help? Or will Hardy?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by redenex on 2009-04-18
Well, I have been having the "no sound issue" with Intrepid for a while now and nothing seems to have helped. Right now I am on Jaunty Beta still no sound. My question to my peers here is, would Jaunty official release next week solve my sound problem? Or would you advice me to roll back (clean install) of Hardy Heron? I am on 64 Bit OS.

I got my new HP TouchSmart a month ago and it has Vista pre-installed. And though uncomfortable, I am forced to use Vista because of the sound issue. At one point I was even thinking of removing Ubuntu completrely and go for another distro.

Confused yes, any guidance?

---

### Post by lemming465 on 2009-04-19
> I have been having the "no sound issue" with Intrepid ... Jaunty Beta still no sound
Bummer.

> would Jaunty official release next week solve my sound problem
Probably not, unfortunately.

> would you advice me to roll back (clean install) of Hardy Heron?]
If that's the last version where all your hardware works, yes.  It will be supported as a desktop OS until 2011.

If you can post more details about the PC, such as the vendor, model number, motherboard, and the output of *lspci -v*, we may be able to offer better troubleshooting advice.

---

### Post by Mark Phelps on 2009-04-20
> **redenex said:**
> Well, I have been having the "no sound issue" with Intrepid for a while now and nothing seems to have helped. Right now I am on Jaunty Beta still no sound. My question to my peers here is, would Jaunty official release next week solve my sound problem? Or would you advice me to roll back (clean install) of Hardy Heron? I am on 64 Bit OS.

Confused yes, any guidance?
What may not be commonly known is that there are at least two Linux projects that have been working on sound drivers/  ALSA is the one commonly known, but OSS (Open Sound System) is another one.  When I install Ubuntu a while back, I too had no sound until I found out about OSS and discovered that they had a driver.

Check the OSS website below:

[http://www.opensound.com/]("http://www.opensound.com/")

---

### Post by apparle on 2009-04-20
Same here...........I also couldn't configure ALSA but OSS did the job for me.......try the site.

Download and see if OSS is working. If yes then you will find many workarounds to make OSS default in the system...
It was same with me an year ago (had almost uninstalled linux) but now I say it's worth the trouble.

---

### Post by redenex on 2009-04-23
> **lemming465 said:**
> 
If that's the last version where all your hardware works, yes.  It will be supported as a desktop OS until 2011.

If you can post more details about the PC, such as the vendor, model number, motherboard, and the output of *lspci -v*, we may be able to offer better troubleshooting advice.

Ironically I got this laptop just 4 weeks ago. Earlier I had my desktop, and everything was working fine (I was last on Intrepid 32 bit), right now on Jaunty 64 bit (release candidate). Anxiously waiting for another few hours when I can download and have a clean install.

---

### Post by redenex on 2009-04-23
> **Mark Phelps said:**
> What may not be commonly known is that there are at least two Linux projects that have been working on sound drivers/  ALSA is the one commonly known, but OSS (Open Sound System) is another one.  When I install Ubuntu a while back, I too had no sound until I found out about OSS and discovered that they had a driver.

Check the OSS website below:

[http://www.opensound.com/]("http://www.opensound.com/")

I have gone through almost all the "sound issues" discussions here, did everything I could. My problem was that, when I log in and try to play a song, it plays for about 3-4 seconds before the sound dies out.

I will try OSS and see what I can come up with, thank you.

---

