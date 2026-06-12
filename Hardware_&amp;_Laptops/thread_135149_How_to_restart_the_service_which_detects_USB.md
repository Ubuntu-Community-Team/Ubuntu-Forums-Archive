---
title: "How to restart the service which detects USB?"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by soofsoof on 2006-02-23
I have ubuntu breezy. When the system is "fresh" all my usb devices (disk on key, mp3 player) are detected and operate well.

However, sometimes, when I connect the Palm (M515) and try to sync it, not only I cannot sync - it seams like the whole "usb system" crashes and new usb devices which I connect are no longer detected. It is needless to say that I cannot connect the Palm too in that case.

A reboot solves the problem, but hey, this is not why I use Linux for.

Apart from trying to figure out why this "usb detection system" crashes when connecting the Palm, I want to know how to restart it without rebooting every time.

Killing hald and restarting it again using sudo /usr/sbin/hald did not work.

Thanks.

---

### Post by 5-HT on 2006-02-23
What about trying: ```
 sudo /etc/init.d/hotplug restart 
``` then pluggin the Palm in?

*Note: It's a good idea to unmount any other removable media that aren't read-only prior to doing this 

I dislike automounting of drives myself, so couldn't be of much more help than that (it worked for me in the past), but there should be lots of threads to do with gnome-volume-manager and automounting probs that may be of help.

HTH

---

### Post by soofsoof on 2006-02-23
Sorry, but that's not it (or at least not the only problem...).

Thanks anyway.

---

