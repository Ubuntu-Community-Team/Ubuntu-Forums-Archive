---
title: "Can I get to a terminal via a serial connection?"
date: 2020-07-04
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2020-07-04
My motherboard has a [serial header](https://imgur.com/lmLy9Ot.png)
Is there a way I can use a raspberry pi to access the command line via this port
I know there are easier ways to do this but i have had issues with crashes with no log data so maybe if it happens again i can see something over serial

---

### Post by Holger_Gehrke on 2020-07-04
There's a [post]("http://0pointer.de/blog/projects/serial-console.html") on setting up a serial console by the author of systemd. I think you'll need a converter between the pi's serial port (3.3V) and the PC (5V, I believe).

Holger

---

