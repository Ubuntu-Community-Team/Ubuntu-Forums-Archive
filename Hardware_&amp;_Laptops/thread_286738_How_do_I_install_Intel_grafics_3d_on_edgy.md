---
title: "How do I install Intel grafics 3d on edgy?"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by bacsa81 on 2006-10-28
Hi folks!
I bought an nx7400 laptop I could run up everything by now expect the 3d capabilities of my intel grafics chip.
My lspci -v looks like this:

csaba@csaba:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a2
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30a2
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at f4400000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 4000 [size=8]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at f4480000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a2
        Flags: bus master, fast devsel, latency 0
        Memory at f4500000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

I was looking for the howto to install the 3d for this card, but couldn't find, please someone could me help out?
And if you have time please share with me your experience.
Thank you in advance!
Best regards
Csaba

---

### Post by unlokia on 2006-10-28
Hi - have you managed to get the native screen resolution working yet?. You will need to install "915resolution" and then reboot - I take it by "3D" you mean you want the 3D Desktop effects (XGX/AIGLX) etc??

If this is so, click HERE [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

I should be glad to help if I may at all.

Regards

Matt.

---

### Post by bacsa81 on 2006-10-28
Actually I haven't done anything with my fresh edgy yet, I have nvidia on my desktop and I had to install some packages to have 3d and opengl capabilities.
Now I couldn't find any howto what do I need to install on my laptop to have 3d and opengl.. Maybe I sound stupid :) But this is my first Intel graphics chip.
Thnaks Csaba

---

### Post by unlokia on 2006-10-28
You need to ```
sudo gedit /etc/apt/sources.list
``` and UNcomment all the repositories (remove the ## before the deb [http://)-](http://)-) then run ```
sudo apt-get update
``` then you run SYNAPTIC and install "915resolution".

Now reboot!.

Next, just follow the link I gave in my first reply, to enable 3D. I know this works because I have the INTEL 915GM chipset on this laptop I am on now, and it works like a dream!!.

---

