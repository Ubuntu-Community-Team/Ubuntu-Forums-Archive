---
title: "Issues with new X"
date: 2008-10-19
forum: Hardware
---

### Post by sukes on 2008-10-19
Hey everyone, so I'm running an IBM T42p laptop and I just upgraded to 8.10. I really like the feature on the laptop that lets you use the eraser head mouse as basically a scroll wheel by pressing a button on the mouse pad. Since I've upgraded though, I'm having issues getting the middle mouse button to enable the scroll function. It used to be configurable in the xorg.conf file by adding two lines to the "Input Devices" section, but now that X has been changed I have no idea how to get that functionallity back and it's getting frustrating. Anyone have any ideas?

---

### Post by rlonnborg on 2008-11-11
I am also dealing with the same problem.  Also unable to get it to play DVD movies.

---

### Post by jocko on 2008-11-12
> **sukes said:**
> It used to be configurable in the xorg.conf file by adding two lines to the "Input Devices" section, but now that X has been changed I have no idea how to get that functionallity back and it's getting frustrating. Anyone have any ideas?

You can still use xorg.conf to configure xorg. The file is still there and it will be used if you add some options to it.

---

### Post by wgrant on 2008-11-12
xorg.conf is no longer the right way to configure input devices. See [the new documentation](https://wiki.ubuntu.com/X/Config/Input).

---

### Post by zaobz on 2008-11-12
It's on [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint) at the very bottom.

---

