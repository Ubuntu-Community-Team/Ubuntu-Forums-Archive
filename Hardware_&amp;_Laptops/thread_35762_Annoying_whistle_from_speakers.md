---
title: "Annoying whistle from speakers"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by JeffG on 2005-05-20
I'm using the onboard 5.1 sound on my ASUS A7N8X Deluxe motherboard and it works fine. Except that I get an annoying high-pitched square-wave (?) hum when the system is idle (or at least when there is no disk activity). I don't get this when running XP on my dual-boot system. It drives me mad. Any ideas?

Thanks,
Jeff.

PS: it starts right at the beginning during the boot-up sequence, then it's always there.

---

### Post by ggozad on 2005-05-20
Could be the interference with your monitor. Try changing its frequency.

---

### Post by ssam on 2005-05-20
if you righ click on the volume control then there is an option there that shows you a window with a few volume slides. you should be able to add some more sliders to that from edit -> preferences.

now play with these. some might have no effect on sound, set these to zero. you should find that a few actually effect the volume. see if you can balance them all (appart from the master) around the 70% mark. this might help.

otherwise it might be that you have an (electronically) noisy system. my via epia is quite bad in this respect (i love it otherwise). i am thinking of trying to get the sound digitally out of the machine maybe USB/firewire.

sam

---

### Post by JeffG on 2005-05-20
Thanks, I'll try those suggestions, though I don't understand why the same problem doesn't occur while running XP.

Jeff.

---

### Post by ssam on 2005-05-20
just been reading this.
[http://www.djcj.org/LAU/guide/audio_quality_HOWTO.htm](http://www.djcj.org/LAU/guide/audio_quality_HOWTO.htm)
it might have some useful info.

sam

---

### Post by JeffG on 2005-05-22
Sam - that looks especially helpful! Especially the bit about no-hlt (sounds like what's happening to me), though since I'm using Grub and not Lilo, I'm not sure where to put the extra command :???: 

(That's another page on my floppy - till I get my Speedtouch ADSL working :|

---

### Post by nocturn on 2005-05-23
[QUOTE=JeffG]Sam - that looks especially helpful! Especially the bit about no-hlt (sounds like what's happening to me), though since I'm using Grub and not Lilo, I'm not sure where to put the extra command :???: 

(That's another page on my floppy - till I get my Speedtouch ADSL working :|[/QUOTE]

I had this too (not with Ubuntu).
I used alsamixer (console) and found a devices that was causing the interference (a line that was not connected, I think it was 3D).  Just muted that, and saved settings did the trick.

---

### Post by ssam on 2005-05-24
i just got a griffin imic usb thingy. and now i have very low interference :-)

maybe sound card just should not be inside a computer.

sam

ps: i had to turn off the onboard sound to get it working. actually i probably didnt have to, but it seemed easier to flick an option in the bios, then mess around with outputs and sound servers, and kernel modules.

---

### Post by JeffG on 2005-05-24
Strangely enough my whistle has gone since I started installing stuff for my Speedtouch 330 USB ADSL modem (still not sorted  :neutral: ). It starts when the Linux kernel starts during the boot sequence, then stops when it starts the hotplug stuff. Odd.

---

### Post by Jabberu on 2006-04-03
I'm still struggling with this... I used to run gentoo which I booted with lilo and I was so happy to have the no-hlt flag because it solved that annoying noise.

Alas, moving onto ubuntu which I know feel my heart can't live without, no-hlt in my grub-config doesn't reproduce the effect. And I'm reluctant to go back to lilo  since ubuntu utilises grub so well in all other instances.

The noise is there and it's particularily noticeable when I use headphones. A virtual cookie to anyone who can help me solve this.

---

