---
title: "Need a cheap sound card that works on Ubuntu 10.10"
date: 2011-01-16
forum: Hardware
---

### Post by jojoguy10 on 2011-01-16
Hello,

I'm using Ubuntu 10.10 with kernel version 2.6.35.

I have on-board sound, but Ubuntu doesn't like any of the drivers I use for it (ALL Windows drivers).  As far as I can see, I need a new physical sound card.

Does anyone know a good, cheap sound card?  I need a PCI card with a mic input and I'd like to have at least 5.1, but it isn't required.  I really want to go cheap, but no so much that it doesn't work.  I'm shooting for around $30, but if it isn't possible, then just give me any great cards!

I have seen the Alsa Matrix, and I've been researching, but everything seems to expensive for me.

Thanks for helping!

jojoguy10

---

### Post by cascade9 on 2011-01-16
What onboard sound chip have you got? Most of them work fine. 

Its a pity that the CMI8788 based soundcards dont work 'out of the box' with ubuntu 10.10. The price is right, and they are decent.

---

### Post by jojoguy10 on 2011-01-16
> **cascade9 said:**
> What onboard sound chip have you got? Most of them work fine. 

I have the VIA 8237 with CMI9739 Sound Card.

I have looked around all over, and my conclusion is that there is no Linux driver(s) for this "sound card".

---

### Post by cascade9 on 2011-01-17
Seems to be a bug- 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1699188.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1699188.html)

---

