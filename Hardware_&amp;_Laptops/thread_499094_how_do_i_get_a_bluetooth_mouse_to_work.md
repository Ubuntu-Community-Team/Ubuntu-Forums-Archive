---
title: "how do i get a bluetooth mouse to work?"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by spud42 on 2007-07-12
i have a dell d620 dual booting xp/fiesty . i also have a bluetoth mouse. it works fine with xp but i would lik to get it to work in ubuntu as well. i have dabbled in linux over the last 10 years or so but im no expert. how would i go about getting it to work?

---

### Post by chichibabin on 2007-07-12
The bluetooth adapter should have been picked picked up on installation and configured correctly. To get a bluetooth mouse to work (I have Logitech MX900) push the connect button on the bottom of the mouse then from a terminal run:

hidd --search

the mouse and its address should be detected so then run:

hidd --connect xx:xx:xx:xx:xx (the bluetooth address)

The mouse should now be working. From now on the mouse will connect automatically as long as the hidd server is running. To start this run:

hidd --server

This can be added to a script and executed on start up.
Hope this works/helps.
Sat

---

