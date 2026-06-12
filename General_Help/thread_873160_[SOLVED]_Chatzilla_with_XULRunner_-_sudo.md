---
title: "[SOLVED] Chatzilla with XULRunner - sudo"
date: 2008-07-28
forum: General Help
---

### Post by strykrforce on 2008-07-28
So, after following the instructions here: [http://chatzilla.rdmsoft.com/xulrunner/]("http://chatzilla.rdmsoft.com/xulrunner/") to install Chatzilla with XULRunner, I ran into a problem.

Running Chatzilla with the command "/usr/lib/chatzilla/chatzilla" does nothing unless I have run something in sudo before. If I have used sudo recently, "/usr/lib/chatzilla/chatzilla" give me a runtime error:

```
NS_ERROR_FILE_ACCESS_DENIED: Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.create] @ <chrome://chatzilla/content/lib/js/file-utils.js> 273
+ QueryInterface (function) 3 lines
+ message (string) 'Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.create]'
+ result (number) 2152857621
+ name (string) 'NS_ERROR_FILE_ACCESS_DENIED'
+ filename (string) 'chrome://chatzilla/content/lib/js/file-utils.js'
+ lineNumber (number) 273
+ columnNumber (number) 0
+ location (object)
+ inner (object) null
+ data (object) null
+ initialize (function) 3 lines
*
```

Everything works fine if I type "sudo /usr/lib/chatzilla/chatzilla". The problem is that I'd prefer not to run Chatzilla with root permissions.

Any solutions?

Thanks.

---

### Post by y-lee on 2008-07-28
This is a permission problem did you run either of the xulrunner commands as root?

---

### Post by strykrforce on 2008-07-28
I used the XULRunner from apt-get and ran both commands as root, because running them without sudo doesn't appear to do anything in "/usr/lib".

I also followed the steps in this tutorial: [http://ubuntuforums.org/showthread.php?t=299991&highlight=chatzilla]("http://ubuntuforums.org/showthread.php?t=299991&highlight=chatzilla") and added the permissions.

SIDE NOTE: Running with "gksudo" instead of "sudo" is fine for a launcher, but it stores everything in "/root" instead of "/home/<user>".

---

### Post by y-lee on 2008-07-28
did you also run

```
sudo chmod a+rx chrome/*
```

in the same directory as suggested in [post 2]("http://ubuntuforums.org/showthread.php?t=299991&highlight=chatzilla")


I haven't installed chatzilla but your error messages suggest a permission problem some file needed has root permissions.

---

### Post by strykrforce on 2008-07-28
Yes, I also ran that command.

Using```
ls -l
```shows that "/usr/lib/chatzilla" and all its files and subdirectories have either ```
-rwxrwxrwx
``` or ```
drwxrwxrwx
``` properties.

---

### Post by y-lee on 2008-07-28
hmm does chatzilla keep any files or directories hidden in your home directory? if so check them too.

---

### Post by strykrforce on 2008-07-29
After running chmod and chown on everything in ~/.chatzilla, it works perfectly. No idea why everything was owned by root. Maybe it's because I ran XULRunner with sudo.

Thanks!

---

### Post by mykmelez on 2008-11-12
> **strykrforce said:**
> After running chmod and chown on everything in ~/.chatzilla, it works perfectly.

Note: for the Chatzilla 0.9.83 package available from [http://chatzilla.rdmsoft.com/xulrunner/](http://chatzilla.rdmsoft.com/xulrunner/), the specific files with incorrect permissions are the following (inside the /usr/lib/chatzilla directory):

[LIST]
[*]chrome/chrome.manifest
[*]defaults/preferences/update-prefs.xr.js
[*]chrome/icons/default/chatzilla-window16.xpm
[*]chrome/icons/default/chatzilla-window.ico
[*]chrome/icons/default/chatzilla-window.xpm
[/LIST]

All these files should be set to permissions 644 (-rw-r--r--), i.e. the owner (root) has read and write access, while the group and others have only read access:

```
cd /usr/lib/chatzilla
sudo chmod 644 chrome/chrome.manifest defaults/preferences/update-prefs.xr.js chrome/icons/default/chatzilla-window16.xpm chrome/icons/default/chatzilla-window.ico chrome/icons/default/chatzilla-window.xpm

```

I have reported the permissions problems to the package maintainer.

Note also that XULRunner 1.9, a stable release (the same code used in Firefox 3; see [https://developer.mozilla.org/en/XULRunner](https://developer.mozilla.org/en/XULRunner) for more info) is now available from the package repository in the package xulrunner-1.9.  It's probably preferable to the older version of XULRunner in the xulrunner package, since a bunch of Linux compatibility fixes went into Firefox 3 (and hence XULRunner 1.9).

> **strykrforce said:**
> No idea why everything was owned by root. Maybe it's because I ran XULRunner with sudo.

Yup, I see that behavior too.  Strange, I would think running Chatzilla as root would create /root/.chatzilla, but apparently when running it as root via sudo it creates /home/YOU/.chatzilla instead.

---

### Post by mykmelez on 2008-11-17
Note: Chatzilla 0.9.84 is now available (from the [Chatzilla on XULRunner web site]("http://chatzilla.rdmsoft.com/xulrunner/")), and its files all have the correct permissions, so there's no need to fix them.

---

