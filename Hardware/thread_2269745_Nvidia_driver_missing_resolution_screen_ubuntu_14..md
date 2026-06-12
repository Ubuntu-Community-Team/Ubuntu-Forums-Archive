---
title: "Nvidia driver missing resolution screen ubuntu 14.04"
date: 2015-03-17
forum: Hardware
---

### Post by daniii10 on 2015-03-17
I'm kind of new on ubuntu. After several attempts to install nvidia driver i still don't have the full settings like resolution and prime.

[IMG]http://s16.postimg.org/f8qldm2ud/Screenshot_from_2015_03_16_22_11_39.jpg[/IMG]

i but i don't get settings like this guy, i found it on the internet

[IMG]http://s10.postimg.org/tnoazjtyh/Screenshot_from_2015_03_17_19_50_17.png[/IMG]

I'm running ubuntu 14.04 LTS on Dell Inspiron 5720 and Nvidia GeForce 630M.

If someone can help me to install nvidia driver the correct way thanks.

---

### Post by Vladlenin5000 on 2015-03-18
Dell Inspiron 5720 was old with hybrid graphics and also integrated only. Make sure yours in the former and [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

---

### Post by Yellow Pasque on 2015-03-18
> Dell Inspiron 5720 was old
Yeah, I think it has a hardware mux and will not work with prime. Bumblebee is probably the way to go on a system like that. (Or, if one expects to be on AC power most/all of the time, completely disable Intel card if BIOS allows it.)

> After several attempts to install nvidia driver i still don't have the full settings like resolution and prime.
You can't just install the Nvidia driver directly on a system like yours. Make sure you completely remove any attempts to install nvidia driver and then see: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by daniii10 on 2015-03-18
The problem when i connect extra monitor with HDMI it overscan and i can't fix it in system settings so i thought maybe in nvidia settings i could so that's why i tried to install nvidia driver.
i got prime although i don't know if it's good:

[IMG]http://s21.postimg.org/f2jglw1l3/Screenshot_from_2015_03_18_14_32_58.jpg[/IMG]

But it's not the point i just want a way to fix overscan when i connect to hdmi screen.
On nvidia display settings i can see only one screen.

[IMG]http://s21.postimg.org/3k6y68nwn/Screenshot_from_2015_03_18_14_38_39.jpg[/IMG]


> You can't just install the Nvidia driver directly on a system like  yours. Make sure you completely remove any attempts to install nvidia  driver and then see: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I just went to nvidia website and install the driver for linux like i do on windows.
So how can i remove nvidia driver completley? i don't want to make anymore mistakes.

And if there is any way to correct overscan when i connect to HDMI.

Thanks.

---

