---
title: "Opening Firefox from Bluefish"
date: 2008-10-25
forum: General Help
---

### Post by Wangsta on 2008-10-25
I just started using Bluefish, and I wanted to use the "View in Browser" button described here:
[http://ubuntuforums.org/showthread.php?t=485246](http://ubuntuforums.org/showthread.php?t=485246)

I followed the advice and it worked! However, when my firefox opens a php file from my harddrive, it goes into a "What should firefox do with this file?" mode.  Only when the php file is prefixed by localhost/... etc, does it really read it.

```
/usr/bin/firefox -new-window "%s" &
``` apparently %s is the full file path. how could i get it so that the file path is relative to where it's placed in my website folder?:confused:

---

### Post by Wangsta on 2008-10-26
any other notation i can use?

---

### Post by cyberjean on 2009-11-26
> **Wangsta said:**
> 
I followed the advice and it worked! However, when my firefox opens a php file from my harddrive, it goes into a "What should firefox do with this file?" mode.  Only when the php file is prefixed by localhost/... etc, does it really read it.

```
/usr/bin/firefox -new-window "%s" &
``` apparently %s is the full file path. how could i get it so that the file path is relative to where it's placed in my website folder?:confused:


Hi,

you must create a new "project". Set the base dir to your appache DefaultRootDir (i.e. where your www directory is), including the final backslash. Set the "preview url" to localhost/ and voila!

Jean

---

