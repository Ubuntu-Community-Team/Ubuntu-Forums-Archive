---
title: "Asus Eee PC 1201PN - headphones and mic not working"
date: 2010-10-12
forum: Hardware
---

### Post by russki_drewski on 2010-10-12
I just bought this little netbook and I have to say, I rather like it and it is a pretty sleek little machine. I just installed Ubuntu 10.04 (Maverick seems like it still has a lot of problems) and it runs like a dream.

The only problem is that when I insert my headphones to listen to music or something the speakers are muted, but no sound comes out in my headphones.

Also, the internal mic doesn't work, but I have a feeling that this is related to the first problem.

I've tested this in Win7 and both headphones and internal mic work fine. Does anyone have any suggestions? My search on the forums has shown very little for this machine.

---

### Post by russki_drewski on 2010-10-13
Any takers on this one? :confused:

---

### Post by gloawu on 2010-10-17
Hi there!
I also recently got a 1201pn and had the problem of having no sound at all or just either on the internal speakers or on the headphone jack independently of having external speakers or headphones plugged in. Haven't tried the Mic-in yet. The solution in my case (also running Lucid) was to purge the alsa-installation an reinstall it with another package, after that it now works fine!

Solution:
So open up a command line and issue the following commands:
1. sudo apt-get purge linux-sound-base alsa-base alsa-utils
2. sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-backports-modules-alsa-lucid-generic
3. restart

How i got to it:
I found that solution via the following two threads:
1. [http://ubuntuforums.org/showthread.php?t=1583078&highlight=alc259](http://ubuntuforums.org/showthread.php?t=1583078&highlight=alc259) Post #9 by lidex
2. [http://ubuntuforums.org/archive/index.php/t-1439408.html](http://ubuntuforums.org/archive/index.php/t-1439408.html) Post #2 by Boobeck

Other tips for users of the 1201PN:
- Getting those hotkeys working: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus) Eee 1201N 
- Nice applet for controlling other hardware stuff on this machine: [http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)

Now if someone could come up with a fix for two-finger-scrolling with that touchpad everything would be ok (after the usual fiddling around to get everything working in ubuntu :mad: )

Please let me know if it worked for you.

Greetings and good luck

---

### Post by IGITIHI on 2010-10-17
Thank you very much for this solution, I had tried all the other threads to no avail!

---

### Post by russki_drewski on 2010-10-18
Thanks a ton for the answer gloawu. I was beginning to think everyone's questions but mine got answered on the forums. :P

As for the problem, I stumbled across a thread for a different EeePC model and it said more or less what you mentioned but a little simpler.

Basically I just installed the following package through synaptic:

linux-backports-modules-alsa-lucid-generic

After that the headphones and mic worked like a charm!

Thanks a ton for the detail in your response. If my audio ever gets borked I know how to purge it and start it from clean.


As for two finger scrolling, I've seen some stuff on the forums about enabling it, but I just never tried it out. I'm fine with the regular side-scroll on the right of the pad.

---

### Post by gloawu on 2010-10-28
About that two-finger-scrolling:
[http://www.uluga.ubuntuforums.org/showthread.php?p=9983689](http://www.uluga.ubuntuforums.org/showthread.php?p=9983689)
Thanks to "eken"!

---

