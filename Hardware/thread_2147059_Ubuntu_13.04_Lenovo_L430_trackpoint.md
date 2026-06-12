---
title: "Ubuntu 13.04 Lenovo L430 trackpoint"
date: 2013-05-20
forum: Hardware
---

### Post by iceonthehudson on 2013-05-20
I just got a Lenovo ThinkPad L430 and put ubuntu 13.04 desktop on it.  I kind of expected this, but the trackpoint and the buttons above the touchpad aren't working.  They're a nice feature of ThinkPads, and I'd like to be able to use them.  Any tips to get them working in Ubuntu?

---

### Post by linrunner on 2013-05-20
Hi,

this is a "peculiarity" that affects only the L430/L530 (with Elantech hardware). 

Install the package **tp-trackpoint-elantech** from my [PPA]("https://launchpad.net/~linrunner/+archive/thinkpad-extras").

---

### Post by iceonthehudson on 2013-05-21
Worked like a charm.  Thanks!

---

### Post by Demiurgous on 2013-05-21
> **linrunner said:**
> Hi,

this is a "peculiarity" that affects only the L430/L530 (with Elantech hardware). 

Install the package **tp-trackpoint-elantech** from my [PPA]("https://launchpad.net/%7Elinrunner/+archive/thinkpad-extras").
I tried the package, and while it worked beautifully for the trackpoint buttons (and I really, really liked it!!) I lost the two finger scroll.  The option was also completely gone from the Mouse and Touchpoint menu.

Did I do something wrong?  I would love to have both!

---

### Post by Demiurgous on 2013-05-24
Friendly bump for ideas, also on L430.

---

### Post by linrunner on 2013-06-07
> **Demiurgous said:**
> I would love to have both!
Unfortunately, this is not possible.

---

