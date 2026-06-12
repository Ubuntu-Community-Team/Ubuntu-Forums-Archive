---
title: "Weird compiz &amp; shortcuts problem"
date: 2008-08-22
forum: General Help
---

### Post by Znupi on 2008-08-22
Ok, here's my problem: I want to be able to resize a window using Alt+Button 3 (right click). Ok, opened CompizConfig Settings Manager, went to Resize Window -> Bindings and set "Initiate Window Resize" to Alt+Button 3. It said it conflicted with Window Menu in General Options. I don't need to be able to pop up the window menu by clicking Alt+Button 3, so I disabled that. The next thing that happened -- I couldn't click! Somehow, it set the shortcut for moving a window to simply Button 1, instead of Alt+Button 1. Why? And I couldn't change that from Move Window in CompizConfig Settings Manager, I had to go to System -> Preferences -> Windows, which looked like this:
[IMG]http://i80.photobucket.com/albums/j161/znupi/ubuntu/Screenshot-WindowPreferences.png[/IMG]
When I chose only "Alt" in there (using the keyboard), the shortcut for Window Menu changed back to Alt+Button 3.

After more testing it seems that if I set Initiate Window Resize to "<Anything>+Button3" it gets reset to "<Anything>+Button2" and Window Menu gets reset to "<Anything>+Button3". I tried setting Window Menu to "<Alt>+Button 9" (I don't have a button 9) but it reset to Button 3. At this point I'm like "WTF Compiz hates me :-("..

Anyone know anything about this problem?

---

### Post by RedfishBluefish on 2008-10-02
I can't really help, but the launchpad bug is [here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153626").

I have this problem too.

Update:
"Resolution" here: [http://forum.compiz-fusion.org/showthread.php?p=60424]("http://forum.compiz-fusion.org/showthread.php?p=60424").
Apparently it is not a bug, as such, but I would say there is a problem with the UI if this sort of thing can happen.

---

### Post by Znupi on 2008-10-02
Thank you very much :)

---

