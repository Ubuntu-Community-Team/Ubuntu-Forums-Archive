---
title: "Problem with intel 945G chipset"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by Chunyong on 2005-10-20
Hi all,

I installed ubuntu 5.10 on my IBM TC M52 with itnel 945G chipset. This is the output when I did an "lspci":

0000:00:02.1 Display controller: Intel Corp.: Unknown device 2776 (rev 02)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corp.: Unknown device 27d2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:02:00.0 Ethernet controller: Intel Corp.: Unknown device 108c (rev 03)

It seems like the os is unable to recognize the chipset I am using. Is there any workaround for this? :confused: 

Thanks in advance~

---

### Post by ektich on 2005-11-10
[QUOTE=Chunyong]Hi all,

I installed ubuntu 5.10 on my IBM TC M52 with itnel 945G chipset. This is the output when I did an "lspci":

0000:00:02.1 Display controller: Intel Corp.: Unknown device 2776 (rev 02)
<snip>
[/QUOTE]

I just installed 5.04 on Dell GX620, and ran into similar problem. The video card is identical to yours (device 2776). I hoped that 5.10 would solve it, but apparently it doesn't. 

I've reconfigured x-server to use "vesa" driver instead of "i810", and it actually worked! I haven't checked what features I'm missing, but hey, it's better than nothing. 

Here's how one can reconfigure x-server (apart from just editing /etc/X11/xorg.conf):
1. sudo dpkg-reconfigure xserver-org
2. say "no" to Attempt to autedetect video hardware
3. choose "vesa" as desired X server driver (instead of i810, or whathever driver 5.10 trys to use)

it's going to ask dozen or so questions, default answers shlould do fine.

Ektich

---

### Post by Teroedni on 2005-11-10
Doesnt it work with normal intel graphics driver (i810)?
You tried the latest from intel?

---

### Post by ektich on 2005-11-10
[QUOTE=Teroedni]Doesnt it work with normal intel graphics driver (i810)?
You tried the latest from intel?[/QUOTE]

i810 that comes with 5.10 works out-of-the-box just fine... 
Then Chunyong said "the os is unable to recognize the chipset" I thought he meant X doesn't work. (It is definitely not working on 5.04).

I'm sure by replacing driver in 5.04 it is possible to make it work as well. The thing is - I don't want to do it. vesa driver will do for me until I will be able to upgrade everything to 5.10 (or maybe the next one, if it will be out).

Fixing lspci "problem" requires patching the kernel I suppose, but I don't realy see the need for it.

Sorry for misleading post :)

---

### Post by davidmoore83 on 2006-03-26
[QUOTE=Chunyong]Hi all,

I installed ubuntu 5.10 on my IBM TC M52 with itnel 945G chipset. This is the output when I did an "lspci":

0000:00:02.1 Display controller: Intel Corp.: Unknown device 2776 (rev 02)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corp.: Unknown device 27d2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:02:00.0 Ethernet controller: Intel Corp.: Unknown device 108c (rev 03)

It seems like the os is unable to recognize the chipset I am using. Is there any workaround for this? :confused: 

Thanks in advance~[/QUOTE]


I have this same issue as well as a constantly active HD light......anyone have solutions to this yet?

---

