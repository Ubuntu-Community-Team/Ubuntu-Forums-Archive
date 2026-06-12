---
title: "For Beginners:Why Xubuntu? Cause it set my PC on fire..."
date: 2008-10-01
forum: General Help
---

### Post by aimpau on 2008-10-01
figuratively that is. :)

I've been semi-lurking long enough in these forums to know that a lot of new users are usually greeted with a lot of problems with their freshly picked u/k/xubuntu and therefore, flood these forums with lots of inquiries. I would like to change that a bit and at least show our new linux users the cool side of xubuntu.

(to the mods, you can move this thread anywhere but I just want to show the beginners what I'm talking about in terms of xubuntu extensibility.) :D

To continue:

[http://i239.photobucket.com/albums/ff173/aimpau323/xubuntu-fire.png](http://i239.photobucket.com/albums/ff173/aimpau323/xubuntu-fire.png)
**My Desktop on fire!**

[http://i239.photobucket.com/albums/ff173/aimpau323/cube.png](http://i239.photobucket.com/albums/ff173/aimpau323/cube.png)
**The Cube**

[http://i239.photobucket.com/albums/ff173/aimpau323/program-close.png](http://i239.photobucket.com/albums/ff173/aimpau323/program-close.png)
**Now you see it...**
[http://i239.photobucket.com/albums/ff173/aimpau323/disappear.png](http://i239.photobucket.com/albums/ff173/aimpau323/disappear.png)
**Now it's beamed up back to enterprise...**

[http://i239.photobucket.com/albums/ff173/aimpau323/rain.png](http://i239.photobucket.com/albums/ff173/aimpau323/rain.png)
**Rain and lots of it.**

[http://i239.photobucket.com/albums/ff173/aimpau323/expo.png](http://i239.photobucket.com/albums/ff173/aimpau323/expo.png)
**Now, don't complain about having no space at all.**

My desktop specs:
512MB DDR2
Sempron 1200 LE 2.0Ghz
Nvidia video chip 64MB

How to:
So, you want to explore? All of these are possible through a cool program called **compiz-fusion**.

Steps:
1. First, if you're using either Nvidia or ATI, make sure you've installed:
```

envyng-gtk

```
2. That program would better guide in setting up you video chip or card.
3. After that, install:
```

compiz-fusion

```
4. After it has installed everything, I prefer to use emerald instead of the built-in window decorator of compiz (gtk-window-decorator) so, optionally, you can:
```

sudo apt-get install emerald

```
5. In your desktop, press Alt+f2, then type in:
```

compiz --replace

```

That's it. About all other inquiries, try to post here if you want. :)

Edit:
Oh and just to point out, yes, xubunutu(xfce) has a built-in compositor but all it just do is to composite. :) It is better for low-end computers.

edit 2:
gnome-screenshot as well as xfce4-screenshot-plugin messed up some of the screenshots. :D

---

### Post by Paqman on 2008-10-01
> **aimpau said:**
> 
Oh and just to point out, yes, xubunutu(xfce) has a built-in compositor but all it just do is to composite. :) It is better for low-end computers.


I actually quite like XFCE's compositor. It can do drop shadows and transparency, plus it means you can run apps that need a compositor like Avant Window Navigator.

---

### Post by aimpau on 2008-10-02
> **Paqman said:**
> I actually quite like XFCE's compositor. It can do drop shadows and transparency, plus it means you can run apps that need a compositor like Avant Window Navigator.

I do like it too. I always use it to "upsell" xubuntu to foreigners (MS users). :D

---

### Post by paulo21 on 2008-10-04
I got curious about your computer performance, because I have an Athlon which gets sluggish most oart of the time.
So, even using compiz your computer's performance is ok? How about CPU usage?

Thanks in advance.

---

### Post by overdrank on 2008-10-04
Moved to  Desktop Effects & Customization :)

---

### Post by aimpau on 2008-10-04
My performance is ok. I even run screenlets with it. Hmmm... Can you post your specs here? Including video card/chip.

Edit:
About CPU usage...I don't quite follow you there since my CPU goes above 0% only when I actually do something like:

firefox + seq24 + rtorrent + avidemux + gimp

Usually a little over 50% but goes back to zero when all is quiet.

Edit2:
Thanks overdrank for the move. Better this way. :D

---

### Post by DAaaMan64 on 2008-10-04
What repository is compiz-fusion in? apt can't seem to find the package :(

---

### Post by paulo21 on 2008-10-04
> **aimpau said:**
> My performance is ok. I even run screenlets with it. Hmmm... Can you post your specs here? Including video card/chip.

Edit:
About CPU usage...I don't quite follow you there since my CPU goes above 0% only when I actually do something like:

firefox + seq24 + rtorrent + avidemux + gimp

Usually a little over 50% but goes back to zero when all is quiet.

Edit2:
Thanks overdrank for the move. Better this way. :D
I am having trouble using ubuntu, my cpu usage reaches 100% if i use firefox+print pdf+deluge. I switched to xfce but didn't get big difference. Usually I run at 50% all the time.

My specs: Athlon 2600 Xp, 2GB DDR, GeForce Fx5200, HD with 250Gb free, mb Asus A7V400-MX-SE, power-Seventeam 450W.

---

### Post by aimpau on 2008-10-05
Dude, your specs are so beyond what I have. Is it safe to assume that you had first Ubuntu then you shifted to xfce? Have you tried doing a fresh install of xubuntu instead?

@DAAman
compiz-fusion is in the repos included in xubuntu.

---

### Post by cic.11 on 2008-11-02
whenever i do compiz -- replace i have no window decorations. does any one know why this happens?
i have an intel graphics card

> bobo@bobo:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	Memory at 90100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0
	Memory at 88000000 (32-bit, prefetchable) [size=128M]
	Memory at 80100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>


---

### Post by aimpau on 2008-11-03
But can you still perform some of the compiz features? Make sure you have the correct drivers in

```

sudo displayconfig-gtk

```

If you video chip doesn't support the 3d stuff, then we have to do something else. I think there's a workaround regarding that.

---

### Post by cic.11 on 2008-11-03
> **aimpau said:**
> But can you still perform some of the compiz features? Make sure you have the correct drivers in

```

sudo displayconfig-gtk

```

If you video chip doesn't support the 3d stuff, then we have to do something else. I think there's a workaround regarding that.

ok when i run compiz i am not able to do any of the features a checked the driver and i do not have the correct driver
this is what i got
> bobo@bobo:~$ sudo displayconfig-gtk
[sudo] password for bobo: 
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:63: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:64: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:65: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-uggZon5754/xauthority
Got pid 5770
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) I810(0): No Video BIOS modes for chosen depth.
Fatal server error:


---

### Post by IeU on 2008-12-02
Thanks !

Just trying to get more themes for emerald ! :)

---

### Post by OrangeCrate on 2008-12-02
Cool thread! Thanks aimpau, I've been waiting for one like this for a long time, and I must have missed it when you first posted. I notice the thread is a bit long in the tooth, but if you and others are still lurking here...

-----

I'm a great fan of Xubuntu, but every time I enable the compositor, I get some random screen flicker, scrolling issues, and once in a while, it'll just simply crash. (I assuming that if the compositor is causing conflict, it's a no go Compiz as well?)

If anyone has a clue as to what's wrong, and if there's anything I might be able to do about it, I'd sure appreciate a comment.

I'm not sure what to include here in the way of information, but taking a hint from a post above ^, I'll post this for the HP 512n in my signature:

$ lspci -v

00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
	Subsystem: Trigem Computer Inc. Device 7148
	Flags: bus master, fast devsel, latency 0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
	Subsystem: Trigem Computer Inc. Device 7148
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f4100000-f41fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Intel Corporation 82801AA IDE Controller
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1080 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

<snip, but I can add more if necessary>

---

### Post by OrangeCrate on 2008-12-05
**Update**

In case anyone has been following this thread, due to having the same issue with compositor, there is a long standing issue with this, between Xfce, and the Intel 810e chipset. At this time, it's a no go, and it routinely creates the issues I outlined above ^.

Oh well.

---

### Post by crav on 2008-12-05
> **aimpau said:**
> 
@DAAman
compiz-fusion is in the repos included in xubuntu.

I respectfully disagree:
```
sam@mouse:~$ sudo apt-get install compiz-fusion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fusion
sam@mouse:~$ 

```

Any ideas on how I might locate these files, or should I lazy-out and compile it myself?

---

### Post by aimpau on 2008-12-05
my mistake. in their website, their known as compiz fusion (the plugins), however the package is just compiz.

---

### Post by Gamak on 2009-02-26
Hey, whats the link to download these files for xubuntu? i looked on compiz-fusion.org i think it was, and they were not there for xubuntu? :S

---

### Post by 133794m3r on 2009-03-21
ok now you said to help xubuntu wouldn't installing the compiz and such require more cpu more memory and such things than the standard one that comes with xubuntu?

I have a 1.59Ghz single core AMD CPU and an ATI radeon Xpress graphics chipset plus 1GB of RAM i came to Xubuntu for the more ease on my weak system. So wouldn't what you suggest mess that up?

---

### Post by foxy123 on 2009-04-25
I have installed compiz on Jaunty and it runs sort of OK. There are still two problems. The first is that I have to run > compiz -fusion --replace twice to start it. Another problem is that I cannot do any configuration with ccsm now. It works perfectly fine on Intrepid. I've got a feeling that it is something to do with xfce 4.6...

---

