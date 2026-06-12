---
title: "[SOLVED] Can't get my new usb pci card to work."
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Xanghi on 2007-11-13
OK so i just got a new pci card from my dads shop and i put it in my computer and well i dont know if i need anything for it to work or not 

i went to the hardwhere maneger to see if it was even reading it and i found when i remove it the list  is missing 5 things witch is good but when it is in i put a jumpdrive in it or a camera and it flashes and nothing works.

iv got all the info off the card i could  

on the chip it has 

  Ali
  m5271  a1
  0409 ts05
  ek472421000c

on a stiker it has 
  FS-MEG-ALI

and inscribed on the back 
  0408
  cte 002 94V-0
help plz?

---

### Post by chaffeur on 2007-11-13
what does dmesg say? Type "dmesg | tail" in a terminal just after you've plugged in the pc card.
Also try typing lspci and see what information that gets.

---

### Post by Xanghi on 2007-11-13
well i finaly got home and heres what i got

---

### Post by chaffeur on 2007-11-14
Hi!
Both files in the archive are identical, they are both dmesg (syslog). But as far as I understand that one the problem, "usb 4-3: device not accepting address 16, error -71", appears when you insert a device in the pccard. Please remove the pc card, then reinsert it and call dmesg.
I gave google a quick search after that error message, have a look at this page;
[http://www.spencerkellis.net/archives.php?post=usb-under-fc5-device]("http://www.spencerkellis.net/archives.php?post=usb-under-fc5-device")

bye!

---

### Post by Xanghi on 2007-11-15
umm well its still giving me the read errors and i even moved bridges to c what it would do but the card acts like it don't got a connection but the hardware manager cs it

im posting a pic of what it shows in the device manager

---

### Post by Xanghi on 2007-11-17
op no now it works for some random reasone well thanks for ur help

---

