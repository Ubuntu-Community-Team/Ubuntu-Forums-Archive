---
title: "Has anyone had success with fglrx and mr9600?"
date: 2008-06-10
forum: Hardware
---

### Post by molochi on 2008-06-10
I've got an Acer Travelmate 3200 that I've been trying to get working with the proprietary ati drivers (off and on) for a year I guess. The notebook is a Pentium-M/i855 system with a mobile radeon 9700 (which is really just a souped up mr9600pro) currently running Ubuntu 8.04 (x86). By turning off all the desktop special effects, I can run it with fglrx drivers, but the system hard locks if I enable compizfusion or try to run anything that uses hardware acceleration like glxgears or alienarena. 

If anyone has ever got their mr9600/9700 to work properly I'd love to hear about what they did that worked and if the mobile r350 series doesn't work with fglrx I'd like to hear about that too so I can stop wasting my time.

Thanks in advance for any advice.

---

### Post by sidran on 2008-06-10
I run Ubuntu on my Dell Inspiron 8600 laptop and it has an ATI Radeon Mobility 9600 Pro Turbo (RV350).  I've been having this trouble myself for the past year or so that I've been using Ubuntu.  What I did (up until Hardy) was just either disable Compiz when I used fglrx or just use the open source driver.

Around the time when I got Hardy by using the update, I did see a lot of talk that the new fglrx driver now supported Compiz, but after the upgrade and updating the driver, I never got it working properly.  Eventually, I decided to bite the bullet and reinstall Hardy from scratch (since my xorg.conf was a mess anyway, I figured it could use the fresh start).

Now, I know I probably look like a noob for resorting to this (and technically I still with Linux, to a degree :P), but the fact is, after reformatting and reinstalling Hardy from scratch off the LiveCD (backing up all my data and everything first, of course), fglrx worked right off the bat right alongside Compiz.  If I recall correctly, it was even enabled by default.  It was a pleasant suprise to say the least.

Now, you may or may not want to try this route, and I am not certain you'd have the same results, but that was my experience.

---

### Post by molochi on 2008-06-10
That's probably what I'll do, as I like the compiz effects and they worked for me too with the base install. I'm noticing too many things that hard lock or black screen the system with the proprietary driver.

---

### Post by molochi on 2008-06-19
Right, I think I figured out the problem. Compiz appears to want to rely on Mesa indirect rendering and OGL apps need direct rendering to not run really slowly. So Compiz has to go, mesa has to go, and I've got to figure out how to get the proprietary drivers and X to use the hardware properly. 

I found a guide (the example was done on a Mobile Radeon 9700) that may help here,

[http://wiki.cchtml.com/index.php/Debian_Installation_Guide](http://wiki.cchtml.com/index.php/Debian_Installation_Guide)

---

### Post by sidran on 2008-06-19
You can also try one of these (you don't specify which version you have so I'll link to the index):
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by molochi on 2008-07-08
Update... still broken.

I was able to get to the point where some games, google earth, etc would load but ran too slowly (because most of the cards hardware is still turned off) to be usable and the system would still randomly lock up. Enabling dedicated memory (a quest in its own right) on the card would lock up the system and eventualy trashed the HDD. Maybe has something to do with AGP aperture (set to 256MB for some reason while it's 64MB under windows), or fastwrites(used to be required with hardware cursor under WinXP but can be unstable) but xorg options don't seem to have any effect, don't know. 

I can't troubleshoot this if the problem is corrupting the HDD. The first hardlock could just be creating side problems. I'll just use the open driver and wait till the next versions to try again.

---

