---
title: "Sound help"
date: 2008-10-16
forum: General Help
---

### Post by Chamillionaire2 on 2008-10-16
Hello,

ok basically my audio works fine apart from it will only provide sound for one thing at a time,

if i start banshee player first then lets say world of warcraft i would hear my music but not wow,

again if i start wow first then i start banshee i would hear wow but not banshee.

it does it with al sound apps not just wow and banshee.

Anyhelp?

---

### Post by beno1990 on 2008-10-16
This sounds like a Pulseaudio problem to me.

Try going to System -> Preferences -> Sound -> and change everything under sound events, sound playback, and audio conferencing to "PulseAudio Sound Server", and the "Default mixer tracks" to whichever one has "Alsa mixer" in brackets, if there is one.

Log out, log back in, and hopefully it should work.

---

### Post by Chamillionaire2 on 2008-10-16
> **beno1990 said:**
> This sounds like a Pulseaudio problem to me.

Try going to System -> Preferences -> Sound -> and change everything under sound events, sound playback, and audio conferencing to "PulseAudio Sound Server", and the "Default mixer tracks" to whichever one has "Alsa mixer" in brackets, if there is one.

Log out, log back in, and hopefully it should work.

Damb, still dident work, any other ideas?

---

### Post by beno1990 on 2008-10-16
You might just need to install some more packages for the Pulseaudio server.

Firstly, keep all of the settings in System -> Preferences -> Sound pointing to PulseAudio. Next, open the terminal and install the following:

```

sudo apt-get install paman paprefs pulseaudio-*

```

This will install all of the PulseAudio packages, and some management/preferences packages.

Once it's installed, go to Applications -> Sound & Video -> PulseAudio Device Chooser.

This might not open a window but it should open a panel icon where you can configure the server. Make sure it's pointing to the right server, source and sink (usually it gets it right with default).

After that, you might want to reboot. Your applications might each have their own audio settings too; just make sure they all point to PulseAudio if that's the case.

---

