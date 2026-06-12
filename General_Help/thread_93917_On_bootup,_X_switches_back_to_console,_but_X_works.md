---
title: "On bootup, X switches back to console, but X works"
date: 2005-11-23
forum: General Help
---

### Post by fourhead on 2005-11-23
Hello, I hope somebody can help me. I don't know what I've done, but suddenly whenever I boot my iBook, the system loads fine, then X starts, but switches back to the console shortly after. But X is working, when I press Crtl+Alt+F7 I'm in KDE. So its not that X is not working, it's just that for some reason X switches back to the console again. The only thing that I've manually changed in xorg.conf was to comment out the synaptics touchpad section, because it would always tell me that it can't be found.

Any ideas what might be wrong?


Tom

---

### Post by mlomker on 2005-11-23
What console does it switch you to?  Is it a fresh login prompt or do you see stuff on the screen about KDE loading?

There are a bunch of files under /etc/X11 and /etc/kde that can modify consoles, such as kdmrc, but if you didn't change them...

---

### Post by fourhead on 2005-11-23
Its switchting back to tty1, there nothing on the screen except the login prompt. Well now I found ou this actually does not happen always, it just happens sometimes.


Tom

---

### Post by GoldBuggie on 2005-11-23
Not that this is of any solution...but I do know that I had that very same problem when upgrading to breezy. Since then I've managed to change the bootup and done some ofter things and now the problem is no more(at least haven't seen it in a while..still don't know if it is lurking to come out). 

So it isn't just you..that was what I wanted to say. Haven't seen a specific solution yet but let's hope it solves for you with time. Seen some threads about others with the same trouble. But they thought that X wouldn't start since they didn't try the f7 thing.

---

### Post by fourhead on 2005-11-24
Well, actually I was tweaking the boot process a little, removing things I don't need, turning everything except tty1 off etc, and I laso haven't seen this for a while now, I've rebootet a lot, and it didn't happen again so far, so perhaps I've also magically "solved" it somehow. Thanks!


Tom

---

