---
title: "IBM/Lenovo X60 does not recognize Labtec Notebook Presenter"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by madmaxx on 2007-11-29
Hi! 

{running gutsy 7.10}

I have a strange problem. My Labtec 2.4GHz Notebook Presenter works on all my desktops (and laptops I had previously) but is not recognized on my Lenovo X60 laptop. Usually, the command 'lsusb' shows all attached usb devices. So, for the Labtec presenter the line indicating the presenter looks like this:

```
Bus 002 Device 008: ID 046d:c101 Logitech, Inc.
```

But on the laptop no additional line is shown. Well, I would need the wireless presenter only for presentations on the laptop. ](*,)

Thank you very much for a hint what I could check to get it running!
madmaxx

PS. I ran 'xev' as well but as the device is not even recognized, there are also no key signals received from xev.

---

### Post by digisus on 2007-12-02
Hello again... Does nobody have an idea? :rolleyes:

---

### Post by Olivier V on 2008-01-01
Hi,

I asked about this Presenter on the french forum :
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1427159#p1427159]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1427159#p1427159")

An answer is :
"Is the usb port correctly alimented ?"

Did you try your usb port with other things ?

Olivier V

---

### Post by digisus on 2008-01-01
Salut Olivier,

merci pour ta réponse! :)

I checked in the dictionary; with "alimentation" they mean "power supply", yes?

Well, yes, the usb socket is working for other devices (sticks, camera, etc).

digisus
(ex-madmaxx)

---

### Post by Olivier V on 2008-01-02
> **digisus said:**
> Salut Olivier,

I checked in the dictionary; with "alimentation" they mean "power supply", yes?



Yes.

> 

Well, yes, the usb socket is working for other devices (sticks, camera, etc).



Very strange ... you shoul see it with lsusb, even if it is not recongnised with linux.

Olivier V

---

### Post by Olivier V on 2008-01-04
> **digisus said:**
> 
Well, yes, the usb socket is working for other devices (sticks, camera, etc).


On the french forum
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1434618#p1434618]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1434618#p1434618"),
someone said that the usb socket maybe not have enough power.

Olivier V

---

### Post by digisus on 2008-01-04
Merci Olivier V !

There is not much I can do in that case...

digisus

---

