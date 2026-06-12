---
title: "[SOLVED] No sound on a HP Laptop"
date: 2008-12-06
forum: Hardware
---

### Post by sheishkabob on 2008-12-06
Im running 64bit ubuntu on a HP Pavilion Laptop. Everything works perfectly so far, except sound. I'm running Ubuntu, Xubuntu, and Kubuntu. I have some sound. On the login screen, i get a crazy sound of drums. It sounds like the usual ubuntu theme, but it seems to run 4 times overlapping. On the Kubuntu desktop, the sound constantly beeps with a low pitch buzz. Apart from that, there is no sound.

The built in sound card is an Altec Lansing, according to a website i found. 

I imagine there is a text file I could post to help, but i don't know what.

I don't know if it's a driver issue or if it's a setting somewhere.

Help! and thanks.

---

### Post by sheishkabob on 2008-12-07
Does any one else have (or had) similar issue?

---

### Post by Enriquesonora on 2008-12-07
I have HP omnibook 4150 and installed Ubuntu 8.04. I am also haviing difficulty getting sound to work. I have started to use the Sound troubleshooting page, however, typing the commands into Terminal have proven unsuccessful. The terminal shows install, then restart, no sound. This is fustrating and almost a deal killer for Ubuntu. Hopefully the wireless features won't be this difficult.
Any advise would be great!

---

### Post by Mike Beggs on 2008-12-08
I have exactly the same problem with an HP DV4-1041TX, with the stuttering drums and everything.

I had this problem under Gutsy Gibbon but it was fixed following remu's directions here: [http://ubuntuforums.org/showthread.php?t=912896](http://ubuntuforums.org/showthread.php?t=912896)

But after upgrading to Hardy Heron the trouble is back, and having pci=noacpi as a boot option no longer does the trick.

I'd be really grateful if someone works this out...

---

### Post by Mike Beggs on 2008-12-08
Sorry... mixed up there - should have said it worked in Heron, but stopped working on upgrade to I. Ibex.

---

### Post by Mike Beggs on 2008-12-09
Alright, I fixed this problem thanks to ohingst in this thread: [http://ubuntuforums.org/showthread.php?t=993075](http://ubuntuforums.org/showthread.php?t=993075)

Open terminal and type:

sudo nano /etc/modprobe.d/alsa-base

Add to the bottom of this file:

options snd-hda-intel enable_msi=1

Exit and save with CTRL-X

Reboot. Drums as they should be! It worked for me.

---

### Post by rajasekhar on 2008-12-11
this worked for hp dv4t laptop. awesome. thanks a bunch!

---

### Post by 2hot6ft2 on 2008-12-12
> 3. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a bug in Intrepid):

Code:

$ alsamixer [COLOR="RoyalBlue"]-Dhw[/COLOR]

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer [COLOR="RoyalBlue"](marked in blue above)[/COLOR], otherwise it will open the PulseAudio mixer.

4. Log out & back in for changes to take effect!

Taken from here [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

