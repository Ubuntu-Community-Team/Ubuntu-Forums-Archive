---
title: "Hotmail on Firefox / Linux"
date: 2008-10-27
forum: General Help
---

### Post by Xinef on 2008-10-27
Recently, I came across a problem on all my linux machines:
I couldn't directly access my hotmail box directly, I always got an error message telling me to install IE, Firefox or Safari to access hotmail, forcing me to click on a link to get the "classic" version (in short: the old one).
I do not mind the older version, but having to click on a useless link each time I wanna check my mail was getting frustrating.
Most places reported that the problem came from the "general.useragent.vendor" variable which hotmail needs set to "Firefox" and that linux distros set to their own name ("Ubuntu", " Fedora" ...)
After trying overwriting it, it appeared that each time firefox restarts, this value is restored. So configuring this variable through about:config is not an option.
Here is the easy way I found so far:

1. close firefox and go to ~/.mozilla/firefox/********.default/
2. create a file called user.js
3. insert this line:
```
user_pref("general.useragent.vendor", "Firefox");
```
4. restart firefox and enjoy the newest hotmail version

I post this here because I couldn't find a similar forum post, and secondly in general help because I did not see where else this should be posted in.

---

### Post by kavon89 on 2008-10-28
Try a user agent changer. It will make your browser look like another browser to get past those stupid requirements.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by BLTicklemonster on 2008-10-28
Sweet. Thanks for the info. That's been bugging me for a while. Update to FF3.0, hello? I'm running 3.0.3 already! Now they think I'm running IE7 for vista, woot woot.

Oops, using the plugin, when I get to my mail, I can't open any. I'm going try the first trick now, see what happens. Okay, did it, that works. Odd.

---

### Post by d_skillz on 2008-10-28
> **kavon89 said:**
> Try a user agent changer. It will make your browser look like another browser to get past those stupid requirements.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

I had no idea that add-on existed, thanks

---

