---
title: "Changing lid close behaviour when an external monitor is plugged in?"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by simplyw00x on 2008-01-18
I'd like to change what laptop does when the lid is closed, but only when an external screen is plugged in. Hence, solutions like [http://www.thinkwiki.org/wiki/How_to_configure_acpid](http://www.thinkwiki.org/wiki/How_to_configure_acpid) and [http://ubuntuforums.org/showthread.php?p=501292&posted=1#post501292](http://ubuntuforums.org/showthread.php?p=501292&posted=1#post501292) are not complete as they change behaviour in general, and I'm quite happy with the result when no monitor is plugged in. 

Ideally I'd like to switch to a modeline (I use nvidia-glx) with only the CRT, but simply not blanking the CRT would be a good start. Are there any solutions, and crucially any solutions that are ubuntu-ish, i.e. not nasty hacks (as this is something that should be part of the OS) and even Windows does this properly (when ACPI even works, that is).

Any help appreciated.

Carl.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/23220](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/23220)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/178665](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/178665)

---

### Post by jerrykenny on 2008-01-18
most convenient way is to goto system-prefernces-powermanagement, and change the behaviour there

---

### Post by simplyw00x on 2008-01-18
*sigh* this doesn't have settings for external monitor behaviour.

---

