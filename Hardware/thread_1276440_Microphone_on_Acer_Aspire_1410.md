---
title: "Microphone on Acer Aspire 1410"
date: 2009-09-27
forum: Hardware
---

### Post by Ryan_Singer on 2009-09-27
Hi Everyone,

For some reason the internal microphone on my Acer Aspire 1410 is not working. Everything looks fine in both the Volume applet and the sound preferences panel.

Any advice for getting it working? It'd be nice to be able to make quick calls using Gizmo5. As a Google Voice user, it is a great combo.

--
Ryan

---

### Post by Sultan-mrm on 2009-09-27
I faced this problem with my acer aspire 6935 but with alsa 1.0.21
i get it work good  :) 

just update your alsa and wish to have goodluck .

---

### Post by Ryan_Singer on 2009-09-27
I just installed Alsa-Base from Karmic's repositories, which gives me alsa 1.0.20.

Still doesn't work.

---

### Post by noliviercifg on 2009-11-14
Had the same problem as you (everything OK including microphone, but no internal microphone). Have also Ubuntu karmic
I finally solved the issue and it works now.
- I installed alsa 1.0.21 
[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)
- then played with kmix 
- at some point, the sound recorder worked with my internal microphone, 
- it is still not recognised by pulseaudio
- Skype is also working with my internal microphone, but only if I run it in a terminal with 'sudo skype'
:KS

---

### Post by fgmart on 2009-11-14
Hey - Same story for me -- new Acer 1410 with Karmic and mic not working.

I did the Alsa 1.0.21 install (those were great instructions) and played with kmix.  The trick in kmix was enabling capture (checkbox) and bringing up the capture level.

At this point, the mic works in Sound Recorder!  Sort of -- it's really scratchy (like analog radio static).

But nothing in Skype -- whether or not I launch it as root.

So frustrating -- especially since everything works fine in Windows 7 :(

Any ideas from others?

Fred

---

### Post by Strohmy on 2009-11-19
Yep, I'm in the same boat as the others. My 1410's mic didn't work at all initially. 

I updated ALSA to 1.0.21, and still nothing. 

Then I tried launching Sound Recorder with gksudo, and the mic worked in Sound Recorder. However, launching with gksudo for Empathy didn't do anything to make the mic work.

Then I enabled Capture in Kmix. Not sure that did anything.

Because the hardware actually can work with the right permissions, I'm at a bit of a loss. Would appreciate any insights on this.

---

### Post by Pigcold on 2009-11-29
I just tried the OpenSuse Live GNOME 11.2 CD.  The microphone works.

I could use the sound recorder to record my voice and play it back.

I checked the Sound configuration in System and it looks very similar as Ubuntu 9.10.  How can I find out the different on the driver?

---

### Post by Pigcold on 2009-11-29
Add this app,

sudo apt-get install linux-backports-modules-alsa-karmic-generic

The microphone works now.



> **Pigcold said:**
> I just tried the OpenSuse Live GNOME 11.2 CD.  The microphone works.

I could use the sound recorder to record my voice and play it back.

I checked the Sound configuration in System and it looks very similar as Ubuntu 9.10.  How can I find out the different on the driver?

---

### Post by yelvington on 2009-12-03
linux-backports-modules-alsa-karmic-generic did not fix the problem for me. I installed alsa-mixer, and if I crank the microphone volume WAY up, I can get a recordable signal, but it's not sound. It's some electronic noise.

---

### Post by yelvington on 2009-12-03
Update: The microphone is now working with Audacity, but not with Skype. 

The only options Skype offers in its config are all "PulseAudio Server (local)." 

Audacity offers three choices for recording devices. "Default" is selected. The other two are "pulse" and "HDA Intel: ALC269 Analog (hw:0,0)"

---

### Post by yelvington on 2009-12-05
Built-in microphone is now working with Skype. The problem seems to be an incompatibility with Skype's auto-leveling feature and PulseAudio. Disabling "Allow Skype to automatically adjust my mixer levels" made the microphone work.

---

### Post by xoqa on 2010-01-11
I have a 1410, and I guess my response should go on this thread. I've tried the solutions presented here, but none of them work. My internal mic just doesn't work.

I can plug in an external one, but that is highly inconvenient at this time, is anyone working on fixing this?

---

