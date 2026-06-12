---
title: "Backlit keyboard not working on Toshiba M640"
date: 2010-08-14
forum: Hardware
---

### Post by Marcelo Ruiz on 2010-08-14
Hi,

I have a Toshiba M640 Laptop that comes with a backlight keyboard (and hybrid graphic card intel/nvidia).
I can't find a way to make it work under Ubuntu Lucid (even when I set the backlight keyboard to be on all the time in the BIOS, as soon as Ubuntu starts loading the backlight turns off and I can't turn it on again).
The keyboard has a shorcut for turning it on (Fn + Z) but that is also not working (xev shows no activity when pressing it).
On another Toshiba I have, as soon as you touch a key in the keyboard, the light goes on... but nothing happens on this one.
Is there any way to turn it on/off from the command line? Do I need to install a package to make it work? I've been reading topics regarding this but they mostly apply to Macs and other brands.
Thanks!

---

### Post by whitethunder922 on 2010-09-10
Any ideas on this?

---

### Post by piotao on 2010-10-21
> **Marcelo Ruiz said:**
> 
On another Toshiba I have, as soon as you touch a key in the keyboard, the light goes on... but nothing happens on this one.

Hey, I'm a new user of brand new Toshiba A665-3DV and under Ubuntu Maverick 10.10 there is also NO backlight for keyboard. It works in BIOS, in windows and everytime, but as soon as it is starting kernel, backlight goes away.
I googled for this a long time and I found somewhere that Toshiba changes radically their method of detecting function keys, like this FN+Z (which is also not working for me, even in xev, but some other works, but not all).
So, if this laptop you mention is the other one, but the one of the older series, it could be working.

Our shiny new laptops are not working and this is a problem for me. I think this is probably caused by the lack of kernel drivers for those specific devices, and maybe it will change in the future. Right now I did not found any working solution for this.

Toshutils and toshset packages did not work either, saying there is no kernel module nor device enabled. So the problem is device/driver related.

---

### Post by SEBASTIANFFX on 2012-04-27
I have a Toshiba M645 S4118X and in Ubuntu 12.04, as above when i press fn+z there is an indicator of backlit, but nothing happens :S, i hope the driver is woriking soon...

---

### Post by RubenMtz93 on 2012-07-26
Same issue here...Any updates? It's kind of making me regret having Ubuntu as my main OS, since the backlit keyboard was one of the reasons I bought it.

---

### Post by Marcelo Ruiz on 2012-07-28
I don't have the computer with me now, but did anyone try the 3.5 Kernel to see if that's solved?

---

### Post by nelsonhoover on 2012-09-10
I've got an A665D. Has anyone had any luck with the backlit keyboard thing yet?

---

### Post by xmilo on 2013-01-10
Same Problem with a Toshiba P850

---

### Post by howefield on 2013-01-10
Old thread closed.

Feel free to start a fresh.

---

