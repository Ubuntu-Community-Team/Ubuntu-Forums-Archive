---
title: "Wireless card not working Toshiba Satellite"
date: 2011-12-22
forum: Hardware
---

### Post by pianogamer5 on 2011-12-22
I own a Toshiba Satellite L655D-S5066. I used to have windows, but then I switched to ubuntu and was loving it...... until last night. I noticed my wireless was off. So, I tried turning it on, but it wouldn't work. So, I did some internet searching and ended up running rfkill list in terminal to find out that my wireless card was hard blocked! There is no hardware switch on my laptop, however. So, I tried reinstalling the kernel and many different things, but none of them worked and I am still stick with a non-functional wireless card. There is a fn+F8 shortcut to turn the card on and off, however, that didn't hard unblock it after many attempts. I ran lspci in terminal and this is the wireless card entry: 

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

PLEASE HELP ME!:cry:

---

### Post by wolfen69 on 2011-12-22
Try booting to a previous kernel. During bootup, press Shift key and you will be taken to the GRUB screen.

---

### Post by pianogamer5 on 2011-12-22
The only problem is, i don't have any old kernels installed. I used to, but then i cleared them. STUPID MOVE... :(

---

### Post by pianogamer5 on 2011-12-22
Well, I installed linux kernel 3.0.0-12 instead of 3.0.0-14 (which was what I was using previously) to no avail........... I DON'T LIKE WIRED CONNECTIONS :cry:

---

### Post by pianogamer5 on 2011-12-23
I fixed it with some good old hardware tinkering. I just opened my computer up, cleaned the wireless card, and put it back together and it works!!!!! yay

---

