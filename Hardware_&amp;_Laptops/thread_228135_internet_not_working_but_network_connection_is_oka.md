---
title: "internet not working but network connection is okay"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by bessimile on 2006-08-02
My internet recently stopped working on both linux and windows on my laptop. The weird thing is that the network connection icon, that I added to the tool bar, says that both the ethernet and wireless are working. I was looking at other forums trying out different things and only one got an error, I don't know if it is relevent or useful. 

cat /etc/network/interfaces -gets- parse error. Last token seen: / Garbled time

any ideas?

---

### Post by wieman01 on 2006-08-02
Can you ping your router or other computers in the network?

If yes, than perhaps editing the "/etc/resolv.conf" helps... just add your DNS and you should be able to happily browse the internet. But not sure if this is your problem.

---

