---
title: "login hangs with error &quot;fglrx: no matching device section for instance&quot;"
date: 2009-03-20
forum: Hardware
---

### Post by Ubuntiac on 2009-03-20
Hey everyone,

My system was working fine until I did some updates last night and now when I log into KDE, it shows the first couple of icons up to the "blue marble", but then it just hangs before showing the desktop icon. I can still access the command line with ctrl+f1 and scanning the logs I see repeated entries in kdm.log stating:

**"(WW) fglrx: No matching device section for instance (BusID PCI:0@0:20:0) found"**

I might have thought that this problem was *only* fglrx if it wasn't for two things:
1. It was working fine up to last night
2. Now even the default xorg.conf and using ATI driver completely hang my system when x tries to start (with a white screen that even alt+shift+SysRq+RSEINUB can't break)

I've tried reverting xorg.conf to it's original state and to the fglrx version but altered to say ati instead to no avail.

I'm running Kubuntu Jaunty AMD64 with the new fglrx driver for Xserver 1.6.

Any ideas? Thanks!


Note: The lspci-vvnn.txt has a couple of less relevant bits removed to fit the forums size limits.

---

### Post by Ubuntiac on 2009-03-20
Seems to have been some kind of funky permissions issue on the home folder.

After seeing another error message I tried 

```
sudo chown username:usersname -R /home/username
```

 and that seemed to fix it. Not sure exactly what happened to get the permissions out of whack though...

---

### Post by Ubuntiac on 2009-03-28
Dang! I can't believe this... I just did another upgrade and...

Iiiiit's baaaaa-aaaack....

Login screen comes up fine, but after entering username and password it hangs on login. The chown command above doesn't seem to help in any way. All my packages are up to date. Same error message as in the title of this post.

Grrrrrrrr....

Any ideas anyone?

---

### Post by Ubuntiac on 2009-03-30
OK, it's really fixed now. See [this post]("http://ubuntuforums.org/showthread.php?t=1110871") if you're interested in the solution (it's easy!).

---

