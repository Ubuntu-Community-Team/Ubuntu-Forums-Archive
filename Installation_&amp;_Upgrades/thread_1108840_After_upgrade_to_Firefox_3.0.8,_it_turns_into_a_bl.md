---
title: "After upgrade to Firefox 3.0.8, it turns into a blank grey window"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by sorill on 2009-03-28
Hi there!

This morning update manager presented me with som security upgrades (running Ubuntu 8.04, with the xubuntu-desktop package on top), including several firefox packages to 3.0.8.

After installation and restart of Firefox, the all that appears is a grey window with the title Mozilla Firefox, a blank menu bar without any items and a big grey space. (Actually, the little "flower" in the top right corner that indicates that a page is loading is still there too.)

Starting from the command line gives no output, and reinstalling does not help :(

Among the upgrades was also xulrunner 1.9.0.8. Just mentioning this because I read about another Firefox problem related to xulrunner in the past.

If nothing helps, at least I just installed epiphany... :)


Best regards,

   s.

---

### Post by Lage on 2009-03-28
I had the same problem, which really frustrated me, because my natural reaction is to go to Ubuntuforums and check for answers. Catch 22.

I tried restarting Firefox several times, before it struck me that I could try rebooting the whole computer, which worked!

It seems I have stopped thinking like a Windows user, where rebooting would have been the first option in any case... even if no problems arise! =)

Hope this works for you too.

---

### Post by sledhead45 on 2009-03-28
I applied the updates this morning and had an issue too. the update crashed with:
```
E: xulrunner-1.9: subprocess post-installation script returned error exit status 127
E: firefox-3.0: dependency problems - leaving unconfigured
E: firefox-3.0-branding: dependency problems - leaving unconfigured
E: ubufox: dependency problems - leaving unconfigured
```

leaving my firefox installation broken, and restarting the computer didn't help.
I tried clearing out my apt cache and re-downloading and installing the xulrunner-1.9, but no luck, same errors.

To fix i had to use the "force version" in synaptic package manager to the older version, that brought my firefox back to life so i could post this message. I'm leaving that update un-applied at this point. I hope it gets fixed.
If anyone wants my system details, please ask and I'll promptly provide.

---

### Post by sorill on 2009-03-29
Lage:

[quote="Lage"]It seems I have stopped thinking like a Windows user, where rebooting would have been the first option in any case... even if no problems arise! =)[/quote]

This morning it started working for me too, probably becuase I turned the machine off for the night. I'm glad it was that simple, but I feel ashamed for bothering you guys!

I second to the above said :)


sledhed45: That looks like something more serious! My update didn't generate any error messages. Hope somebody has an idea.



Best regards

   s.

---

### Post by infoseeker on 2009-03-29
Logging off and then back on got mine going.

---

### Post by skiwithpete on 2009-03-29
Mine keeps crashing too.

Restart didn't help.  Don't know what is wrong with it.  Am hoping I can upload this message before it crashes again.

Only started happening after the upgrade to 3.08

P

---

### Post by sledhead45 on 2009-03-29
skiwithpete: use your synaptic package manager to revert to older packages if you need to. I believe the one i mentioned above and "firefox-3.0" are the 2 packages effected in the update. Good luck

---

### Post by uzusan on 2009-03-30
This happened to me as well.

I removed the following package and the 2 firefox dependancies, and 3.0.8 worked again:
xulrunner-1.9-gnome-support

---

