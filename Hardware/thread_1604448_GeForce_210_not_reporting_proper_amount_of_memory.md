---
title: "GeForce 210 not reporting proper amount of memory"
date: 2010-10-24
forum: Hardware
---

### Post by ggoforth on 2010-10-24
Hello, I seem to be having an issue with a new GPU I installed this afternoon.  The card is a Galaxy GeForce 210 1024 MB DDR2 Hdmi + DVI + VGA.  I am wanting to run a virtual box of windows 7 with full Aero support, which I figured I would be able to do with this card.  However, my pc seems to think there is only 256 MB of video memory (thus, I can't give my virtual box the video memory it needs to run Aero).  Running the command below:

$ lspci -v -s 02:00.0
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
	Subsystem: nVidia Corporation Device 0000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [**size=256M**]
	Memory at ee000000 (64-bit, prefetchable) [size=32M]
	I/O ports at cf00 [size=128]
	[virtual] Expansion ROM at e0000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia-173, nvidiafb, nouveau

Notice in bold the 256 MB of memory.  Why would this not properly report the right amount of memory?  My NVIDIA settings manager shows 1024 MB so I'm not sure where the disconnect is.  Any ideas?

---

### Post by cchhrriiss121212 on 2010-10-24
My output gives the same value for a 512MB 9600GT, it is nothing to worry about.

---

### Post by ggoforth on 2010-10-24
Ok, thanks!  That's good to know.  Maybe a bug?  Anyhow, it looks like the issue lies with virtualbox, and 128 MB of video memory is all you can allocate to the guest os.  Anybody find any way around that? 

Thanks for the reply!

---

### Post by cchhrriiss121212 on 2010-10-24
I don't think it is a bug. 
Edit: see replies below

---

### Post by efflandt on 2010-10-24
On a regular (non-vbox) system my GT220 likewise shows [size=256M] in lspci.   But in NVIDIA X Server Settings it shows **Memory: 1024 MB** under GPU 0.  So what the kernel defaults to for a terminal or X uses may be 2 different things.

---

### Post by jocko on 2010-10-24
The amount of memory you can allocate to the **virtual** graphics card in virtualbox has **nothing** to do with your **real** hardware. Virtualbox is limited to 128 MB, that's just the way it is and there's nothing you can do about it.

---

### Post by Fafler on 2010-10-24
The amount of memory lspci shows is only the amount of memory mapped directly to the PCI bus. So, both your CPU and GPU can "see" 256 MB, but only the GPU can access the rest directly.

Do you have working Direct3D on your VM? AFAIK, VirtualBox only supports OpenGL and you need a 3rd. party Direct3D to OpenGL wrapper to get DirectX3D.

---

### Post by ggoforth on 2010-10-26
Thank you all for the enlightenment regarding the reported video memory.  That makes sense now.  In doing my research regarding the virtual box, you are also correct, Aero is not currently supported in a VM.  Not a big deal, I can still get my work done :)

---

### Post by andreselsuave on 2010-11-08
Hello there, I have the same video card and I don't  seem to be getting the expected performance for a 1024 Mb card. I tried some 3d test benches and I get pretty low FPS(~10) @1680x1050   and also the window manager (Kwin) hasn't improved significantly. It is also very slow. And I can't choose opengl in Kwin, just xrender. If I force it, the screen will freeze and won't work.

Anyone is haveing the same issues?

Thank you

---

### Post by Fafler on 2010-11-09
Are you using the right driver?
Memory != performance. The GT210 is a really slow device with only 16 cuda cores and a 64 bit memory bus. The real reason it has 1024 mb memory is that it sells. People see a cheap card with a gig of memory and buys it.

---

### Post by andreselsuave on 2010-11-09
Really? Didn't know... I asked for a nice card to the hardware department and this is what I got. I suppose they fell for the trick hehe.

Anyways, my driver version is 260.19.06. 

So, for example, won't this card perform well for Starcraft 2?

And, I would appreciate a lot if you gave me some guidelines on evaluating video hardware.

Thanks a lot for your comment... I was going crazy expecting great performance for this card...

---

### Post by Fafler on 2010-11-09
The driver seems right. Still, you should look at the output from
```
glxinfo | grep string

```
to see if everything is working alright. As for SC2, i havent tried it yet and really have no idea about system requirements, but i guess it depends on the video settings. The GT210 is still faster than the Intel GMAxxxx devices, which also runs SC2 at low settings.

[http://www.tomshardware.com/reviews/gaming-graphics-radeon-hd-6870-radeon-hd-6850,2782.html](http://www.tomshardware.com/reviews/gaming-graphics-radeon-hd-6870-radeon-hd-6850,2782.html) is a good place to start. In general, Nvidia cards seems to be better supported under Linux than AMD cards.

---

### Post by Yellow Pasque on 2010-11-09
> And I can't choose opengl in Kwin, just xrender. If I force it, the screen will freeze and won't work.
This is a known issue with ATI driver in KDE 4.5.x, but I don't remember it affecting nvidia users.

---

