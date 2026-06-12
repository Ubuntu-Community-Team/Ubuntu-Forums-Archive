---
title: "glxgears - abnormally low? Terrible wine performance"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by WasabiVengeance on 2008-02-29
Quick question for the community. I'm running gutsy on a 1.8gHz core 2 thinkpad with intel 945 graphics. I wasn't expecting stellar 3d performance, but it was MUCH worse than I expected in my games via wine. I ran glxgears and am getting just under 1000 fps. I realize it's not a benchmark, but it would seem to me to be a clear indicator if something was seriously wrong with my setup.

Is 1000 fps abnormally low?

I do have glx/dri loaded I believe.

---

### Post by taurus on 2008-02-29
What driver do you use in /etc/X11/xorg.conf for your graphic card?

```
cat /etc/X11/xorg.conf
```

---

### Post by WasabiVengeance on 2008-02-29
i810 I believe

---

### Post by taurus on 2008-02-29
Try the intel driver to see if it improves the performing.

---

