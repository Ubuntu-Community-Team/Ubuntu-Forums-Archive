---
title: "My Sony Vaio SB"
date: 2011-05-19
forum: Hardware
---

### Post by Pierre Zabell on 2011-05-19
Hello

So i purchased this new Sony Vaio Model: SB1V, 13" Screen laptop. And i intended to install Ubuntu 11.04 x64 on it. It succeeded in many ways, but i still have some problems:

1. It uses a integrated Intel graphic card, and a ATI 6470M graphic card. When i first install ubuntu, i can use the Unity GUI, but when i download the restricted drivers and install the driver for the ATI graphic card, i'm only allowed to use classic GUI. Also noticed that installing the driver for the ATI adapter, did reduce the noise from the computer drastically. I can't launch the Catalyst ATI config tool, it says i have a problem with my driver. Any ideas?

2. It have an integrated 3G modem, someting sony calls Everywair 3G. Ubuntu does not show this hardware in anyway, i wondered if i could get it to work under ubuntu.

I'm fairly new to Ubuntu so please help :)

Thanks in advance !

---

### Post by Pierre Zabell on 2011-05-20
bump

---

### Post by analyzer123 on 2011-05-20
I have the same problem with ATI driver on my new VAIO SC which is essentially the same as SB. Unity fails to come up and CCC cannot be loaded. Guess we'll just have to wait till AMD updates its graphics drivers for ubuntu.

> **Pierre Zabell said:**
> Hello

So i purchased this new Sony Vaio Model: SB1V, 13" Screen laptop. And i intended to install Ubuntu 11.04 x64 on it. It succeeded in many ways, but i still have some problems:

1. It uses a integrated Intel graphic card, and a ATI 6470M graphic card. When i first install ubuntu, i can use the Unity GUI, but when i download the restricted drivers and install the driver for the ATI graphic card, i'm only allowed to use classic GUI. Also noticed that installing the driver for the ATI adapter, did reduce the noise from the computer drastically. I can't launch the Catalyst ATI config tool, it says i have a problem with my driver. Any ideas?

2. It have an integrated 3G modem, someting sony calls Everywair 3G. Ubuntu does not show this hardware in anyway, i wondered if i could get it to work under ubuntu.

I'm fairly new to Ubuntu so please help :)

Thanks in advance !

---

### Post by Pierre Zabell on 2011-05-21
Is it just a matter of time?

---

### Post by Pierre Zabell on 2011-05-21
What about this driver, shoulden't it be new enough?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Dosen't work for me, can't understand why, almost got released.

---

### Post by Pierre Zabell on 2011-05-21
bump

---

### Post by Pierre Zabell on 2011-05-21
Any suggestions?

---

### Post by analyzer123 on 2011-06-01
You could try installing the driver directly from AMD but I doubt it'll work. Even in windows, the driver alongwith the ATI registry patch is required to operate both the intel hybrid graphics and ATI discrete graphics. 

I suppose someone will either have to ask Sony to build a custom driver for linux or hack it into the kernel. Either ways its not happening soon. In any case, I find linux on the laptops pointless now. Windows 7 is extremely stable and user friendly and has features (like intel widi or bluray) which linux will not have for a looong time. (or never!)

> **Pierre Zabell said:**
> Any suggestions?

---

### Post by svast on 2011-06-02
Have you considered using "bumblebee" ?

---

### Post by Pierre Zabell on 2011-06-03
Bumblebee? Isen't that only for Nvidia Optimus Technology? I am using an AMD Radeon 6470M Graphic card along side Intel integrated graphic card (sandy bridge).

---

