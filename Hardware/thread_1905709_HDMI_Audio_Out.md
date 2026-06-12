---
title: "HDMI Audio Out?"
date: 2012-01-07
forum: Hardware
---

### Post by mrmylanman on 2012-01-07
Hello all,

I have a custom-made PC which has an HDMI output.  I recently picked up an HDTV, and would like to just output all audio to it, since I am going to use this as an HTPC of sorts.

I was unable to get HDMI audio output to work through the tools available in Unity, so I dug deeper.  I used the command 'aplay -l' to get the full list of audio output devices, then used 'aplay -D' to play a test sound to find out which one actually was the HDMI audio output (there were 4 listed in 'aplay -l'.

I found out that the values I needed are; card 1, device 7.

So I created an ~/.asoundrc file, per the [ArchLinux Wiki]("https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#HDMI_Output_Does_Not_Work").  The contents of my ~/.asoundrc file is:

```
pcm.!default {
    type hw
    card 1
    device 7
}
```

Still, audio does not work after a restart.  I can get the test to work, however.  I have a feeling Unity may be overriding the settings in my .asoundrc file, but I'm not positive.

Anyone have any tips?

Thanks!

---

### Post by mrmylanman on 2012-01-07
I guess I didn't check the new settings deep enough.  I got thrown off by the fact that you have to set sound settings in a few places...

Solved now.

---

