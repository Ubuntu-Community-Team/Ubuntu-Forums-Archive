---
title: "Lacie 500gb disappears!"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by Dalstal on 2007-12-24
Hello!
Just got a new Lacie 500gb external hard drive for chirstmas and I plugged it in about an hour ago and started the computer. It worked fine for about half an hour but then it suddenly disconected and I got a message saying it had been dismounted unproperly? Now I can't find it in my ubuntu system anymore? I heve tried restarting it and reconecting it to the USB but nothing happens, what should I do?

---

### Post by taurus on 2007-12-24
Open a terminal and post the output of this command here.  Make sure it is plugged and power on before you run the command though.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by StefanoCole on 2008-01-02
Hello Dalstal, I had a similar problem with a LaCie external hard drive 500 GB. I gave it back to LaCie store. They returned it to me with a different power supply (more powerful they said). Now it seems to work better.

Stefano

---

