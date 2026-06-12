---
title: "changed resolution - lost display"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by qwavel on 2009-01-23
I installed Ubuntu 8.10 on a new computer.  No problems.

I decided to try a different screen resolution, so I used the 'screen resolution' option in system/preferences on the Ubuntu desktop and changed the resolution.

Now my screen reports "resolution not supported".

So how do I get back?

Eventually I rebooted the machine, and it had the same problem when it restarted.

I seem to remember that there is a key-stroke that will drop me into a non-x terminal?

And then how would I change the resolution back from the command line?

Thanks.

---

### Post by iaculallad on 2009-01-23
Try to boot from recovery mode and issue the commands below:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
dpkg-reconfigure xserver-xorg
```

then

```
shutdown -r now
```

---

### Post by qwavel on 2009-01-23
I follow the steps you recommended.  Everything seemed to work fine:  I was led through an X configuration wizard, and then I rebooted.

However, the problem has not changed.

Looking at xorg.conf, there isn't much in it.  Which configuration file has the screen resolution?

---

### Post by iaculallad on 2009-01-23
Try posting the content of your /etc/X11/xorg.conf file, maybe it could help resolve your issue.

---

### Post by qwavel on 2009-01-23
I just figured it out.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I guess they moved these settings from the xorg.conf file to this new monitors.xml file at some point.

Thanks for trying to help.

---

