---
title: "Karmic Koala, Pulse Audio and Hibernation"
date: 2009-11-09
forum: Hardware
---

### Post by ChrischanM on 2009-11-09
Dear Users,

I'm sorry but after many hours of searching through all kind of forums I didn't find a suitable answer to my problem.

In short: I use Kubuntu Karmic Koala 9.10, changed recently to Pulse Audio and suddenly Hibernation and Standby doesn't work.

Details: Firstly I installed the ALSA driver because the preinstalled one from the CD didn't work. Unfortunately there was only the option of one sound at the same time. In case of more sounds (e. g. listening to music and a system notification) I had to stop everything or even log out and in to re-activate the sound. Because of this I changed to Pulse Audio according to several posts. It worked quite good (not regarding some strange sounds in a couple of music files), also simultaneous sound. But I guess since then the hibernation and standby is not possible. I checked various log and the problem seems to lie in Pulse Audio. All the hacks which other people proposed didn't work.

Thanks in advance! You do a good job!
Christian

---

### Post by ChrischanM on 2009-11-10
bump :-)

---

### Post by jtp755 on 2009-11-10
Had pretty much same problem..

Install the pulseaudio-utils package and that will solve it.

For proof check out the log at /var/log/pm-suspend.log and it will mention it cant find pacmd and it inhibits the suspend.

---

### Post by ChrischanM on 2009-11-11
Wow, I'm impressed! Thanks JTP! Now I can hibernate and execute Standby.

My workaround was that I installed uswsusp and "s2disk" / "s2ram" - but this is much more comfortable, especially regarting the implementation in the power management programs.

Ubuntuforums.org rulez! :D

---

