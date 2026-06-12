---
title: "Installation on a Laptop with a faulty HDD"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by joseraeiro on 2009-04-29
Hello,

I'm trying to install ubuntu 9.04 on a laptop with a broken internal HDD. I want to install it on a external USB HDD.

I'm able to boot with the live CD, choose to install, and then after step 3 on the installation it freezes. I guess this is because of the faulty internal HDD.

Is there any way to prevent the installer from trying to recognize the faulty HDD? Is there any other solution?

Thank you!

---

### Post by joseraeiro on 2009-04-29
I've tried using hdparm -Y on the faulty HDD and then installing. But it freezes the same.

Is there any way to disconnect the HDD without pulling the physical cable inside the laptop? I can't open the laptop as it would void the warranty.

Thanks.

---

### Post by jojo1224 on 2009-04-29
What model is the laptop? With most laptops you can disable the sata/ide bus which then the drive won't be recognised.

---

### Post by joseraeiro on 2009-04-29
It's a Vaio laptop. The BIOS has no option to manage the HDD.

I've managed to start the installation using the alternate CD, but it freeze when during the installation GRUB tries to detect other operating system. He's probably trying to recognize the OS on the faulty HDD.

Why doesn't it give up?

---

### Post by joseraeiro on 2009-04-29
I've waited more than 30 minutes on the GRUB install.

It eventually gave up. I'm now running ubuntu on the external HDD.

Thanks!

---

### Post by Monotoko on 2009-04-29
If youv got warranty cant you just ring the repair people and get them to fix the broken int HDD? :confused:

---

### Post by timcredible on 2009-04-29
is there any chance you could just remove the broken hard drive from the laptop and then do the install?  or maybe could use another machine to install the system to the external drive, then connect that external drive on the broken laptop.

---

