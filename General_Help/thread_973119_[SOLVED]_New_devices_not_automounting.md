---
title: "[SOLVED] New devices not automounting"
date: 2008-11-06
forum: General Help
---

### Post by Stunts on 2008-11-06
Hi all.

I've been running Ubuntu 8.04 for over 6 months on this PC and I've never experienced something like this before.
This started to happen only this week.

When I plug in a USB disk it doesn't automatically mount. I can mount it fine in Nautilus, and I can do it without any problems from the terminal too. However, when I do this, the mounted drive doesn't show up in the desktop.

The same is true about samba shares. I can mount them fine, but they never appear in my desktop. Other files appear fine in the Desktop.

Any ideas on what could be causing this?
This is kind of annoying. It's not a show stopper, but it's annoying.
Any help is greatly appreciated.

Thanks in advance.

---

### Post by Stunts on 2008-11-06
Just forgot to mention:
If you require anymore info, just let me know what to post!
Thanks.

---

### Post by drs305 on 2008-11-06
If you run the following, is the media_automount option enabled?
```
gconf-editor /apps/nautilus/preferences/media_automount
```

---

### Post by Dave54 on 2008-11-06
I think there's an option for that. Check System > Administration > Removable drives and media.
I'm not on my Ubuntu machine right now so I can't check.

---

### Post by Stunts on 2008-11-06
@Dave54:
I've checked there before, and there are no options for usb disks or whatsoever. Just for selecting software when a digital camera, or a PDA get mounted on your system. But thanks anyway.
@drs305:
That does sound promissing - I'll try it as son as I get to my main computer - which should be soon. I'll report back afterwards.

---

### Post by Stunts on 2008-11-06
OK, we're getting somewhere now.
The gconf-editor boxes you mentioned were inn fact unchecked. Why this happened is beyond me, but I've checked them.
USB disks now automatically mount.
But they still don't show up on my desktop. I'll try to check more settings and report back.
Thank you very much!

---

### Post by Stunts on 2008-11-06
OK, I'll mark this thing solved.
Further up the config settings, in the desktop folder I checked the "show volumes" box, and voilá!
Got it all up and running.

This gconf editor reminds me of... I get the creeps from saying it... the windows registry.

It is however, much simpler to use.

Thank you both for your replies!

---

### Post by drs305 on 2008-11-06
> **Stunts said:**
> OK, we're getting somewhere now.
The gconf-editor boxes you mentioned were inn fact unchecked. Why this happened is beyond me, but I've checked them.
USB disks now automatically mount.
But they still don't show up on my desktop. I'll try to check more settings and report back.
Thank you very much!

Well, if the above wasn't ticked, you can see files on your desktop but none of your devices, check this setting. It should be ticked to see volumes/devices mounted on the Desktop or in /media.
```

gconf-editor /apps/nautilus/desktop/volumes_visible

```

---

### Post by Stunts on 2008-11-06
I beat you there by 10 minutes. 

But thanks anyway. =-)

---

