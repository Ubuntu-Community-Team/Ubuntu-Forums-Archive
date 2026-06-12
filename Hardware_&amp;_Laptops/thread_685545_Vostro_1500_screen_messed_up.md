---
title: "Vostro 1500 screen messed up"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by twiddler on 2008-02-02
I installed ubuntu 7.10 on my new Dell Vostro 1500 with a geforce 8600m video card. When I use envy to install nvidia's driver my screen gets messed up like a bad sync. Anyone have this problem on the vostro 1500? I think it has to do with my screen, it doesnt like the veritcal or horizontal sync settings. Is there a way to fix this? what should my sync settings be?

Thanks

---

### Post by RFGunslinger on 2008-02-02
My Vostro 1400 (w/ nVidia GeForce 8400M) works great using the restricted driver manager.

---

### Post by Yellow Pasque on 2008-02-02
Dell doesn't say what the sync settings should be (sigh..)
[http://support.dell.com/support/edocs/systems/vos1500/en/om_en/html/specs.htm#wp1102222](http://support.dell.com/support/edocs/systems/vos1500/en/om_en/html/specs.htm#wp1102222)

What does this command give you?:
```
xrandr -q
```

---

### Post by twiddler on 2008-02-02
I ran "xrandr -q" and get "can't open display".  I've heard people had issues with the vostro 1500 but usually are able to resolve it. For some reason ubuntu doesn't like mine. It works fine in windows though.

---

### Post by twiddler on 2008-02-05
I tried changing settings in my xorg.conf but it still produces a wacky screen at boot. This has frustrated me for two weeks now, I've just about given up hope with ubuntu on my laptop. Unless someone can help me out, I might try another distro like Mandirva.

---

### Post by twiddler on 2008-02-09
--bump--

---

