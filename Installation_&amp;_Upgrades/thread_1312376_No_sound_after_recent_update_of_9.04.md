---
title: "No sound after recent update of 9.04"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by christopherbalz on 2009-11-03
Description: No sound except system beep.  The update was in the last few days (up to a week) from this post.  Previously, the sound was working fine, albeit with the helper-script needed after resume from suspend/hibernate.  

Specific Problem: I believe I need snd-hda-intel module to load, and it is not loading.  Have added it to /etc/modprobe.d/alsa-base.conf but it is still not loading after reboot. Are backports required here?  

System Info: Here is the relevant info on my set-up:

 [http://www.alsa-project.org/db/?f=48af5b0359e4ef62f778a1d12f02cf0adb3317ff](http://www.alsa-project.org/db/?f=48af5b0359e4ef62f778a1d12f02cf0adb3317ff)

Packages: I have all main and peripheral 'alsa'-related packages installed via Synaptic.  The comments on [this debian bug]("http://osdir.com/ml/debian-bugs-dist/2009-10/msg04961.html") assert that indeed snd-hda-intel is available with current kernel (although that bug refers to .30, and I am on .28 ).  

Any ideas would be great.  Thank you in advance.

---

### Post by MrSnowmiss on 2009-11-03
I do have an HDA Intel soundchip too, first after upgrading I missed sound but solutions in this thread helped me (and others): 

[http://ubuntuforums.org/showthread.php?t=1304783](http://ubuntuforums.org/showthread.php?t=1304783)

---

### Post by christopherbalz on 2009-11-04
Thank you.  Tried the suggestions on the link you posted but no luck.  Also, I have "Null Output" for PulseAudio.  Any sound server is fine, pulse or alsa, as long as it will work again.

This update seems to have nuked the sound on my system in a clever way.

---

### Post by christopherbalz on 2009-11-11
No luck with this one either (am also on a ThinkPad - R51 ): [https://answers.launchpad.net/ubuntu/+question/73060](https://answers.launchpad.net/ubuntu/+question/73060)

---

### Post by christopherbalz on 2009-11-11
Many solutions entail opening alsamixer from the command line.  When I do this, I get:

//cbalz-tp-r51-0/.../~ $ sudo alsamixer
[sudo] password for christopherbalz: 

alsamixer: function snd_ctl_open failed for default: No such file or directory
//cbalz-tp-r51-0/.../~ $

---

### Post by MrSnowmiss on 2009-11-11
> **christopherbalz said:**
> Many solutions entail opening alsamixer from the command line.  When I do this, I get:

//cbalz-tp-r51-0/.../~ $ sudo alsamixer
[sudo] password for christopherbalz: 

alsamixer: function snd_ctl_open failed for default: No such file or directory
//cbalz-tp-r51-0/.../~ $


And if you open it as user (ie. without sudo)

---

### Post by christopherbalz on 2009-11-13
Thank you.  It gives the same exact error message.

---

### Post by christopherbalz on 2009-11-22
Just to highlight how dead my sound is - no soundcards, no alsamixer.  Also OSS does not work either.

//cbalz-tp-r51-0/.../~ $ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
//cbalz-tp-r51-0/.../~ $ sudo aplay -l
aplay: device_list:217: no soundcards found...
//cbalz-tp-r51-0/.../~ $ sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
//cbalz-tp-r51-0/.../~ $

---

### Post by christopherbalz on 2009-11-24
Took the plunge and upgraded to 9.10, and that fixed it!

Note that at some point during the upgrade, I lost video.  After nine hours from the start of the upgrade, facing no video, I did a hardish reboot (hold down power key on this IBM R51 ThinkPad (circa 2004)) and ran recovery-mode / fix-broken-packages option twice.  

When asked during the fix-broken-packages cycles, I always took the clean version from the new install vs. my modified files (X, audio).  Then system asked to reboot on a text-only console log-in (no X) and I obliged.

Everything completely nice from then on: video, audio,

---

