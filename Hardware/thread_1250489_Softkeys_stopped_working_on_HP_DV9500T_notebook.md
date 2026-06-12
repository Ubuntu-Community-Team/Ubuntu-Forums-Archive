---
title: "Softkeys stopped working on HP DV9500T notebook"
date: 2009-08-26
forum: Hardware
---

### Post by tgeer43 on 2009-08-26
Couldn't decide whether to put this is Multimedia or here but since it may be an HP notebook issue, I decided on this forum.

In all prior releases of Ubuntu up to and including 9.04 32-bit, the blue LED softkeys on my HP DV9500T did not function at all and in fact were not even recognized as keypresses. When I switched to 9.04 64-bit I was delighted to find that they were now functional.

Until today, that is. :(  I really only use the volume up/down and mute keys. Upon booting up this morning I found that they were no longer controlling the sound. The on-screen display still comes up when pressing the keys and the volume slider and mute indicator appear to work but have no effect on the sound output. Xev recognizes the keystrokes properly and System->Preferences->Keyboard Shortcuts shows them correctly configured and recognizes the keystrokes as well. They're just not making it through to the sound hardware.

I did some updates a day or two ago and hadn't used the softkeys since then so it might be related but I don't see anything in /var/log/apt/term.log that sticks out.

Also, I run deborphan, apt-get clean/autoclean/autoremove regularly with a cron script. Could I have inadvertantly removed a needed package? If so, which one(s)?

I could really use some help on this one. I kinda got spoiled with the keys finally working and miss them sorely.

Thanks in advance,

tgeer

---

### Post by sergiom99 on 2009-08-26
theres a hotkey-setup package for you to install.

---

### Post by tgeer43 on 2009-08-26
Alas, hotkey-setup is installed by default. I had even tried completely uninstalling it and it's config files then reinstalling.
No joy. :(

tgeer

---

### Post by sergiom99 on 2009-08-26
what about keytouch?
Mine worked out of the box since Hardy and it still does.

I only had to install lirc for the remote control.

---

### Post by tgeer43 on 2009-08-26
Nailed it! :P

System->Preferences->Sound: The Default Mixer Tracks Device had gotten set to Pulseaudio instead of Alsa Mixer. Changed it back and the audio softkeys are once again working. Yeah.

It must have been an update that changed this because I sure didn't and I haven't even run any new audio related apps or utils either.

tgeer

---

