---
title: "Switching from CRT to LCD moniter"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by Nex6 on 2005-03-30
Hello all,


i have a machine, with a Nec 17 inch CRT moniter. and i switch it to a 17inch LCD i get no video ? any ideas?



-Nex6

---

### Post by DJ_Max on 2005-03-30
Well, you have to reconfigure xfree86. I use xorg, so I forgot the command.  #-o

---

### Post by Nex6 on 2005-03-31
ahhh,

i remember now...


dpkg --reconfigure something


hmmm, i i just have to get the correct syntax.


-Nex6

---

### Post by Darrena on 2005-03-31
[QUOTE=Nex6]ahhh,

i remember now...


dpkg --reconfigure something


hmmm, i i just have to get the correct syntax.


-Nex6[/QUOTE]


sudo dpkg-reconfigure xserver-xorg

---

### Post by Nex6 on 2005-03-31
thanks,

other then connecting the LCD, and ssh'ing in to the box is there an easyer way to do it?

becuase when i connect the LCD i get no video. 



-Nex6

---

