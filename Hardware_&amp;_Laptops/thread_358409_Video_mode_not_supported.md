---
title: "Video mode not supported"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by _Matt_ on 2007-02-10
when i boot Linux from ubuntu, it charge the system but when he is starting it, my monitor say "Video Mode not supported"

what i have to do???

---

### Post by dcstar on 2007-02-10
> **_Matt_ said:**
> when i boot Linux from ubuntu, it charge the system but when he is starting it, my monitor say "Video Mode not supported"

what i have to do???

CTRL-ALT-F1, log in and then:
```
sudo dpkg-reconfigure xserver-xorg
```
You can accept all the defaults until you get to the video refresh rate section, then choose "Simple" and choose what is appropriate, then:
```
sudo /etc/init.d/gdm restart
```

---

### Post by _Matt_ on 2007-02-11
when i have to press CRTL+ALT+F1??
when the system give me the problem or in the bootloader???

---

### Post by valke on 2007-02-11
just keystroke it right now, as you are on your computer, while it's up and running. it switches to non gui, just don't feel like you killed it. trust me you didn't.

---

### Post by Maube-Not on 2007-10-29
> **dcstar said:**
> CTRL-ALT-F1, log in and then:
```
sudo dpkg-reconfigure xserver-xorg
```
You can accept all the defaults until you get to the video refresh rate section, then choose "Simple" and choose what is appropriate, then:
```
sudo /etc/init.d/gdm restart
```

I want to have your babies. :)

Seriously though, thanks dude, i had this problem to! Fixed now! :)

---

