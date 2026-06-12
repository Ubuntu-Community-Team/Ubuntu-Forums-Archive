---
title: "how do i install rutorrent on ubuntu server 9.04?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by steve51184 on 2009-08-11
hi all how do i install rutorrent on ubuntu server 9.04 as i've tried to find a good guide but there seems to be none out there

---

### Post by wojox on 2009-08-11
```
sudo apt-get rtorrent libtorrent7
```

---

### Post by steve51184 on 2009-08-11
> **wojox said:**
> ```
sudo apt-get rtorrent libtorrent7
```

but i need rutorrent not rtorrent?

rutorrent is a web gui for rtorrent but what i need to know is how do i setup rutorrent?

---

### Post by stlsaint on 2009-08-11
have you tried the torrent client transmission?

---

### Post by steve51184 on 2009-08-11
> **stlsaint said:**
> have you tried the torrent client transmission?

not what i need as i want a php based torrent client and before someone suggests it i have torrentflux ;)

---

### Post by steve51184 on 2009-08-13
anyone? :)

---

### Post by T0aster on 2009-08-25
It's pretty easy.  Follow instrutions for rtgui but instead of putting rtgui into your /var/www/ folder replace it with the rtorrent folder from the rutorrent page.  

You'll need the XML-rpc packages installed and some lines need to be added to your .rtorrent.rc file.  I think the rtgui guide will cover most of it. [http://code.google.com/p/rtgui/wiki/ubuntu_rtgui](http://code.google.com/p/rtgui/wiki/ubuntu_rtgui)

Hope this helps!

---

