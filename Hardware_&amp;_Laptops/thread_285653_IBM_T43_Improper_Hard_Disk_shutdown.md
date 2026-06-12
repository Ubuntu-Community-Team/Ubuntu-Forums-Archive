---
title: "IBM T43 Improper Hard Disk shutdown ??"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by ritalin_kid on 2006-10-27
Greetings Ubuntu community !

I am wondering, ever since I upgraded to Edgy, whenever my laptop ( IBM T43 1871 machine series ) shuts down or hibernates, my hard disk stops as if power to it has been abruptly cut; it makes a noise which generally only happens if I perform a hard shutdown on the machine. 
But, if I put my laptop in standby, the hard disk appears to stop normally and does not make said noise.

Maybe the head on the hard disk does not park properly during the shutdown process ?

This noise issue never happened to me when using Dapper, only when I upgraded to Edgy..can anybody offer any answers as to what is going on here ? I am hoping that there is no damage to my disk.

Thanks in Advance !

---

### Post by aiu on 2006-10-27
It's happening to me also on an Dell XPS Gen 2 notebook. I experienced this problem some time ago with earlier versions of Ubuntu and with others distros but when I upgraded to 6.06 LTS the problem was gone. Now with 6.10 it's back again! :mad: 

Please anybody can help? 

Thanks in advance!

---

### Post by esaym on 2006-10-27
Yea thats a bad noise.  Has something to do with how laptop harddrives are supposed to park the heads before a spindown.  If they don't they make that noise as it does an emergency park. I think they are only rated for a a few hundred of those (or atleast back in 2000 when I looked up all this stuff).  So the problem needs to be fixed.  I would guess it has something to do with acpi but if suspend is working then acpi should be too.  hmm 

Does it make the noise with the boot disk or do you only have the drapper disk?

Sorry I can't be of more help

---

### Post by ritalin_kid on 2006-10-27
I have only one hard disk in my laptop.
Dang, might have to reinstall 6.06 then :( I was looking forward to using 6.10 but if it kills my hard disk then I have nothing to use with Ubuntu :/

Thanks !

---

### Post by julioromano on 2006-10-27
[http://www.ubuntuforums.org/showthread.php?t=285969](http://www.ubuntuforums.org/showthread.php?t=285969)

Sorry guys, made a dup post.

As you can see there I tried to file a bug in launchpad in the upstart section but they rejected it, they say it's kernel's fault.

---

### Post by aiu on 2006-10-27
I was waiting like a mad man for 6.10 and now I need to roll back to 6.06. This is so not cool. I mean they fixed it in 6.06 and they don't care about it in 6.10? Why?

---

### Post by ritalin_kid on 2006-10-27
So if it's the kernel's fault then maybe it might be patched in a newer kernel ?

But how come this unclean shutdown only occurs on shutdown and not standby ?

EDIT: aiu, perhaps while the dev team was patching other bugs, maybe this one could have cropped up. I don't think they don't care about the issue..

---

### Post by julioromano on 2006-10-27
Filed a bug here:
[https://launchpad.net/distros/ubuntu/+bug/68660](https://launchpad.net/distros/ubuntu/+bug/68660)

---

