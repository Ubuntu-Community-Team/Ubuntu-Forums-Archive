---
title: "hardware pci modem, set serial?"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by semetay on 2007-02-05
Hello all,

I am trying to make an internet connection through a pci hardware modem. It does not work automatically. It runs under winxp on irq 17, but when I do a lspci I see it on irq 5

When I try;

setserial /dev/ttyS2 port 0x8c00 irq 17 or irq 5 and then

setserial -g /dev/ttyS2 returns
no such device

any idea what goes wrong?

thanks,

cumali

ubuntu edgy 6.10 x86_64
asus m2n32
amd 4200+ x2

---

### Post by comfurtn on 2007-02-05
I've dealt with quite a few modems under linux.... back when i still operated under dial-up...  what kind of modem are you dealing with?  google something like "linux modems" and check to see if that modem is supported under linux.  some work better than others....

---

### Post by semetay on 2007-02-05
hello,

thank you, I have been trying to solve this issue for months now. of course I am new to linux so it took me sometime to understand the linux os. winmodems do not work with linux but this is a hardware modem so theoratically it should work. the thing is it is not attached to a com port (i guess) so i need to attach it by using setserial. I do it but it doesnt work.

---

### Post by comfurtn on 2007-02-05
I'm sorry.. I didn't catch that you have an external modem..   

I haven't dealt much with external modems.. this [howto]("http://www.linuxplanet.com/linuxplanet/tutorials/3206/1/") might offer you some insight..

maybe someone else will come along with some experience on the matter.

---

### Post by unisol on 2007-02-06
try running sudo wvdialconf /etc/wvdial.conf. if you have a hardware modem it should detect what port it is on.

---

