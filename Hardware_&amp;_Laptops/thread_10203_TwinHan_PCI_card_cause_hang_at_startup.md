---
title: "TwinHan PCI card cause hang at startup"
date: 2005-01-05
forum: Hardware &amp; Laptops
---

### Post by XrM on 2005-01-05
Hi,

I have a PCI TwinHan DVB-S/CI (and I use it under windows).

After a good ubuntu installation, the first boot hangs at hotplug. Everything works if i unplug the DVB card.

Cause I don't really need these card under linux, i would try to disable it's detection in order to boot with ubuntu.
But i don't know wich module is causing this. I try putting bttv in /etc/hotplug/blacklist with no success.

Can someone help me to boot linux with this card plugged ?

Regards,
XrM

---

### Post by XrM on 2005-01-06
Ok, for those that have the same problem.

Blacklisting bttv is not enough, i have been able to boot with all theses modules blacklisted :

bttv
bt878
btaudio
bt8xx
snd_bt87x
dst

---

### Post by emrextreme on 2007-11-13
I have the very same problem. That's why i can't use any Linux distro. Is there a way to bypass this problem?

---

### Post by staverts on 2007-12-02
My card did work flawlessly for months on end...and now the card is hanging of the driver load....

---

### Post by spidertnt on 2008-01-02
Try this

[http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A](http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A)

check out the diiscussion thats what fixed my hanging

---

