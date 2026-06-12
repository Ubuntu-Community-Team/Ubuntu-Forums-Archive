---
title: "All Browsers in crash!"
date: 2004-12-23
forum: General Help
---

### Post by Smash on 2004-12-23
Hello, when i try to open a webpage with Firefox, or Mozilla, or Epiphany etc.. i get this error:

```
*** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
*** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
Segmentation fault
```

When i try to run Thunderbird, this is the error:

```
selected locale: en-US
 ***** Registering: Clean Compreg! ****
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 451:  4765 Segmentation fault    "$prog" ${1+"$@"}
```


This happens when i run them as user.
Now i'm writing this post as root.

---

### Post by Rancoras on 2004-12-23
What changed?  We're they ever working?

---

### Post by Smash on 2004-12-24
I updated them from Hoary repository, and they were ok.
Now, without reasons, they crash, ONLY if i run them as user.

Maybe i've installed some libraries that is not compatibile, but i can use it as root.

---

### Post by Rancoras on 2004-12-24
In the future, make sure to put all the information about the problem in your initial post.  It makes it easier to diagnose.

That's why it isn't a good idea to mix warty and hoary.  Hoary has diverged quite a bit from warty at this stage.  If you want updated packages, a better idea is to use the backports projects packages.

[http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)

If you can, revert to only warty packages, if not then you probably need to reinstall.  This may sound harsh, but consider it a lesson learned.

---

