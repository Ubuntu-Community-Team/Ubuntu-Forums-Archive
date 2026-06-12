---
title: "xorg.congif option for trackpad scroll size?"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-02-20
What is the xorg.config option to change the size of the vertical scroll area on my track pad?

I looked through this list and could not find what I was looking for.
[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

---

### Post by JaggedOne on 2008-02-22
Why does no one answer my questions anymore?

---

### Post by Ayuthia on 2008-02-22
Have you checked out:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)
If you look at the Real-Time Tweaking section, it mentions that if you try:
```
synclient RightEdge=5000
```
it might give you an easier vertical scroll.  This will only work for the current session.  If you want to make them permanent, you would need to update your xorg.conf to have:
```
   Option "RightEdge" "5000"
```
I have to admit that I did not try it out, but it seems to be close to what you are requesting.

---

### Post by jijacob on 2008-03-19
This solution worked for me.  I had been looking all over for a vertical scroll size adjustment.  On my Asus Z71v laptop I found

```
Option "RightEdge" "5850"
```

Worked the best for me.

---

