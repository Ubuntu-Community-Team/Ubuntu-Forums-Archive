---
title: "Can't find soundcard!"
date: 2008-12-29
forum: Hardware
---

### Post by Hoyland84 on 2008-12-29
I've just done the stupidest thing. I wanted to update my alsa-driver and looking for the shortest way I ran the script on this site:
[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I'm sure this is a good script for those who actually have an Intel HDA sound card. I don't.

[FONT="Courier New"]lspci[/FONT] tells me i have this:
[FONT="Courier New"]nVidia Corporation Device 0774 (rev a1)[/FONT]

[FONT="Courier New"]aplay -l[/FONT] now tells me this:
[FONT="Courier New"]aplay: device_list:207: no soundcards found...[/FONT]

So I need help with cleaning up after myself here. How can i set up alsa to work with my sound card again. Be advised as I am quite a newbie (as you could probably tell by now). I'm running Debian, but I don't think that should matter here(?) 

Joke's on me guys.

---

### Post by Yellow Pasque on 2008-12-29
First, uninstall the alsa sources you compiled:
```
cd /usr/src/alsa-utils-1.0.16
sudo make uninstall
cd /usr/src/alsa-lib-1.0.16
sudo make uninstall
cd /usr/src/alsa-driver-1.0.16
sudo make uninstall
cd /usr/src
sudo rm -rf alsa*
```
Now, edit your alsa-base file and remove the last line.
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Finally, if you want the latest alsa suite, you could try this script. It was written for Ubuntu, but I don't see why it wouldn't work on Debian if you're running kernel 2.6.24 or later.
[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---

### Post by Hoyland84 on 2008-12-29
Thank you very much! This was just what I needed. And, yes, worked fine for Debian.

---

