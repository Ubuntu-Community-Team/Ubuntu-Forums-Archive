---
title: "No Sound, Lenovo X61 Tablet"
date: 2008-10-26
forum: Hardware
---

### Post by dcajacob on 2008-10-26
Lately, my sound has stopped working consistently.  I have a Lenovo X61 Tablet running Ubuntu 8.04  Sound worked out of the box, but recently, I started using the docking station at work.  I am pretty sure that sound worked fine for a while after this too.  But now, it seems that when I am out of the dock, sound doesn't work at all.  When docked, it works fine.

My laptop seems to use the AD1984 sound chip.  I have done some due diligence and tried sound-related solutions like adding ```
options snd-hda-intel model=thinkpad
``` to the /etc/modprobe.d/alsa-base file and even the /etc/modprobe.conf file.  Nothing seems to help.

Has anyone else experienced this problem?  Any solutions?  Thanks alot!

---

### Post by bigmeanogre on 2009-02-04
I have had this same problem since hardy.
I saw that there was an open bug with Alsa, but the bug track was fixed in Intrepid.
No one seems to even want to admit this issue exists, even though there are hundreds of posts in various forums, with people having the same issue.

---

### Post by Russel Nurjew on 2009-02-05
I almost drove crazy solving that sound issue. I did join several
advices from other forums and websides.
The most proposed thing was something like:

sudo killall pulseaudio
sudo gzip /etc/X11/Xsession.d/70pulseaudio
sudo alsa force-reload

...then set everything to ALSA on gnome-sound-properties...
Nothing!

Other advice was to disable the modem in BIOS...Nothing! It seemed to me that nobody has an idea of what to do in that case and the proposals I got were more or less amateurish or even dilettantish.

I must mention that I can play movies - even with firefox on youtube. I can play *.mp3 or other soundfiles with several programs but have no sound on the speaker or headset.
So if anyone has a good idea...please help...Russel Nurjew

---

### Post by ketamynx on 2011-04-30
Same issue, here's how it got fixed:
- PRESS THE VOLUME UP KEY ON THE TABLET'S BUILT-IN KEYBOARD (near the blue thinkvantage button)

You will get the same issue when you press mute. If the OS doesn't recognize the mute event, the sound card will still mute itself internally, but without notifying the OS. This unless you have proper drivers installed.

---

### Post by nodnerb on 2011-10-27
Yes! Thank you!
(Updated to Oneiric, thought my sound had stopped working. As the previous post states, the mute button stops sound (duh!) but this isn't reflected in the top panel. So, to get my sound working, all I had to do was turn the volume up using the small buttons next to the thinkvantage button...)

Very happy!

---

