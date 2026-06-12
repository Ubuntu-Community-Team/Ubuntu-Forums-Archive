---
title: "No new login screen after Karmic upgrade"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Kralizec on 2009-11-04
Hi guys. I have no problems with my Karmic upgrade except that after upgrading I don't have the fancy new login window that everyone else is raving about. I have the face browser, but the background is solid brown with an ugly grey interface and there is no progress splash screen after logging in. Does anyone have any suggestions?

---

### Post by Donalb on 2009-11-05
Same problem here. (And others that I've seen also).

One way of addressing here;

[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)


But to honest I can't understand it. It's about changing back to GDM though rather than fixing our problem.

---

### Post by Kralizec on 2009-11-05
I followed the instructions in that post, and it turns out there weren't actually any options for GDM configuration in the gnome control center.

---

### Post by Linfreak on 2009-11-07
I was facing the same problem ever since I upgraded to Karmic from Jaunty. Try installing xsplash.

```

apt-get install xsplash
```

Probably in a fresh install this package is installed, whereas its left out in an upgrade from an earlier release.

Cheers.. HTH..

---

### Post by Kralizec on 2009-11-07
Thanks! Installing xsplash did indeed get me the nice background and the login status screen. The interface still looks the same, but that could just be how it is supposed to be and I didn't get a good enough look at it before.

---

