---
title: "Random Total Freezes/Lock-Ups"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by wyth on 2007-12-11
I've been searching the forums for an answer to this for a couple days now, but no dice, and certainly nothing recent.

** The problem:** Every now and then, my system completely locks up.  The mouse freezes, the screens freeze, I have no keyboard function, nothing.
[B]
The circumstances:[/B] This happens completely at random, and it started about three days ago:  It's happened while booting up.  It's happened while using Gimp.  It's happened when checking email.  It almost always happens when the screensaver kicks in.  

** The specs:** I'm running Gutsy with an ATI Radeon R250 (9200) with the open source drivers.  CPU is a Pntium 4-M.  The fans don't go bonkers when it locks; in fact, they do nothing at all, and nothing feels hot (after all, sometimes it happens while logging in).  My laptop sits on a chill pad, so it stays cool.  I opened it up yesterday and checked for dust; it's clean.  I run a bare minimum of Compiz effects, less than the Normal setting; I tried it with the effects both on and off, and still got the lock-ups.  

**The diagnostics:**   I didn't find anything out of the ordinary in the logs, but may not have seen the right ones.  My system hasn't run fsck in some time; I popped in a live CD and fsck'd my partitions, and everything seemed cool.   Then I rebooted, downloaded some podcasts, stepped out for a bit, and returned to another frozen laptop.

Considering this is the end of the semester and I have a lot to write, this is pretty daunting.  I haven't lost any work *yet*, but I'm living in fear of writing and losing my work to yet another freeze (and have set OpenOffice to save every three minutes).

Any suggestions?  I'm getting pretty worried.

---

### Post by wyth on 2007-12-11
It's froze on me another four times since I posted my question, and I'm thinking this must be a hardware issue and it's time to upgrade... almost six years was a pretty good run on one laptop.

So I'd re-vamp my question to:

I beat the hell out of my laptops.  I use it constantly for work and grad school and writing.  I also use linux 95% of the time.  So what's more rugged, a Dell Inspiron with Ubuntu preloaded or a Lenovo?  Because I think it's coming down between the two.

---

### Post by ilago on 2007-12-11
For the usage you are describing, look seriously at the Lenovo. They are bug-ugly, but they are the most rugged laptops I've come across outside the Panasonic Toughbooks (widely used in mining and geology). 

Not light, but quite luggable and I work in multiple locations so I lug it around a lot. The keyboard on mine doesn't have the "Windows" key which is a minor irritant. It's easy to type on and the touchpad is usable, although I prefer a mouse. I know RedHat runs well on them and the specs are made available to linux developers. They won't let me use linux at work :(

I work in a University and they use Lenovo laptops exclusively because they are so robust. In many places they are issuing laptops rather than desktops because tech support is lower. 

My official laptop issued to me as staff is a Lenovo. We get almost no hardware failures other than some damaged screens from being dropped while open - that is user malfunction, not the fault of the machine. They were chosen to replace HPs that weren't quite as rugged. 

The biggest problem is them getting lost or stolen. 

Good looks - no. Robust - yes. Don't go for the bottom of the range, it doesn't have an optical drive.

---

### Post by tgalati4 on 2007-12-11
Reset your RAM and run memtest overnight.  You need at least 30 passes and no failures to quality your RAM to high confidence.

---

### Post by wyth on 2007-12-11
Thanks folks.  I went out to get a Lenovo tonight, pondered between a T60 and a Y410, decided the Y410 was all I needed (and a hell of a deal), and they were out of both.

Came home to do some more research, booted up, and it froze on boot.  Rebooted into windows, and it's not freezing -- which makes me think it's not the hardware, it's something else.  (First time I've booted into windows in over a month -- and I work in a windows-only office at my university.)  

So I'm taking the ram/memtest advice and will run more tests overnight.  Since I am a little rough on my machine, maybe something got knocked a little loose.

...but I did like the Lenovos...

---

### Post by sadata on 2007-12-11
Obviously, I can't say for sure whether you have a hardware problem or not, but Ubuntu does occasionally lock up the way you described. I've experienced this at least a few times on several different laptops (HP Pavilion dv8230, HP TX1220 tablet, and a Toshiba Satellite), but nowhere as frequently as you seem to be experiencing. All machines are dual core (2 Intel, 1 AMD64) and have 2 GB of RAM or higher.  At any rate, I only mention this so that you don't automatically assume that it's the result of defective hardware (although it could still be related to the specific hardware configuration and/or driver issues).

---

### Post by wyth on 2007-12-12
When I re-seated my memory, I saw that the casing around the door was cracked, so I have no doubt my hardware will choke soon.  A lot of parts in this machine were scavenged off Ebay; I figure the longer I keep this running, the longer it is before some kid in China is forced to boil it in a wok full of acid and breath the fumes.

Ran the memtest all night, no errors.  Booted up, immediate freeze even before the login screen.  Rebooted into an earlier kernel, and all is well for now.

Hmm, kernel...

EDIT: Using the previous kernel didn't work either; it still froze.  Since I was able to work for 3 hours on the windows partition last night, I'm now pretty convinced this is an Ubuntu issue, and I'm considering a re-install.

---

### Post by MONODA on 2007-12-12
I am also getting similar problems on my hp notebook (specs in signature) but it is only freezing about once a day at random times as well. I have reinstalled several times to no avail.

---

### Post by wyth on 2007-12-12
It looks like there's a similar issue with people running 64 bit machines, and there's a large thread about it [over here]("http://ubuntuforums.org/showthread.php?t=587905").  I'm not running a 64 bit machine, but I posted over there anyway, since it's the same problems.

I did a fresh re-install today; this was originally upgraded from Feisty.  So far, five hours in, no issues.

---

### Post by jmate24 on 2007-12-12
See This:
hope this works:)
[URL="http://ubuntuforums.org/showthread.php?p=3942202#post3942202"]

---

### Post by jmate24 on 2007-12-12
second try...
[http://ubuntuforums.org/showthread.php?p=3942202#post3942202]("http://ubuntuforums.org/showthread.php?p=3942202#post3942202")

---

