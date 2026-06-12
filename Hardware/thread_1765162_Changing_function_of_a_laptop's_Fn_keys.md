---
title: "Changing function of a laptop's Fn keys"
date: 2011-05-22
forum: Hardware
---

### Post by msyriac on 2011-05-22
At the moment, Fn + left/right arrow keys adjust my screen's brightness. And the volume from my Acer Aspire (2930Z) is controlled by an archaic mechanical dial which has stopped registering clockwise and anti-clockwise motions correctly - which means that when I try to decrease the volume, it sometimes increases it!

So, I want to associate Fn + up/right arrow keys with volume so I don't have to use the broken dial any more. Any ideas how I can do this?

---

### Post by zia.newversion on 2011-05-22
Welcome to the Ubuntu Forums.

I would have tried this on my laptop first but I am sorry, I have all the keys already set up for something or the other. So I am not 100% sure it would work, but it just might.

Very easy, if you are in the Ubuntu classic desktop, you just go to System - Preferences - Keyboard Shortcuts. In the dialog, the second / third or so are the keyboard shortcuts for Volume Up / Down / Mute etc etc... Against them is the shortcut key assigned to these shortcuts. You just double click on whatever is previously assigned and then press the desired key combination (Fn+Up or whatever)... I guess that'd settle it.

If you are in Unity desktop, or the default desktop of Natty (11.04) with the funky sidebar on the left side, you can click on the Ubuntu Icon on the top left of screen and type in Keyboard Shortcuts, and there you have it.


Just in case
------------:
However, if that doesn't work, I do know another method. But I am not so good at describing it. Maybe someone else will hook you up. I can give a hint though. It's something about changing the configuration files for your keyboard (maybe fiddling with the keyboard map file) and in there you set the Fn+<Key> for the desired system call, like alsa_volume_up or alsa_volume_mute etc... That's advanced but failsafe... Too bad I cannot describe it all because I don't remember the configuration files or where they are located.
The first one should work though... Because it does on my system.

And don't forget to mark the thread solved when it indeed is solved.

---

### Post by msyriac on 2011-05-22
Oh thanks! I was completely unaware there was a "Keyboard shortcuts" dialog.

Anyhoo, that dialog doesn't recognize the Fn key so I can't set it to how I originally wanted it. This is of course not of much concern to me - I've configured volume to the Meta + up/down association and I'm happy with that.

I'm going to leave this thread as unsolved until someone explains how to set the association with the Fn key.

---

### Post by zia.newversion on 2011-05-22
Just wondering. What's ```
Meta?
``` :???:
There's one Mod4 on my laptop which actually is the Windows key...

---

### Post by msyriac on 2011-05-22
Yes, Mod4, Super, Windows, however you want to call it :)

---

### Post by zia.newversion on 2011-05-22
So *that's* Meta, *too*? LOL.
Got it. Thanks.

---

