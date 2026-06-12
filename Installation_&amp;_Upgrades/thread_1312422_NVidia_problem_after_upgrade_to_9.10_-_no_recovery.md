---
title: "NVidia problem after upgrade to 9.10 - no recovery"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by paulkater on 2009-11-03
I upgraded my laptop from 9.04 to 9.10.
Boot goes well, but even before logging in there is a weird moving line at the top of the screen. After logging in, after several seconds the graphics screen goes haywire.
Now I did find an option or two to fix it but I have not time to open an xterm to enter the needed commands.
An extra problem is that when I select 'recovery mode', the boot hangs after loading all kinds of modem-drivers. I left it at that for over 10 minutes, but no joy.

Is there a way to fix that, except going back to 9.04?

Thanks

---

### Post by tomBorgia on 2009-11-03
> **paulkater said:**
> 
Now I did find an option or two to fix it but I have not time to open an xterm to enter the needed commands.

Before logging in press ctrl-alt-f1 (or any f-key, except 7 & 8 ) and you'll get to a bash login prompt... you can then login at the command line and enter the commands you'd enter in the xterm.

Good luck!

---

### Post by paulkater on 2009-11-03
Magical! Thank you.

---

