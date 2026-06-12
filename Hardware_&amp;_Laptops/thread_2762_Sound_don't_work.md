---
title: "Sound don't work"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by Lord_ZealoN on 2004-10-31
Hi.

I have 2 soundcards

An integrated in motherboard and a SounBlaster 5.1

In Suse It did not have sound but it entered in yast and it selected the card that it wanted to use.

But in Ubuntu, i can't select it (well, or i don't know how become it)

Then i have'nt sound, and I am returning to me crazy into config  files.

Some idea?

---

### Post by jwb on 2004-10-31
Did you make sure to set the PCM (1 &2) to be up in the sound control applet? For some reason, adjusting the volume isn't enough. You have to set those two sliders up before you get the volume control to do jack.

I thought my sound card wasn't detected when I first ran into that in Gnome 2.4. Don't know why they haven't changed that. For all the talk of sane defaults and expected behaviour talk, that one has continually slipped by.

---

### Post by Joeb on 2004-10-31
I had a similar problem, but instead of an integrated sound chip being picked up, my tv card was being picked up as the sound card (snd_bt87x or something like that).  My SBLive showed up in the mixer, but the bttv card was always listed in the first tab.  Since I could not find a way to disable it and it kept interfering with sound, I renamed the driver under /lib/modules/2.6.8.1-3-386/kernel/sound and rebooted.  I received an error message about it being missing during the boot, but now my sound works flawlessly!

I'm assuming that something changed in one of the updates I did after installing, because it used to work fine.  I haven't had time to try a clean install without doing any updates to see what is different.  Maybe one of these days....


Joeb

---

### Post by Lord_ZealoN on 2004-11-01
Ysterday, after hours and hours proving configurations, I was decided to deactivate the integrated card (that is deactivated with jumper) and now works perfect.  

Single I have to do like causing that it sounds by the 5 loudspeakers

---

### Post by theBlackDragon on 2004-11-02
My sound also won't work, I can't open the gnome-volume-manager as it just hangs there forever, options in Gnome's Sound Panel don't work and get me a "/dev/dsp: No such file or directory" in the console.

When I check things with lsmod all the appropriate drivers appear to be loaded, what could be wrong? :confused:

---

