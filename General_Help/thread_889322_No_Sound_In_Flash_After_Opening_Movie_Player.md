---
title: "No Sound In Flash After Opening Movie Player"
date: 2008-08-14
forum: General Help
---

### Post by dethredic on 2008-08-14
So, I just did a fresh install of Ubuntu. Sound works in flash until I open something in Movie Player, then it doesn't. Any ideas?

---

### Post by tuxxy on 2008-08-14
Are you using ALSA, try at system > prefs > sound

---

### Post by dethredic on 2008-08-14
Sorry if I was unclear, all other sound works after opening movie player, just not flash sound. I dono't know what I am looking for in system > prefs > sound?

---

### Post by mb_webguy on 2008-08-14
Have you tried installing the libflashsupport package?

Even better, install the latest version of the Flash plugin, found in the Intrepid repository or [here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree") for download.

---

### Post by Lexicon101 on 2008-08-14
The default flash doesn't plug in correctly into PulseAudio, which is what libflashsupport was meant to fix. PulseAudio, from my understanding, is a system for playing multiple sound streams simultaneously, I'm not sure if ALSA does it. Of course, the latest version of flash may just fix the need for libflashsupport, but I installed the latest Flash, then libflashsupport, and my sound works perfectly.

In essence, install the latest flash, then libflashsupport for good measure. Some people have experienced problems with libflashsupport, so if it gives you troubles, remove it.. but for me, it's produced perfect results.
(Oh, then go into Tools->Add-Ons in Firefox, and click 'Plugins', and disable the older flash, if it's still there. You'll only need the new version, and you don't want it defaulting to the old flash.)

---

### Post by sdennie on 2008-08-14
> **Lexicon101 said:**
> The default flash doesn't plug in correctly into PulseAudio, which is what libflashsupport was meant to fix. PulseAudio, from my understanding, is a system for playing multiple sound streams simultaneously, I'm not sure if ALSA does it.


ALSA does support multiple sound streams and, in fact, the default sink for Pulse Audio is ALSA so it's really just a layer of indirection that few people need.  

I believe that libflashsupport wasn't included by default because it constantly crashes firefox.  The initial problem in this thread sounds like it can likely be fixed by 1) Switching to ALSA as described above or 2) Reading this lengthy but interesting guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by dethredic on 2008-08-14
Thanks guys.

> $ sudo apt-get remove --purge flashplugin-nonfree
$ wget -c [http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb](http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb)
$ sudo dpkg -i nspluginwrapper_1.1.0-0conn2_i386.deb
$ sudo apt-get install flashplugin-nonfree libflashsupport

That fixed it for me.

---

### Post by mb_webguy on 2008-08-15
The only thing about nspluginwrapper is that it doesn't keep Flash from crashing -- it just keeps it from taking the browser with it when it does.  I think the best way to go is to install the newest version of the Flash plugin from the Intrepid package.

---

