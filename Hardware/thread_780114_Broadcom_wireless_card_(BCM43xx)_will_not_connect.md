---
title: "Broadcom wireless card (BCM43xx) will not connect"
date: 2008-05-03
forum: Hardware
---

### Post by Eirikizer on 2008-05-03
Hi, I have been using Ubuntu on my own laptop ever since Hardy Heron came out in April. I have shown it to several people I know, and all of them have been impressed by it, and yesterday my mother asked me to install it on her laptop (which is not very old).

Partitioning and installing went smoothly and I was able to install and set up within an hour and a half, and I installed a proprietary driver to make the wireless card work. The card is in the Broadcom BCM43xx series

Then I got a list of the networks available to us, and I tried to connect to our own. I did everything by book, input our password the way it worked on my laptop, but every time I tried to connect it didn't even reach the first green dot.

Then I tried installing the Windows drivers with ndiswrapper, I found the drivers here. None of them would work properly. How am I supposed to solve this?

I really need this, it might decide the future of Linux for my entire family for generations to come...

---

### Post by luisromangz on 2008-05-03
I have a broadcom wireless card and it works perfectly with the included b43 driver that replaces the older bcm43xx driver. Can you provide more details about your setup?

---

### Post by Eirikizer on 2008-05-03
I think the card is named BCM94311mcg, and I have installed the newest Vista driver from the site (because the XP version wouldn't work with ndcwrapper), and also some older versions. Do you want some details about the other hardware?

---

### Post by subzero316 on 2008-05-03
> it might decide the future of Linux for my entire family for generations to come
:lolflag::lolflag:
hope u get it workin

---

### Post by Eirikizer on 2008-05-03
What's strange is that the same network connection works completely fine on the two other computers in our house, and that without installing any proprietary drivers whatsoever.

---

### Post by luisromangz on 2008-05-03
I'm not sure about using Vista drivers with ndiswrapper, and I would give the b43 drivers another try. Did you install the firmware for those in the restricted drivers manager?

---

### Post by Eirikizer on 2008-05-03
Yeah, I tried the drivers designed for Linux. Perhaps the only solution is to wait for the next release in six months or some kind of update. Or is there anyone here with a better idea?

---

