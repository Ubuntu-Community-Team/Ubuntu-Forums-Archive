---
title: "Installing new graphics card"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by rubiks14 on 2007-05-07
I just got a new graphics card today and I'm have trouble installing it.  It is a Radeon rv250 (9000).  I have gone through the tutorials on installing the driver and have searched the site but I can't seem to find anything to help me.  I think the problem has something to do with my older graphics card still being used.  How can I deactivate my old graphics card and activate my new one so that it is the one that my computer uses?

---

### Post by taurus on 2007-05-07
Did you remove your old card before you installed your new ATI card?  

Then, boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
When done, reboot and see if X is up.

```
shutdown -r now
```

---

### Post by rubiks14 on 2007-05-07
OK, it recognizes the graphics card now.  Thanks.  I didn't do that before because I have had problems doing that in the past.  Now I have to get fglrx working.

---

