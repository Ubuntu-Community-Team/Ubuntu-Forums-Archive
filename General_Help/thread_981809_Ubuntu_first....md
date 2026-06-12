---
title: "Ubuntu first..."
date: 2008-11-14
forum: General Help
---

### Post by philokokus on 2008-11-14
Hi all

I am running vista and Ubuntu on same desktop. When it starts I get a message to choose to run vista or ubuntu. The problem is that vista is in first place and ubuntu on second. I would like to change that and put ubuntu in fist place. 

Any help?

José

---

### Post by kdcoetzee on 2008-11-14
Hey.

You can change that in your menu.lst
Open up a Terminal.

```

sudo gedit /boot/grub/menu.lst

```

And somewhere in there you can specify it. But sadly I don't have an Ubuntu machine close to me. So can someone else please give that info. 

Or else you will need to wait for me to get Home.

---

### Post by Carl Hamlin on 2008-11-14
> **Juggernaut_KDC said:**
> Hey.

You can change that in your menu.lst
Open up a Terminal.

```

sudo gedit /boot/grub/menu.lst

```

And somewhere in there you can specify it. But sadly I don't have an Ubuntu machine close to me. So can someone else please give that info. 

Or else you will need to wait for me to get Home.

You can find the information pertaining to menu order right after the default options in menu.lst.

---

### Post by philokokus on 2008-11-14
> **Carl Hamlin said:**
> You can find the information pertaining to menu order right after the default options in menu.lst.

Tks Carl but I am new to Ubuntu. Can you please tell me where that is? 

Tks again
Jose

---

### Post by Zhukov on 2008-11-14
Easy:

sudo gedit /boot/grub/menu.lst

Now, there is a small thing in the end, about sections and all that stuff. It is divided in small sections, maybe you can post the content of the file here...

Nevertheless, just count the number of entries, and in the beginning of the file there is a line:

default 0

You must replace the 0 with the entry number you want to boot by default.

Best regards!

---

### Post by philokokus on 2008-11-14
> **Zhukov said:**
> Easy:

sudo gedit /boot/grub/menu.lst

Now, there is a small thing in the end, about sections and all that stuff. It is divided in small sections, maybe you can post the content of the file here...

Nevertheless, just count the number of entries, and in the beginning of the file there is a line:

default 0

You must replace the 0 with the entry number you want to boot by default.

Best regards!

Hi

I will try that, if something goes wrong I will come back.

tks to all
Jose

---

### Post by eldragon on 2008-11-14
you shouldnt edit menu.lst directly, or with the next kernel update everything will revert back.

use startup-manager which is in the repos to make the change.
```

$ sudo apt-get install startup-manager

```

and start it with
```

$ sudo startup-manager

```

you will find your default option there.

---

### Post by caljohnsmith on 2008-11-14
It sounds like you might have a Wubi install of Ubuntu, or Ubuntu installed inside Windows; if that is the case, unfortunately the previous suggestions will not work for you. Did you install Ubuntu to its own partition, or did you use the "install inside Windows" option? Do you have a C:\ubuntu folder in your Vista directory?

---

### Post by philokokus on 2008-11-14
> **caljohnsmith said:**
> It sounds like you might have a Wubi install of Ubuntu, or Ubuntu installed inside Windows; if that is the case, unfortunately the previous suggestions will not work for you. Did you install Ubuntu to its own partition, or did you use the "install inside Windows" option? Do you have a C:\ubuntu folder in your Vista directory?

Yes it is in Vista directory.

---

### Post by caljohnsmith on 2008-11-14
> **philokokus said:**
> Yes it is in Vista directory.
OK, then you do have Wubi install; that means the boot menu that you see on start up is actually Vista's boot menu and not Grub's boot menu. If you want to change the Vista boot menu, probably the best thing to use is [EasyBCD]("http://neosmart.net/dl.php?id=1") within Vista. Give that a shot and let me know how it goes. :)

---

### Post by philokokus on 2008-11-15
> **caljohnsmith said:**
> OK, then you do have Wubi install; that means the boot menu that you see on start up is actually Vista's boot menu and not Grub's boot menu. If you want to change the Vista boot menu, probably the best thing to use is [EasyBCD]("http://neosmart.net/dl.php?id=1") within Vista. Give that a shot and let me know how it goes. :)

Hi

tks for the help. Unfortunatly I had to format my pc and now I have the chance to install ubuntu from scretch! I have 4 partitions in my hard drive in one is vista already installed and now I want to install ubuntu in another one.

 When I started to install from the live CD, in the 4º step all the partition are there but when I try to install in one partition (25 Gb) it says that no swap partition is there. Do I have to partition another one just for the swap or is it ok to install without swap? If I have to make a swap partition is 5 Gb ok?

Tks again for all the support.
Jose

---

### Post by caljohnsmith on 2008-11-15
> **philokokus said:**
> 
 When I started to install from the live CD, in the 4º step all the partition are there but when I try to install in one partition (25 Gb) it says that no swap partition is there. Do I have to partition another one just for the swap or is it ok to install without swap? If I have to make a swap partition is 5 Gb ok?

Tks again for all the support.
Jose
It is possible to install Ubuntu without a swap partition and instead set up a swap file in your main Ubuntu partition afterwards, but I wouldn't recommend it if you can simply let Ubuntu have a swap partition. I think a 5 GB swap partition is larger than necessary. Swap generally doesn't need to be larger than 2X your RAM size, and I've heard that anything over ~4 GB really won't buy you much in performance; so even if you have more than 2 GB of RAM, I would stick with a 4 GB swap partition.

You might find the tutorial at Herman's website helpful for leading you step-by-step through the installation process:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)
[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Good luck and let me know how it goes.

---

### Post by philokokus on 2008-11-16
> **caljohnsmith said:**
> It is possible to install Ubuntu without a swap partition and instead set up a swap file in your main Ubuntu partition afterwards, but I wouldn't recommend it if you can simply let Ubuntu have a swap partition. I think a 5 GB swap partition is larger than necessary. Swap generally doesn't need to be larger than 2X your RAM size, and I've heard that anything over ~4 GB really won't buy you much in performance; so even if you have more than 2 GB of RAM, I would stick with a 4 GB swap partition.

You might find the tutorial at Herman's website helpful for leading you step-by-step through the installation process:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)
[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Good luck and let me know how it goes.


Hi

I installed it with a 4 GB swap partition. Now it boots up with Ubuntu first but regarding to that I have done nothing. Just reinstalled Ubuntu and now it is booting first then vista. 

The only problem I have now is that I don't have the sleep mode and hibernate and suspend freezes in a black screen and have to reset. 

Any help for that?
Tks
José

---

