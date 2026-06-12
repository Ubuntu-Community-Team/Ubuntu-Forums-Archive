---
title: "Firefox will not open"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2009-10-31
I tried to upgrade Firefox to version 3.5.4 through Ubuntuzilla.  All appeared to function well with all the proper prompts to the end.  When I tried to open Firefox, I only get the rotating circle symbol and nothing happens.  I tried [sudo dpkg-reconfigure firefox] and there were no errors.  What am I missing?

---

### Post by -=Stefan=- on 2009-10-31
Did you try to open firefox via console?
If there's an error, you'll be able to see it that way!

---

### Post by gilloz on 2009-10-31
Thanks Stefan for your reply.  I'm embarrassed to ask what do you mean by "console"?  Are you referring to the Terminal?  I first tried the icon on the Desktop, then I went to applications and tried it from there.  Nothing happens in both cases.  I also notice that the Synaptic Package does not show the upgrade of Firefox 3.5.4.

---

### Post by -=Stefan=- on 2009-10-31
> **gilloz said:**
> Are you referring to the Terminal?
Yes, sorry for my strange vocabulary, i'm not a native English speaker ;)

If you type "firefox" in a Terminal (e.g. xterm) you might get an error message which would help to fix the problem (e.g. like "Couldn't load XPCOM" which would mean that you have  to update xulrunner).

---

