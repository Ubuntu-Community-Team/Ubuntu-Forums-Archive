---
title: "Thinkpad screen issues- help please!"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by theuberpig on 2007-09-08
Hi,

I already posted a similar question in the general help forum, but received little actual aid...

I've just installed Gutsy tribe 5 on my Thinkpad T61, actually, several times at this point, and what seems to be happening is that every time I reboot for the first time, my login screen and everything after is appears totally distorted and skewed (see image).

Here's basically what's been done on my computer in general so far.  Confusing bits!

Installed Gutsy in Safe Graphics Mode.  Installed with no issues.
Rebooted,  Ran with no issues.  Installed updates, rebooted.
Screen fubar, as shown in picture.
Several reboots to see if the problem would just go away, no avail.
Ran LiveCD in Safe Graphics mode for a while, ended up just reinstalling.
Rebooted and everything seemed OK.  Did NOT install updates.
Accidentally rebooted.  Screen fubar, again.
Ran LiveCD, sought help on forum.
Issued the following command:
              sudo dpkg-reconfigure xserver-xorg
Went through all the steps.  Rebooted.  Black screen.
Reinstalled using safe graphics mode, rebooted the necessary one time, etc.
Rebooted again.  Screen fubar.  Another attempt at reconfiguring.  No avail.
Reinstalled using safe graphics mode.  Rebooted once.  Left computer on all night, suspended, in fear of getting the same issue.  Network was not responding this morning, rebooted with a sigh.
Booted up without a hitch...

Too afraid to try again.  But does anyone know if there's something I can do to prevent this from occurring?

Here are my stats:
Core 2 Duo T7300 (2.0ghz)
2 gb RAM
Nvidia Quadro NVS140M
Gutsy Gibbon Tribe 5
Monitor resolution at 1440x900
...don't know what you all need.

Any and all help greatly appreciated!

Thanks in advance,
Robert

---

### Post by rybu on 2007-09-08
I have Ubuntu 7.10 running pretty well on my Thinkpad T61p (6457-5KU) at the moment. 

This thinkwiki page has reasonably-detailed instructions which covers what I've done. 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video)

The "nv" driver is a pretty good first start as far as drivers go.  Just download the latest update and switch from the generic driver to "nv" in your xorg.conf.  Once you've installed all the basic apps like g++, you can take the next step and download the NVIDIA proprietary drivers from the NVIDIA webpage and follow the build instructions above.

I still have a few problems on my laptop, but it's mainly just the odd DRI app crashing.  I have one other app regina-normal that doesn't want to compile for some strange reason... The compiler seems to be choking on the qt libraries.

---

### Post by theuberpig on 2007-09-08
Thanks a lot for the help!  I really appreciate it.

However, I'm kind of a linux/unix uber-noob, so I have a few questions.

To switch my driver to nv, do I have to go through that whole process (the one I encountered when I put in dpkg-reconfigure xserver-xorg) again?  I'm sick of configuring my keyboard and all that, when it works alright to begin with.

Also: what is g++, and how do I get it?

Thanks so much, I apologize for my ignorance.

---

### Post by theuberpig on 2007-09-08
Oh, woe is me.

Installed the updates.

Got restricted drivers manager to work.

Installed the latest nvidia drivers.

Restarted the computer so they would take effect.

After witnessing my monitor turn on and off for a while...

This happened.

Help?

---

### Post by Kxpress on 2007-09-08
My Thinkpad T61 is similar to yours, excepted my screen is little bit better: 1680x1050. I follows steps in this page:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)

Most of components of my laptop works great excepted the Audio/Sound subsystem. Last time, I tried to install ALSA driver, somehowthe driver installation "killed" my laptop: screen was totally BLANK when I logged in. So,  I am putting it off for awhile, I believed the Audio Chip is Intel 82801H (ICH8) family and Codec is Analog Device Inc., there is no driver for this chip on ALSA page...

My graphic display is in full mode 1680x1050x24, looks great.

One note: I used Ubuntu Fiesty 7.04 Alternate 64-bit version CD for installation:lolflag:

---

### Post by theuberpig on 2007-09-08
...bump.  :(

---

### Post by Vadi on 2007-09-08
Oh dear.

If you're new to Ubuntu, why are you trying out Gutsy, which hasn't even been released yet? Is there a specific reason?

Go with Fiesty, that's the current version...

---

### Post by Vadi on 2007-09-08
See is this thread helps you:

[http://ubuntuforums.org/showthread.php?t=533557&highlight=Thinkpad+T61](http://ubuntuforums.org/showthread.php?t=533557&highlight=Thinkpad+T61)

---

### Post by theuberpig on 2007-09-09
Well, despite the fact that it's in alpha at the moment, I've read that it's easier to get that running on my laptop than Feisty.  Lot more stuff works out of the box on 7.10...

---

### Post by Vadi on 2007-09-09
That's not confirmed by thread though, eh? 

;)

Just give Fiesty a try, maybe you'll have better luck. I definitely wouldn't recommend starting out in Ubuntu with non-finished software - you might get too frustrated, because, well, it's not finished.

Gutsy does have nice things, but it's better wait the month 'till they're all ready :)

---

