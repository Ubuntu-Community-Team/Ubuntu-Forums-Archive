---
title: "VIA Independent Audio"
date: 2012-02-14
forum: Hardware
---

### Post by Grisk13 on 2012-02-14
First off, I think this is in the right spot, I am just returning to ubuntu as of last week, so if this is wrong, I will happily adjust it.

My problem: In Ubuntu 11.10 headphones will either produce no sound, or headphones and speakers are both on constantly.  

This is not such a problem on my desktop, but on my laptop, where I can't just turn off the speakers...  Well, the people at the university library don't appreciate dubstep the way I do...

What I've tried: I've done some digging in Alsamixer and I have discovered this neat little setting called "Independent HP." My research shows that this setting is what sets the sensor when you plug in/unplug the headphones.  

When I set Independent HP to "OFF," when I plug in my headphones sound mutes.  Unmuting the sound causes both my speakers and headphones to produce sound

When Independent HP is "ON," I plug in my headphones and nothing happens.  No audio through my headphones, and the speakers continue to pump sound as normally.  

Some digging has turned up a bunch of complaints about this bug, but no way (that I have found yet) that fixes it.  It is also worth noting that the threads I have found have always been from more than 2 years ago, so the issue may have been resolved for most people already.  

It is worth noting that I have already tried reformatting and re-installing Ubuntu.  

The next logical question is what hardware I actually have, and I have compiled two console commands that the Ubuntu audio debugging wiki mentions that have that information in it.

This is probably too much information, but I didn't want to leave anything important out.  Before this, I knew almost nothing about sound cards...  I'm learning ^_^

Thanks for reading!

Edit (2/18/2012): This issue has been repaired, it appears there is simply a bug in the verison of Alsamixer that comes on the Ubuntu install disk, a proper version can be obtained  [https://code.launchpad.net/~ubuntu-a...aily/+packages](https://code.launchpad.net/~ubuntu-a...aily/+packages) but you may have to remove the old one using: sudo apt-get purge alsa-hda-dkms 

Thanks, Ubuntu community!

---

### Post by Grisk13 on 2012-02-16
I wanted to post an update in case anyone has any clues as to what is causing this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/741825/comments/20](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/741825/comments/20)

describes a patch that one can install that fixed the same issue for someone else, but when I run the same commands I get a package not found error.  Any thoughts/ideas?

---

### Post by Yellow Pasque on 2012-02-17
What version of Ubuntu are you running?

---

### Post by Grisk13 on 2012-02-17
I am running 11.10, I apologize for leaving that out!

---

### Post by Yellow Pasque on 2012-02-17
I think your bug's a bit different then, since that one was fixed in 11.04. Looking at ALSA changelog, this is one of the items noted in ALSA 1.0.25:
> ALSA: hda - Fix the silent front with independent-HP for VIA codecs 

To try ALSA 1.0.25 kernel module/driver, use: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

---

### Post by Grisk13 on 2012-02-17
Interesting.  I've had this problem with all distros since 9.10,  I will try those kernel modle/drivers once I get back to my machine.  I do have one question, though.  all of the modules on that page are built for "i864" which I believe means x86_32 systems, but my desktop is running an amd_64 version.  Is that a problem?

---

### Post by Yellow Pasque on 2012-02-17
The .deb file has "_all" in the name, which means it will work with amd64.

---

### Post by Grisk13 on 2012-02-17
I ran the .deb and I encountered this error:

Selecting previously deselected package alsa-hda-dkms.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 197737 files and directories currently installed.)
Unpacking alsa-hda-dkms (from .../alsa-hda-dkms_0.201202151446~precise1_all.deb) ...
Setting up alsa-hda-dkms (0.201202151446~precise1) ...
Loading new alsa-hda-0.201202151446~precise1 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-16-generic
Building for architecture x86_64
Building initial module for 3.0.0-16-generic
Error! Bad return status for module build on kernel: 3.0.0-16-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201202151446~precise1/build/make.log for more information.
dpkg: error processing alsa-hda-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 alsa-hda-dkms

So apparently there is something going haywire between my kernel and Alsa?

EDIT: I realized I had the wrong file version, that's the new one for Ubuntu 12.04?  The one labeled "Oneric" comes up as "A later version is already installed"

---

### Post by Yellow Pasque on 2012-02-18
```
sudo apt-get purge alsa-hda-dkms
```
Then, try to install the Oneiric one.

---

### Post by Grisk13 on 2012-02-18
This worked!  You are the biggest nerd-baller I have ever had the pleasure of questioning!  

One more question: I'm a CS student and fairly new to Linux (Window$ campus.)  To clarify what just happened: I uninstalled my sound driver (using the purge "alsa-hda-dkms") and then just re-installed it (through the .deb) right?  Do you have any recommended reading on Alsa?

Thanks a ton, this was the last real glitch I needed to work out before  I completely switched to Linux! :D

---

