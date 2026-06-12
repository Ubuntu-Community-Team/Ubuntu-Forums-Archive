---
title: "SONY Laptop Cant install ubuntu!"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by i-tech on 2005-09-11
Hi all!
I've tried to install ubuntu it boots but while cdrom detection it stucks in 98% , saying "Starting PCI Card" or something like that. Can any1 help? 
thanx

---

### Post by ubuntunewbieit on 2005-09-12
what's the laptop model? and ubuntu breezy or hoary?

---

### Post by sebdel on 2005-09-13
I have the excact same problem with hoary on a vaio FS285H. I've tried noacpi nolacpi but it doesn't fix it. Oh and the livecd does it too.
someone can help ?

---

### Post by i-tech on 2005-09-14
my model is FS215S i tried to boot with > hw-detect/start_pcmcia=false and it worked!! i installed wtihout any problem but have minor problems like no sound..
try to fix em now.

---

### Post by InvIsiBlekID on 2005-09-14
i couldn't get it installed on my sony vaio when i tried hoary, but i downloaded the breezy pre-release and it works, so maybe its worth trying that

---

### Post by sebdel on 2005-09-16
hw-detect/start_pcmcia=false

did the trick on a FS285H.
thank you so much.

From what I can see:
- there is no sound
- the 3d is not accelerated
- wifi might work. I have nothing to try but it shows 2 ethernet interfaces.

next step: try the nvidia driver.

---

