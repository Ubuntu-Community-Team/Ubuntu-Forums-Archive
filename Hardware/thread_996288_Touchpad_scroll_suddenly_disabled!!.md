---
title: "Touchpad scroll suddenly disabled!!"
date: 2008-11-28
forum: Hardware
---

### Post by kakyoism on 2008-11-28
Hi,

Regarding [this issue]("http://ubuntuforums.org/showthread.php?t=799167"), I used the syndaemon package to disable the touchpad. 

However, my laptop has a hardware button that can toggle-disable the touchpad as well. If I disable touchpad and enable it again with the button, the touchpad scroll is suddenly gone yet all the other function is still working. 

Then only if I restart gnome, the touchpad will go back to normal.
I placed a call of syndamon in the gnome session startup options.

```
syndaemon -i 3 -d -t -k
```

Does the problem have anything to do with this?

Thanks!

---

### Post by kakyoism on 2008-11-29
bump

---

### Post by kakyoism on 2008-11-29
bump

---

### Post by kakyoism on 2008-12-01
bump

---

### Post by kakyoism on 2008-12-02
Update (still no hope)

I followed some guidance in ubuntu wiki concerning HP Pavilion dv6000 series.

I installed a lot of tools and scripts including
gsynaptics, xbindkeys... 

The only reliable way to disable the touchpad is still the tiny hardware button that came with the laptop.

Being the same synaptic touchpad, my previous VAIO laptop worked with the software solution. 

I don't understand why...did ubuntu install a wrong drive to this by default?

---

