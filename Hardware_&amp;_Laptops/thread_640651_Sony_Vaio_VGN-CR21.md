---
title: "Sony Vaio VGN-CR21*"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by s3phiroth on 2007-12-14
Hi there.

I'm thinking about buying a Sony Vaio VGN-CR21 S/W. Has anyone installed Ubuntu on any laptop of this series ? What are the thoughts on it ? Does everything work right ?

My main concern is suspend/hibernate. How does that usually works in Sony Vaio laptops ? I've looked around on other threads but I haven't seen any mention of this series (or the VGN-CR11 which is basically the same with lower clock speeds on the processor).

If I do buy it, I'll report on it later on this thread :)

Thanks in advance.

---

### Post by kufa on 2007-12-17
Ubuntu runs great on my Sony Vaio VGN-CR21 S/W, however the RTL8101E Ethernet card will be a pain in the *** if you change distro.

---

### Post by s3phiroth on 2007-12-17
Thanks for the input :)

I'm not thinking about changing distro, but even if I did, I have a long past of Gentoo and Slackware, and lots of kernel compiling and weird issues solving, so I would probably find my way around ;)

If you can get it to work on one distro, you can get it to work in any distro, one way or another.

Sorry about asking this again, but suspend/hibernate works perfectly, right ?

What's your average battery time ?

And have you ever used external screens ? Any troubles with that ?

And apart from Ubuntu itself, is there anything you haven't liked in the laptop itself ? I'm not sure if I'll buy it yet (due to some financial issues), but I do buy one now, that's going to be it.

It was actually fun to see a couple of Macbooks sitting a few meters away from these Sony Vaios at the store. The Vaio specs are much better and they cost almost the same as the lower end Macbook. And yeah, the Macbook screens are smaller, but the space around the Macbook screen makes it as big as the 14" Vaio.

---

### Post by s3phiroth on 2007-12-20
Well, I have several issues.

Sound didn't work, i solved it installing linux-backports-modules from the backports repository.

Compiz fusion isn't working but I'll look into that later.

I haven't tried wireless yet.

Suspend/Hibernate aren't working and I haven't had the time to find a fix yet.

So far, that's it. I'll post more news as I find out solutions.

---

### Post by systemgod on 2007-12-20
Thanks for the tip on linux-backports-modules that solved my sound issue on my VGN-CR11S

Hibernate out-of-the-box does not work  (doesn't poweroff the portable, I still have a blinking cursor on the screen and I can't revive it. The only way to make it stop is to press the powerbutton for a few seconds)

Suspend seems to turn off the machine but then I can't get it up anymore.

Note: I did not investigate much as I normally don't use hubernate or suspend (I started using portables 10 years ago when hibernate/suspend was highly unreliable even on Windows so I stopped trying it :-)

Nico

---

### Post by s3phiroth on 2007-12-20
I already solved that as well, installing a more recent kernel (i had to compile it). I'll post the links for the guides i followed later because right now i'm not on the laptop.

On the process of compiling the new kernel i lost the wireless configuration but i'm working on it, so when i get it all to work i'll post it here :)

---

### Post by murmel on 2007-12-24
Hehe, that would be nice! I had problems when installing Gutsy Gibbons. The X2300 didn't work at default. I had to use the alternative cd and then install xorg-server and restricted drivers (maybe something else too.. can't remember. had problems with the sound drivers but solved it whith google) and then the Webcam doesn't work. And "maybe" I have a problem with the "power options" .. but that's probably just me who've configured it wrong... :P
Hibrinate doesn't work that well for me either...

---

### Post by murmel on 2007-12-26
I just posted a small howto for CR21*!
Chech it out **_[here](http://ubuntuforums.org/showthread.php?p=4020021)_**!

---

### Post by sixmoney on 2008-02-01
What kind of strategy you've used to partition the drive?
I was planning on removing vista putting just ubuntu and then emulate windows XP for further needs.
What about the system for dvd,mp3 and movies playback did you removed it?
In your opinion is it better to put an usual dual boot configuration? I did not want to, since it wastes disk and I would probably use linux and not windows...

---

