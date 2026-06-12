---
title: "X or Gnome crashing repeatedly"
date: 2005-11-27
forum: General Help
---

### Post by LeSkip on 2005-11-27
I am having problems with X or Gnome crashing repeatedly. It generally starts with the cursor locking up, then disappearing. After 10 seconds or so the screen goes blank and I observe hard disk activity. Another 10 seconds later I see the cursor again for five seconds or so, before it goes blank again. Sometimes I see some screen noise. Then I get the cursor again for 5 seconds. Lather, rinse, repeat.

There seems to be no way to stop this. Ctrl-Alt-Backspace does nothing, trying to switch to a text mode console does not work.

This happens at least once a day, and at least once it occured when I launched Totem.

Hardware is an IBM Thinkpad X40. Could it be the X server?

Thanks!

Skip

---

### Post by Qrk on 2005-11-27
I had similar problems when I first used Breezy. It went away when I changed the x.org driver from nv to nvidia. 

I'd definatly try a different driver, though nvidia may not be the right one for you.

Change your x.org driver with 

```
sudo dpkg-reconfigure xserver.xorg
```

and follow the instructions.

---

