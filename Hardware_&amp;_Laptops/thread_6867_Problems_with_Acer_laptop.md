---
title: "Problems with Acer laptop"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by paul.hendrick on 2004-12-02
Hi there,
i've been trying to install Ubuntu on my laptop, but i'm having 2 major problems. 
the first is the network card setup during the install. my card isnt detected using dhcp, and the card is a Broadcom NetXtreme, which is built into the laptop.

the second, and most troublesome problem is the bootup after installation. when the process for starting hotplug tries to start, i get this message 
```
 modprobe FATAL: Error installing hw_random (lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random)
input/output error

```
and the system hangs there.

can anyone help me out with these sticking points, please?

thanks for readin.

---

### Post by 2fargon on 2004-12-02
Check out [http://kitech.com.my/ubuntu/4.10/index.html#troubleshooting](http://kitech.com.my/ubuntu/4.10/index.html#troubleshooting) for help with the hw_random error.

I have a Acer 290 LMi (centrino), and I get the same error, but that does not stop my laptop from booting.

Have you tried getting things running off of the liveCD to check things out?

---

