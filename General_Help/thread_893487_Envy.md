---
title: "Envy"
date: 2008-08-18
forum: General Help
---

### Post by HpZ on 2008-08-18
Im trying to use Envy to install NVIDIA drivers. Can someone tell me how to install and run it? I tried this [http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html](http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html)

but this happened: andy@andy-laptop:~$ wget [http://albertomilone.com/ubuntu/nvidia/scripts/](http://albertomilone.com/ubuntu/nvidia/scripts/)
--15:46:48--  [http://albertomilone.com/ubuntu/nvidia/scripts/](http://albertomilone.com/ubuntu/nvidia/scripts/)
           => `index.html'
Resolving albertomilone.com... 208.109.14.20
Connecting to albertomilone.com|208.109.14.20|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
15:46:49 ERROR 403: Forbidden.

andy@andy-laptop:~$ envy_0.8.1-0ubuntu6_all.deb
bash: envy_0.8.1-0ubuntu6_all.deb: command not found
andy@andy-laptop:~$ 



please help. TY<3

---

### Post by Elfy on 2008-08-18
If this is hardy - install it from synaptic. If previous versions the easiest way is to get it from the envy site.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You need to be aware that previously if there was a kernel update you needed to redo the envy thing, from what I remember - afaik it's not an issue with the hardy synaptic envy

---

### Post by tuxxy on 2008-08-18
Search for **envy-gtk** in synaptic and install it, or from terminal type

```
sudo apt-get install envy-gtk
```

---

### Post by HpZ on 2008-08-18
I ran it and got this error: python pulse.py nvidia 
root@andy-laptop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.8
ENVY ERROR: Your Operative System does not seem to be supported by Envy

---

### Post by tuxxy on 2008-08-18
Which command did you run?

---

### Post by cdtech on 2008-08-18
I take it you have a problem with your screen resolution?

If you go into the "**System > Administrator > Synaptic Package Manager**" select search and type in "nvidia" you will see the "envyng-gtk" and the "envyng-core".

If you did a kernel upgrade be sure to select the "linux-restricted-modules" for the upgraded kernel version as well.

Type in a terminal:
```
**sudo envyng-gtk**
```

---

### Post by Elfy on 2008-08-18
Which version of ubuntu do you have?

I get that error message at the moment with envy and intrepid.

---

### Post by cdtech on 2008-08-18
> **forestpixie said:**
> Which version of ubuntu do you have?

I get that error message at the moment with envy and intrepid.

I'm running **Hardy**.

---

### Post by cowboyup6983 on 2008-08-18
> **tuxxy said:**
> Search for **envy-gtk** in synaptic and install it, or from terminal type

```
sudo apt-get install envy-gtk
```

use this it worked for me. i have ubuntu 8.04 with Nvidia 8800GTS.

---

### Post by HpZ on 2008-08-18
okay guise. i got it to work and it looks fabulous. ty all.

---

### Post by Elfy on 2008-08-18
> **cdtech said:**
> I'm running **Hardy**.sorry meant to reply to OP ...

---

### Post by cdtech on 2008-08-18
:) whooooppppssss....

---

