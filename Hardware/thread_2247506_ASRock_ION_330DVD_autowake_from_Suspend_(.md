---
title: "ASRock ION 330DVD autowake from Suspend :("
date: 2014-10-08
forum: Hardware
---

### Post by Azyx on 2014-10-08
Hi.
My ASRock ION 330 DVD with Ubuntu 14.04 can wake from suspend if I have USB device like keyboard connected, but no typing.

It can happend when I turn on a light or some thing in the room, so I think small EMP can cause the turning on.
Is there a way to only some signal to cause the wakeup from suspend?

/Cheers

---

### Post by Vladlenin5000 on 2014-10-08
Weird, but not impossible.
Have you already checked and ruled out other wake up calls like network or even the mouse?

---

### Post by Azyx on 2014-10-08
Yes. Physical disconnected ethernet and disconnected wifi.

---

### Post by Azyx on 2014-10-08
I get to BIOS and turned off CIR, I think it''s an onboard IR reciver, I don't have any Remote-control, any way..

---

### Post by varunendra on 2014-10-08
How about disabling all the "Advanced Power Management" features in the BIOS, if it provides that kind of control?

Is the power adapter one without a [ferrite bead]("https://en.wikipedia.org/wiki/Ferrite_bead")?
Does it also happen if the laptop is not connected to the AC power source at all (running on Battery)?

Cheap circuitry can do many miracles like this.

---

### Post by Azyx on 2014-10-08
Is  a 'Nettop' not a laptop, so there are no battery.

I will wait and see if it starts after i disable CIR 'remote control'. Have not started yet :)

---

### Post by Azyx on 2014-10-08
Is  a 'Nettop' not a laptop, so there are no battery, and the power-cord have a ferrit-thing, just near the connector to the machine.

I will wait and see if it starts after i disable CIR 'remote control'. Have not started yet :)

---

### Post by Azyx on 2014-10-08
By the way, if I during Suspend' disconnect AND connect the keyboard, It start up.

---

