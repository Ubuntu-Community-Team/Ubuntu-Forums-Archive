---
title: "Live CD freeze on install - Packard Bell easynote"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by CoximusPrime on 2008-04-07
Hi guys, 

  I've looked at the other easynote threads and can't find this problem, hope someone can help. I've used ubuntu for a while now (by no means an expert but can find my way around ok). A mate asked if we could install ubuntu on his laptop, a packard hell easynote F-series. I don't know too much about the spec other than its running a 2.8GHz intel celeron and an sis600 video chipset.

  Anyways, when I boot off the live cd, it gets to 
    "cat: /var/lib/acpit-support/bios-version: no such file or directory"
    "* Saving VESA state..."
  and hangs there.

  I have tried F6 and the options noacpi nolapic nodma all_generic_ide found here [https://answers.launchpad.net/ubuntu/+question/26995](https://answers.launchpad.net/ubuntu/+question/26995) but they make no difference, and I have tried vga=771 which just either give me a blank screen and hangs or a screen with a white underscore in the top left of the screen and hangs. I've tried this with an ubuntu 7.40 and latest 7.10 live cds and both do the same. I did try an openSUSE live cd and that boots fine (but I really want to stick with ubuntu as is by far my preference if possible) ... can anyone shed any light on this one??

cheers everyone.

---

### Post by CoximusPrime on 2008-04-09
Hi again guys,

  OK, I've now installed ubuntu via the alternative CD, it still hangs on boot stating "*saving vesa state" ... I can however get to the console by using the recovery option.

  I checked the xorg.conf file and it has setup the video chipset as some sis chipset (that is not the sis600).

  I was wondering if, firstly is this a graphics issue or am I barking up the wrong tree, and whether I could boot off the openSUSE live CD and copy the working drivers from there onto the installation of ubuntu (I've just tried copying the xorg.conf file from the openSUSE boot to the ubuntu /etc/X11/ directory as when I boot openSUSE the xorg.conf file sees the chipset as sis600) but this had no impact. Is this possible and if so which file/folders should be copied where, or am I just dreaming??

Cheers everyone

---

