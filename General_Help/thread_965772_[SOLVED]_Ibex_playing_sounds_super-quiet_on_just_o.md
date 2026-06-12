---
title: "[SOLVED] Ibex playing sounds super-quiet on just one of the accounts"
date: 2008-10-31
forum: General Help
---

### Post by Tuxoid on 2008-10-31
I installed Ibex right when it came out. Made sure everything was working, tested some new features out, and eventually realized sound was playing back really quiet. I was very frustrated, and immediately started to look into it. Both the gnome and kde network monitor were attempting to run at on gnome and kde. After everything was loaded after log-in, a KDE error message stating that the sound server had crashed due to a cpu overload.
This was the first suspicion I had to the possible reason. Due to this being a KDE error message, and the KDE network monitor had already tried to start while I was running Gnome, I figured kmix could have been trying to start as well. Therefore, I decided to uninstall every KDE package I could find, as well as purge configuration files for each one, and restart after. So I restarted, cranked my volume up to full on each option, and tried to play some audio.

So I could then faintly hear audio (and I mean very faintly). So then I decided to see if the problem was affecting the guest account, or my brother's. Oddly enough, the sound was playing at the correct volume on my brother's account, and the guest account, so I started to think that this is beyond weird. At that point, I started scrounging my home folder for configuration files, and had little idea what to look at.

So, what is it that could be going? Why can't I get decent volume on my account, but every other account is fine?

Is there any files or documentation that anyone can point me to?

I have an HDA Intel sound card running on an LG P1 laptop

---

### Post by Tuxoid on 2008-10-31
Fixed it :D

I set all playback options in System>Preferences>Sound to Autodetect, instead of ALSA.

Problem solved :D

---

### Post by Tuxoid on 2008-11-01
Actually, it's not fixed completely. My wine applications are still playing audio very, very quietly when the volume is full. Again, wine apps are only near silent on my account; they are running at normal volume on my brother's account, and the guest account. I have tried all the different driver options under wine's Audio configuration. I have also tried ever hardware acceleration setting from Full to Emulation. I changed the sample rate from 44100Hz to 48000Hz. I even turned turned on driver emulation.

None of the stuff above fixed the overly quiet nature of my wine applications.

Given that there was a problem with my native applications and having low volume earlier, I started to think that the root of my problem could be my account specific configuration. In thinking so, I decided to copy the guest account's .pulse directory from /home/guest/.pulse to my account's home directory. The problem, unfortunately remained.

I have little idea what configuration files control user-specific sound settings, and I have little idea of where to find out. Is there anything that anyone can think of? Something I may not be seeing? What configuration files could I look at?

---

### Post by agentnixon on 2008-11-01
Try double clicking on the volume icon if you're under Gnome. Sliding the PCM slider up fixed it for me.

---

### Post by Tuxoid on 2008-11-01
My PCM is set to full volume already

---

### Post by cryptecks on 2008-11-01
I have this same problem, the volume on everything is ridiculously low, and I have all my sliders turned up.

---

### Post by Tuxoid on 2008-11-01
Is there an account-specific configuration file that I can look at?

I have looked a the differences between the guest account's configuration files, in the guest account's home folder, and compared them to my own account's configuration files. I noticed that my account had some additional files. .asoundrc and .asoundrc.asoundconf. I could not find these files in the guest account's home directory, or my brother's (even with hidden files shown), so I figured I could delete them from my account.
I deleted both files mentioned above from my account. This yielded no positive or negative effects; I still had same problem and symptoms with super-quiet wine apps.

so I looked at yet another difference between the guest account's home folder configuration files and my own account configuration files. the file, '.esd_auth' was showing up as a text file on my account. Therefore, I backed up this file to my SD Card, copied the same file from the guest account's folder over to mine, and rebooted. Again, nothing got better, nothing got worse.

Am I missing something? Is there anything else I can look at?

---

### Post by Tuxoid on 2008-11-01
Okay, at this point I have relocated everything in my home directory and restarted my system to get it to re-create all configurations from scratch. My wine apps are still as good as inaudible.

My Wine version is 1.0.1

---

### Post by Tuxoid on 2008-11-01
I have now gone to the point of firstly, completely removing (or purging) wine, removing my '.wine' directory and everything in it, reinstalling my applications, and seeing that, despite the complete removal of the .wine directory, the problem remains. I have found out that using EsounD with wine, instead of ALSA allows for audio that; while it may be playing at normal volume, it playing audio with an over 1 second delay, making a game like starcraft unplayable. Besides, if the account are capable of using alsa for wine, why the heck can't I?

---

### Post by Tuxoid on 2008-11-01
Fixed! compiled drivers from the alsa project :D :popcorn:

---

### Post by darinmiller@cableone.net on 2008-11-02
[Work around]

After upgrading to Ibex and wine 1.1.7, Starcraft sound was "scratchy" from opening screen thereafter.  After a 1 to 5 minutes of play, sound would disappear entirely.

Switching back to Wine 1.0.1 fixed the scratchy sound, but sound would still disappear after a few minutes of play.  Warcraft III sound worked perfectly.

Tried System | Preferences | Sound set to ALSA- same problem.  Finally, I tried the OSS driver in the Wine config menu and sound worked fine in both wine 1.0.1 and 1.1.7.

I will attempt the ALSA project recompile to see if "Wine ALSA" will work once again.

---

