---
title: "[SOLVED] New windows appear behind old ones"
date: 2008-09-22
forum: General Help
---

### Post by the real omni on 2008-09-22
Ever since I've switched from Windows to Linux months ago, there's been a small irritant.

Occasionally when I bring up new windows, they appear behind the currently-focused window, instead of appearing in front of it.

The new window also steals the focus, so I can't even just alt-tab to bring it up.. I have to alt-tab and then alt-shift-tab to bring the new window up. Definitely an irritating bug!!

There's another reference to this bug in the archives (though with less detail):

[http://ubuntuforums.org/showthread.php?t=577010](http://ubuntuforums.org/showthread.php?t=577010)

Can anyone tell me how to squish this bug?

---

### Post by ashmew2 on 2008-09-23
I assume you are using Compiz. Install the Compizconfig-settings-manager.
```

sudo apt-get install compizconfig-settings-manager
```

Look for a setting called "Focus Stealing Prevention Level" and set this to Low.
I cant tell u exactly where it is cuz i am updating my system and so cant install the compiz settings manager..Do let me know what happens!

---

### Post by the real omni on 2008-09-23
> **ashmew2 said:**
> I assume you are using Compiz. 
Look for a setting called "Focus Stealing Prevention Level" and set this to Low.


Ok I've changed it from the default setting of "Low" to "Off" and it seems to have stopped stealing focus. 

It was an intermittent problem to begin with, so if it's not fixed I'll play around with the levels and if none of them work I'll post again. :) If the problem stays fixed for a few days I'll post this as resolved. 

Many thanks!

---

### Post by the real omni on 2008-09-23
Ok looks like I spoke too soon.

Within mere minutes the problem has demonstrated itself to still be present.

Here's something interesting though:

With focus stealing prevention set to "Off" my pidgin window and other windows that were appearing in the background before now appear on the top level.

With focus stealing prevention set to any other setting, those windows would be among the ones that come up in the background.

Currently, with 'focus stealing prevention' set to 'off', new windows appear on the top EXCEPT windows related to Thunderbird, which I suspect is related to another bug Thunderbird has been plaguing me with. (Specifically, the window is stuck in maximized mode with no window decoration or minimize/maximize/close buttons at the top. If I alt-space and choose "move" or "resize" nothing happens at all.)

So, I'mma mark this as resolved and focus on getting thunderbird fixed.

Many thanks! :)

---

### Post by the real omni on 2008-09-23
Oh, one last follow-up post:

For others experiencing this issue, the fix is indeed to change the "Focus Stealing Prevention Level" setting, and that setting is found in the General Options within the Advanced Desktop Effects applet in the System Preferences menu.

---

