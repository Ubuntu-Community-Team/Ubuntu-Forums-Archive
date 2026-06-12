---
title: "Ubuntu Natty No Sound on My Laptop"
date: 2011-06-06
forum: Hardware
---

### Post by kaqfa on 2011-06-06
Hallo friends, I have problem with my sound after installing Ubuntu 11.04.
Okay I've installed it once and all hardwares seem fine, and then I remove my Natty and install OpenSuse 11.4. I separate my /home folder into different partition so that I do not need to back up my document when I format the root partition.

And now I remove my Celadon and back to Natty (without formating /home directory). And this time my sound driver is detected as always, but no sound at all.

This is link to my alsa information [http://www.alsa-project.org/db/?f=8d9a9d57f1c5a01fa99551a0f584fa76b074af0e](http://www.alsa-project.org/db/?f=8d9a9d57f1c5a01fa99551a0f584fa76b074af0e)

Anybody can help me?
Thank you before.

Note: I can still play mp3 and movie files well but with no sound

---

### Post by Yellow Pasque on 2011-06-06
Let's start with the obvious. Make sure nothing is muted:
```
alsamixer
```
Also, you might have corrupted pulseaudio user config in your /home from your previous install(s).
```
cd ~
rm -rf .pulse*
```
Log out and back in.

---

### Post by kaqfa on 2011-06-06
Thank you for the reply....

It works now. But the funny thing is I don't even do anything, it just work after I reboot. And I'm sure last time there is nothing muted in alsamixer.

---

### Post by gaelicdarkwater on 2011-09-19
I had a similar problem.  Mine seems to randomly switch which output source it's using.  Since i only have speakers plugged into ONE source (USB), sometimes I have sound, sometimes I have to remind it.  I went through searching everything once, only to feel stupid when I went back to basics and found it had switched itself.  Now I check sound in the system folder first.  lol

---

### Post by maul9999 on 2011-09-19
> **kaqfa said:**
> Hallo friends, I have problem with my sound after installing Ubuntu 11.04.
Okay I've installed it once and all hardwares seem fine, and then I remove my Natty and install OpenSuse 11.4. I separate my /home folder into different partition so that I do not need to back up my document when I format the root partition.

And now I remove my Celadon and back to Natty (without formating /home directory). And this time my sound driver is detected as always, but no sound at all.

This is link to my alsa information [http://www.alsa-project.org/db/?f=8d9a9d57f1c5a01fa99551a0f584fa76b074af0e](http://www.alsa-project.org/db/?f=8d9a9d57f1c5a01fa99551a0f584fa76b074af0e)

Anybody can help me?
Thank you before.

Note: I can still play mp3 and movie files well but with no sound

You will have to click sound volume control then go to setting.  Enable sound device that you will use it most.  Intel HD audio is the problem, because it is not for Linux.

---

