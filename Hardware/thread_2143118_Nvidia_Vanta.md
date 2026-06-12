---
title: "Nvidia Vanta"
date: 2013-05-07
forum: Hardware
---

### Post by brendanwr on 2013-05-07
My computer keeps saying error this system is running in a low-graphics mode. I have tried to update and reinstall the nvidia drivers but everytime I do then nothing will appear and I have to boot into graphic safe mode to delete the driver

---

### Post by mörgæs on 2013-05-07
Hi, welcome to the fora.

Please run ```
sudo lshw > lshw.txt
``` and post lshw.txt.

---

### Post by brendanwr on 2013-05-07
```
[B][COLOR=#000000][FONT=Arial]*-display UNCLAIMED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	product: NV6 [Vanta/Vanta LT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	vendor: nVidia Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	bus info: pci@0000:01:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	version: 15[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	width: 32 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	clock: 66MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	capabilities: pm agp agp-2.0 bus_master cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	configuration: latency=64 maxlatency=1 mingnt=5[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]            	resources: memory:40000000-40ffffff memory:42000000-43ffffff(prefetchable)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[/B]
```

---

### Post by brendanwr on 2013-05-07
> **mörgæs said:**
> Hi, welcome to the fora.

Please run ```
sudo lshw > lshw.txt
``` and post lshw.txt.
Thanks, is this all you need?

---

### Post by mörgæs on 2013-05-07
Whoa, that's an old card. I don't know this one, sorry. Moving to Hardware to see if anyone there is able to help.

By the way, you should begin with a fresh install of Lubuntu 13.04 as 10.04 is out of support.

---

### Post by brendanwr on 2013-05-08
> **mörgæs said:**
> Whoa, that's an old card. I don't know this one, sorry. Moving to Hardware to see if anyone there is able to help.

By the way, you should begin with a fresh install of Lubuntu 13.04 as 10.04 is out of support.
Do you think install Lubuntu would solve the issue or no?

---

### Post by mörgæs on 2013-05-08
Regardless of the card problem it's time to leave 10.04 and switch to something supported, preferably a light distro. 

Your card is from around 2000 and it wasn't even considered powerful when it was new. I think you should be happy for just getting some kind of picture out of it. Demanding a high resolution is not realistic.

---

### Post by brendanwr on 2013-05-09
> **mörgæs said:**
> Regardless of the card problem it's time to leave 10.04 and switch to something supported, preferably a light distro. 

Your card is from around 2000 and it wasn't even considered powerful when it was new. I think you should be happy for just getting some kind of picture out of it. Demanding a high resolution is not realistic.

I know its old, but I just want to play around with it. And I'm not demanding high res I just don't want that message to pop up every time

---

### Post by arsenic23 on 2013-05-09
Nvidia dropped support for that card years ago.  If you want it to work you'll need to install legacy drivers.  I think you need a 71 version nvidia-glx-legacy or something similar.

The newest Nvidia drivers do not support that card.

---

