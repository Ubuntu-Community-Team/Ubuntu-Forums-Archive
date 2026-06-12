---
title: "Inconsistent touch events on Lenovo Carbon X1 Touch"
date: 2013-03-31
forum: Hardware
---

### Post by nfmangano on 2013-03-31
I recently got a Lenovo Carbon X1 Touch and ubuntu has been working wonderfully on it, with the exception of some quirkiness of the touch events. It seems like my machine has also fallen victim to the following bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1015183](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1015183)

It seems that the system works fine so long as you don't touch the screen since startup, but after that, mouse-down and mouse-up events sometime get scrambled.

Edit: Just to add what I have above, this bug especially messes up any java-based application you may have, making programs like Eclipse mostly unusable. The only way to get them back is to kill the X session, which is pretty invasive since that logs the user out. A real pitty, I love ubuntu but the screen is one big shiny death trap if you touch it!

---

### Post by nfmangano on 2013-04-06
Happy ending. I updated to the latest kernel and this seems to have solved my touch event problem.

---

