---
title: "Mouse left click non-functional"
date: 2014-02-21
forum: Hardware
---

### Post by pasjoman on 2014-02-21
set up: 13.10 32 bit Ubuntu on a Lenovo x220
background: I  let my laptop go into sleep mode while streaming videos in chromium. Later I logged in, and was unable to left click to exit full screen. 
I was able to Esc out, but realized that my left click was completely non-functional. The cursor moves correctly, but Unity and most programs other than chrome don't seem to respond to hover over as they normally would. 

I have tried:
[LIST]
[*]Plugging in a tested functional USB mouse. same problem
[*]Rebooting the computer. no dice
[*]switching primary to right click - works but has strange behavior, like a left click + middle button. Not functional in Unity.
[*]```
modprobe -r psmouse
```   ```
  modprobe psmouse
```      nothing
[*]```
xev
``` - shows nothing for left click
[/LIST]

Haven't tried booting from a LiveCD yet. It'd be a pain to get that set up, but I'll do it if that's the best course of action

I've looked through these forums and haven't seen any problems quite like this. Any ideas?

Thanks

---

### Post by pasjoman on 2014-02-21
For posterity.. it seems that there was a hardware problem with the Thinkpad Trackpoint's left button. I disabled the trackpoint in BIOS and that solved all issues with external USB mouse, and I'm able to use the the trackpad as well.

---

