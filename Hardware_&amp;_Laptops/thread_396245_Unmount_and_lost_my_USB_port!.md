---
title: "Unmount and lost my USB port!"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by lawentzel on 2007-03-29
Ok, so I was stupid.  A friend of mine lent me his USB external hard drive.  After using it, I right clicked on the drive and chose "unmount" instead of "eject".  Oops.  Now, my USB port seems to be dead.  It isn't active any more.  I have shut down and restarted my laptop with the same result.  How do I get my port to work.  I have tried the following:

```
sudo mount -a
```

But that didn't seem to work.  Help!  Thanks.  Oh, I am using Fiesty.  I am aware of the fact that it is in Beta... but thought I would give it a try.  Again, thank you in advance for any help.

---

### Post by lawentzel on 2007-03-29
Ok, here is what I just figured out.  I hooked up a thumb drive to my USB port and it works.  But, when I right click on it, there is no Eject option.  Hooking up the old USB drive, still no longer is recognized.

---

### Post by azemute on 2007-03-29
umount -a unmounts everything in /etc/mtab [mounts table] and isn't a wise thing to use, generally :)

In your case, this likely included udev and procbususb. 

If you run "mount" with no parameters you can see what's currently mounted, if those aren't listed then you have indeed unmounted some fairly core systems including the pseudo-filesystem tied to USB devices and the udev [dynamic device manager] system...

A restart should clear that up, though you could re-mount them by hand... running "/etc/init.d/udev restart" may fix some of your problems, for the moment.

---

