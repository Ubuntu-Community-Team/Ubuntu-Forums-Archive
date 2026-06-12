---
title: "Sound is too fast and high-pitched"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by timelord726 on 2005-02-17
I just (re)installed Ubuntu Warty on my computer, after a bad experience with Hoary.  My sound worked great after install, but once I rebooted, everything (system sounds, MP3s, etc.) is too fast and high-pitched.  I've searched the internet for over half an hour looking for a solution but I found nothing.  I have an Intel AC'97 onboard sound card, and a relatively fresh install of Warty.  Please help!

Thanks!

---

### Post by wallijonn on 2005-02-18
If this was Windows I would say to check that DMA is turned on all your drives or to check for IRQ conflicts. I'm sorry I could not be of more help but I have an Audigy Live and an Audigy1 on my comps.

---

### Post by Buffalo Soldier on 2005-02-18
If I was in your position, here is what I would try:

1) Go to Computer -> Desktop Preferences -> Sound -> **un**check Enable sound server at startup.

2) Edit your /etc/modules file and add **snd_ac97** at the end of the list.

3) Update the plugins for my mp3 player.

4) Restart the computer.

---

### Post by timelord726 on 2005-02-19
Not to sound ignorant, but I understand everything except step 3.  How do I update XMMS plugins (or MPlayer or whatever)?

EDIT: Okay, sorry, followed steps 1, 2, and 4 and the problem is solved.  Normal *played* sounds are working fine, but there is no system sound.  I know this directly traces back to step 1, but is there any way to get regular system sounds back?

EDIT #2: Problem solved.  I turned back on "Enable sound server at startup" with **snd_ac97** in my modules list, and both work normally!  Thanks so much!

---

### Post by ba5e on 2005-03-21
This is a problem I know well, it is linked to the 'ac97clock' (sampling rate) that is fixed in the ac97 hardware (unable to convert other rates). I have experimented with many different settings, and 48000 is the best. 

The problem is that ALSA, or the kernel, maybe does not seem to recognise the correct setting.  I had a pig of a time trying to get ANYONE to help me on this matter, but eventually sorted it. Unfortunatly cant remember where the setting goes,( due to not saving my settings last time i re-installed) but if you find out tell me!
the line you need is related to ALSA:

ac97clock=480000

i think it goes in the alsa-base config file after thinking ! googling brings back nothing, but i did find the solution on google about 2 months ago.
Maybe its time for me to by a nice SB audigy or something instead!
btw I am using an i815 chipset (compaq)

Will.

---

### Post by munki on 2005-03-21
I got the same chipset in my laptop, and got the same problem.

But fixed the problem by running alsa drivers, instead of oss drivers. alsa rox :)

---

