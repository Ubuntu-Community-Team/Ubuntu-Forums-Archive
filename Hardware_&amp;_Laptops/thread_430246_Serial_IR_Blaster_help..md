---
title: "Serial IR Blaster help."
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by lonegeek on 2007-05-01
I just bought a blaster from [http://www.irblaster.info/]("http://www.irblaster.info/").

And I'm having trouble getting it to work with lirc 0.8.1.

I have lircd.conf set for my dish receiever.

I've run 

> sudo dpkg-reconfigure lirc-modules-source

and I select serial as the module, then other, then no, and no.

And I did

> sudo nano /etc/lirc/hardware.conf

adding the module lirc_serial

And built the modules

I've also added  

> alias char-major-61 lirc_serial 
options lirc_serial irq=4 io=0x3f8
install lirc_serial /bin/setserial /dev/ttyS0 uart none ;\
    /sbin/modprobe --ignore-install lirc_serial

to /etc/modprobe.conf




When I try
 > irsend SEND_ONCE DISH_1 power

it says remote not found even though ive checked with lircd.conf and thats the remote name.

So If i do 

> sudo lircd -n

It says file locked with pid or something. I can't specifically recall.

[U]

What am I missing?

[/U]

---

### Post by lonegeek on 2007-05-02
Bump.

Anyone have experience getting one of these to work?

---

### Post by dannyboy79 on 2007-10-02
please help. I am in the same boat

---

### Post by teet on 2007-10-13
I bought the same IR blaster.  I got it to work.

> and I select serial as the module, then other, then no, and no.

I believe the second "no" that you chose needs to be a "yes"  You need to say yes to the question that asks you about "software" something or another.  I couldn't get mine to work at first either, then I tried that and it worked.  Go figure.

After you do that, be sure to do a 'sudo /etc/init.d/lirc restart' and a 'sudo killall mythbackend' followed by a "sudo mythbackend" before you test the blaster out in mythtv (assuming this is for myth).

-teet

Note:  This applies for Ubuntu 7.04 Feisty Fawn.  I'm currently trying to get it to work in Ubuntu 7.10 Gutsy Gibbon.

---

### Post by dannyboy79 on 2007-10-13
> **dannyboy79 said:**
> please help. I am in the same boat

well I got mine working finally. It turns out that the lircd config for the SA 2000 wasn't the correct one and the SA 3250HD STB has different codes. The SA 3250HD config is named something with an A at sourceforge.net lircd project under remotes. I also had to use ttyS0 (com1) instead of com2 which almost every other guide defaults to com2. I know this guide says com1 but just pointing that out. A good tip if you have problems after you get it working is to cover the sides, top and bottom of the irblaster emitter with aluminum foil so that it doesn't get any ambient lights causing channel channel changes.

---

