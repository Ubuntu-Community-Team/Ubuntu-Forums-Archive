---
title: "How I got my Interlink Bluetooth Media Remote to work on my Dell Inspiron 1720"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by banjo man on 2007-10-20
My bluetooth adapter (built in on my 1720) worked out of the box in Gutsy.

After installing [BlueMan]("http://blueman.tuxfamily.org/"), I could see my remote when I put it into discovery mode (hold volume up and down).

Unfortunately, I couldn't connect to it because I needed a passkey.

I looked it up, and ended up using this to find my remote address (while it was in discovery mode)

```
sudo hcitool scan
```

After that, I manually connected to it:
(your's may be different)

```
sudo hidd --connect 00:15:D8:00:77:8B
```

This worked beautifully. All the functions worked perfectly.

(still working on the automatic battery life saver function on the remote)

This may need to be run at every boot (haven't rebooted yet).

I may post an update later after adding the command to the sessions program list thing...


This method should also work on bluetooth mice etc... that do not use a passkey when connecting.


Also, [_Here_]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A0691231") is a link to the Dell page for my remote...


**_[COLOR="Red"]EDIT:[/COLOR]_** Tried adding -t in the command  when connecting the remote. Sets device connection timeout value. check "man hidd" (still determining how this works. Doesn't fix the problem where the remote disconnects while charging, though.)


**_[COLOR="Red"]EDIT:[/COLOR]_** Completely Resolved: using

```
sudo hidd -i 00:15:D8:00:77:8B
```

automatically reconnects, works with most all media players (that I use) except VLC...

---

### Post by Chrisoldinho on 2008-01-13
bringing this thread back from the dead. 

my bluetooth mouse works perfectly using the above. but when i reboot it doesn't. how do i add this command to ubuntu on the startup so that it will always attempt to connect the mouse?

---

### Post by Chrisoldinho on 2008-01-14
bump

---

### Post by banjo man on 2008-02-27
I don't have  a bluetooth mouse, so I can't test this, but here is a [link...]("http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=8")

sorry for taking so long, I'm in college and pretty busy lately

---

