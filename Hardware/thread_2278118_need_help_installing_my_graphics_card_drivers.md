---
title: "need help installing my graphics card drivers"
date: 2015-05-14
forum: Hardware
---

### Post by kaitlin3 on 2015-05-14
ok so my laptop has a discreete mobilirt HD 3650 i downloaded the legacy drivers from the amd site but when ever i try to exicute the installer i get a message saying this installer needs to be run b y the super user how do i fix this?

---

### Post by ajgreeny on 2015-05-14
Which version of Ubuntu are you using, as there is no working proprietary AMD driver for that card if you have Ubuntu 14.04 or later; they will not work any more with the newer versions of xorg in those later Ubuntu versions, even if you have the legacy fglrx version.

The open source radeon driver should work fine with that card as far as I am aware.

---

### Post by kaitlin3 on 2015-05-14
how do i find my version i think im using the latest Lbuntu 15.04

---

### Post by Pilot6 on 2015-05-14
There are no proprietary drivers for that card, that will work in modern Ubuntu versions. You can use open sourece driver. It is already installed.

---

### Post by kaitlin3 on 2015-05-14
ok thanks but will the open source driver have the same performance as the official amd driver

---

### Post by ajgreeny on 2015-05-14
If this is a version that you downloaded recently from the website it doesn't really matter, for this enquiry, which version you have, as the problem will be exactly the same for 14.04, 14.10 and 15.04, however for your information the command **lsb_release -a** in terminal will tell you what version you are running.

---

### Post by kaitlin3 on 2015-05-14
thanks for all the help

---

### Post by Pilot6 on 2015-05-14
> **kaitlin3 said:**
> ok thanks but will the open source driver have the same performance as the official amd driver
Since there is no any official AMD driver supporting that card for linux, what could be an answer to this question?

---

### Post by kaitlin3 on 2015-05-14
this is where i got the info from but all is well  [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64)

---

### Post by Pilot6 on 2015-05-14
This driver can be installed only on old versions of Ubuntu, AMD dropped support for this card a few years ago. But open source driver works OK.

---

### Post by kaitlin3 on 2015-05-14
ok thasnks for all the help plz lock this thread

---

### Post by dino99 on 2015-05-14
> **kaitlin3 said:**
> ok thasnks for all the help plz lock this thread

set it by clicking the "Tread Tools" on top right corner of your first post, and select SOLVED

---

