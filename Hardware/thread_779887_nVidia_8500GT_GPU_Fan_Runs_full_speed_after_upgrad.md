---
title: "nVidia 8500GT GPU Fan Runs full speed after upgrade to Hardy"
date: 2008-05-03
forum: Hardware
---

### Post by ubtpenguin on 2008-05-03
I have Geforce 8500GT graphics card equpped desktop. I didn't have any problem with this card on 7.10 Gutsy. But as soon as I upgrade to Hardy. Fan runs full speed and noise is unbearable. As soon as I disable nVidia driver fan becomes quiet. I searched nVidia site and they said they fixed the problem when they released version 169.09. Hardy has 169.12 how come the problem is not solved? 

I tried nvclock but it says my card is not supported by nvclock. 

Anyone knows solution? 
:popcorn:

---

### Post by db5007 on 2008-05-24
I too am having the same problem. Anyone know how to fix this one?

---

### Post by Marat Galiev on 2008-05-25
I have 8600GT,and without nvidia driver,my fan runs full speed.
After installing driver, it run silent.
Maybe you should reinstall you driver?

---

### Post by hotweiss on 2008-05-25
Try installing the Nvidia drivers using Envy:

A) First we’ll need to update Ubuntu’s repositories by typing the following in Terminal:
sudo apt-get update

B) Now we’ll need to install Envy by typing the following in Terminal:
> sudo apt-get install envyng-gtk

C) Next we’ll need to execute Envy by typing the following in Terminal:
> sudo envyng -g

D) Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 169.12, and finally click Apply.

E) Once the installation is completed, reboot and you will once again have a crisp screen.

If that doesn't work, I used this fix to get my fan working before:

Download the latest nvfan deb from here:
> [http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/](http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/)


Then follow these steps here:

[http://ubuntuforums.org/showthread.php?t=315430](http://ubuntuforums.org/showthread.php?t=315430)

Start at 
use automated fan control.

---

### Post by db5007 on 2008-05-25
Thanks for the tips. I tried both and unfortunately it didnt fix the fanproblem. I am running 64bit 8.04 with an 8500GT.

I installed the latest version of nvclock like this:

```
 sudo apt-get install nvclock
```

Then ran this:

```
nvclock -f -F auto
```

The following error was returned:

```

Error: Your card doesn't support fanspeed adjustments!
```

Anyone know of a good NVIDIA card that hasnt been giving anyone problems?

---

### Post by hotweiss on 2008-05-25
> **db5007 said:**
> Thanks for the tips. I tried both and unfortunately it didnt fix the fanproblem. I am running 64bit 8.04 with an 8500GT.

I installed the latest version of nvclock like this:

```
 sudo apt-get install nvclock
```

Then ran this:

```
nvclock -f -F auto
```

The following error was returned:

```

Error: Your card doesn't support fanspeed adjustments!
```

Anyone know of a good NVIDIA card that hasnt been giving anyone problems?

Try these beta drivers:

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

### Post by db5007 on 2008-05-25
> Try these beta drivers:

[http://www.nvidia.com/object/linux_d...32_173.08.html](http://www.nvidia.com/object/linux_d...32_173.08.html)

That fixed the problem..thanks again.

---

### Post by ubtpenguin on 2008-05-28
hmm, I think I will wait till next nVidia stable driver release

I talked with Linux driver developer over e-mail and submitted log file to him. 

And it is a good news that beta driver solved the problem. 
:lolflag:

---

