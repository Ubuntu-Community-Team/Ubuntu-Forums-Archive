---
title: "Sony Vaio F12 and Alps Touchpad"
date: 2010-08-29
forum: Hardware
---

### Post by speedygeo on 2010-08-29
I have some problem with my touch-pad on the Sony Vaio F12Z.
The touch-pad is not recognized at all.
Can anyone help me? I need help!

---

### Post by bjmg on 2010-08-29
Hey,

I have the same notebook.
Try the following in your grub startup:
edit the linux kernel line while in grub menu
and change "quite splash" into "quite splash i8042.nopnp".
You can also add that option to /etc/default/grub.

I also had some other problems on mine...
But unfortunately I don't have time to write about them at the moment.


HTH

Bernhard

---

### Post by speedygeo on 2010-08-31
> **bjmg said:**
> I have the same notebook.
I also had some other problems on mine...
But unfortunately I don't have time to write about them at the moment.
HTH
Bernhard

I think we can collaborate to write a wiki page for our Sony Vaio F12. I'm waiting for you. I'm on vacation until the 15.


> **bjmg said:**
> Try the following in your grub startup:
edit the linux kernel line while in grub menu
and change "quite splash" into "quite splash i8042.nopnp".
You can also add that option to /etc/default/grub.


Thank you Bernhard. It works finally!!! :D

---

### Post by bjmg on 2010-08-31
Hey,

you may look into this project: [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)
This project tries to find solutions for common problems when running linux on Sony Vaio F11 and I think they also list bugs that are present on Sony Vaio F12.

So I think it is actually not needed to write a wiki entry for that.

By the way: I've just upgraded to 10.10 and at least the sound issues are solved there.

Bernhard

---

### Post by speedygeo on 2010-09-10
I think it is an hardware problem. I should call to Sony. For now I buyed a mouse.

---

