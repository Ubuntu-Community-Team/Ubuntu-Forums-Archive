---
title: "Wireless trouble on Ubuntu 9.04! Help!!"
date: 2009-06-19
forum: Hardware
---

### Post by Wily Walrus on 2009-06-19
Hi, I'm rather new too all this, and I'm not even sure I'm posting in the right spot, but I really need some help. I have a HP Compaq nc1620 that installed Ubuntu 9.04 on yesterday. I found a driver for my Wifi card which was manufactured by Intel. With this driver I'm supposed to be able to install it and somehow the wireless will work. I can't figure out how to install it, or if there is something else I'm supposed to do first. I've been trying to wrok on this for hours and hours, searching the web and Ubuntu forums and threads. Please help! Anybody.......:icon_frown:

---

### Post by gradinaruvasile on 2009-06-19
So u are saying your wifi doesnt work? Open a terminal (Applications->Accessories->Terminal) and type:
```
lspci
```
And post (copy/paste) the output of that command. This is for knowing what t ype of hardware your laptop has.
Also post the output of
```
dmesg
```
command. This is because sometimes this command has some useful information.

---

### Post by Wily Walrus on 2009-06-19
Sorry, I don't know how to copy from the terminal. I looked up the card earlier though and it said it was an "Intel Corporation PRO/Wireless 2200BG. I also downloaded the driver for it and extracted the file, but I can't figure out what to do from there; ie how to install it.

---

### Post by Wily Walrus on 2009-06-19
Thanks anyway for your help, I finally got it working anyway on my own, unfortunately though this thread probably won't be helpful for anyone else.
Thanks again.!!

---

### Post by mikeczap on 2009-06-26
Could you possibly share what you did?

I just installed 9.04 on an nc6120, and everything is working wonderfully except the wifi.  It seems to work partially (I can ping & resolve names), and for a short time after a restart I can browse the web, but eventually it just bogs down.  The ethernet port works great, however, and although I have an old Netgear WG511, I hate to resort to it when I have a reasonably new laptop with one built in.

So, never underestimate what can help people.

MikeC

---

