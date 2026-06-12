---
title: "Karmic Koala won't allow System Updates...Help!"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by DiAnah on 2009-11-12
Recently "upgraded" to Karmic Koala.

Update Manager tells me I have Important Security Updates -- when I click INSTALL UPDATES spinning wheel and box says "Reading Package Information," BUT nothing happens.  Updates have not been installed.

I thought Sudo Nautilus would help, BUT I've gotten this cryptic message:  

**/etc/sudoers/ is mode 0646, should be 0440**

Is anyone out there aware of a way to fix this?

***   ***   ***   ***   ***

For the record...Karmic Koala has noticeably slowed my system AND I now have **no** sound.  Argh!  I wish I hadn't upgraded...

---

### Post by wojox on 2009-11-12
Boot into recovery mode from the GRUB menu, drop to a root shell and then 

```
chmod 0440 /etc/sudoers
```

 and reboot.

---

