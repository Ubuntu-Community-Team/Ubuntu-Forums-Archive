---
title: "Can I make a keyboard shortcut connect with a sound effect?"
date: 2008-09-06
forum: General Help
---

### Post by kestal on 2008-09-06
call me cliche, but I like the mac os almost as much as I like Ubuntu. I have used mac for a while and I now love Ubuntu. As little of a thing this actually is, I miss the little sound effect during volume up/volume down. So I set up the keyboard shortcut, is there any way to specifically have a sound effect for those shortcuts?

---

### Post by Genius314 on 2008-09-06
The only way I would know how to do this would be with Compiz.
Something like this might work:
1. Disable the volume keys in System>Preferences>Keyboard Shortcuts.
2. Use Compiz's commands to run a script when those keys are pressed.
The script would then either increase or decrease the volume, and play a sound effect.

I can't help at all with the script, though. :(

---

### Post by kestal on 2008-09-06
Thanks for pointing me in the right direction.. though I currently have no experience with knowing what commands to put in, also how to put in sound for it. :(

---

### Post by kestal on 2008-09-10
anyone?

---

### Post by kestal on 2008-09-11
*sigh*

So nobody can tell me how to connect a sound to a keyboard shortcut that deals with volume (while keeping the graphical volume display that pops up when setting volume with 'keyboard shortcuts' over compiz?)

Does anyone know how to access the visual display for volume in Ubuntu?

---

### Post by Whiffle on 2008-09-11
I don't know how to access the visual display, but you could easy write a small script for this.  Something like:

```

#! /bin/bash

aumix -v +2 
aplay sound.wav

```

Its quick and dirty, but it might work.  All you'd have to do is make it executable, save it somewhere convienient, and then link it to a keyboard shortcut.

---

### Post by kestal on 2008-09-12
> **Whiffle said:**
> I don't know how to access the visual display, but you could easy write a small script for this.  Something like:

```

#! /bin/bash

aumix -v +2 
aplay sound.wav

```

Its quick and dirty, but it might work.  All you'd have to do is make it executable, save it somewhere convienient, and then link it to a keyboard shortcut.

Thanks. Thats also a good start for me to start tinkering. I just really like the visual display ;) hehe.

---

