---
title: "Ubuntu Natty Narwal with Lenovo 420s with nvidia quadro NVS4200M - Can't run X11"
date: 2011-05-19
forum: Hardware
---

### Post by benoitcsirois on 2011-05-19
Hi all,

I just got a Lenovo 420s with the following specs:

Intel Core i7-2620M Processor (2.70GHz, 4MB L3,1333MHz FSB) with Intel 
14.0" HD+ (1600 x 900) LED Backlit Antiglare Display, Mobile Broadband Ready
NVIDIA Quadro NVS4200M Optimus technology (1GB)
6 GB PC3-10600 DDR3 SDRAM 1333MHz SODIMM Memory (2 DIMM)
128GB Solid State Drive, Serial ATA
Intel WiFi Link 1000

And now I'm experiencing major problems with the nvidia card! The complete installation procedure is detailed in my blog entry here:
[http://beakiest.com/posts/installing-linux-on-lenovo-420s](http://beakiest.com/posts/installing-linux-on-lenovo-420s)

Now i've tried to dpkg-reconfigure xserver-xorg and it still won't load X.

I've been using Ubuntu as my primary operating systems for many years now and I need to get this running, please help!

---

### Post by benoitcsirois on 2011-05-19
Update:
- I changed the video devide to "Integrated Graphics" in the Bios
- I change xorg.conf to this:

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

So now I can boot in X and Unity runs.. but no nvidia graphics :(

---

### Post by Ming.Jiang on 2011-05-20
Try this:

[http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml](http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml)

---

### Post by benoitcsirois on 2011-05-21
Thanks Ming Jiang, I installed those drivers, but no luck, same result.

-
Ben

---

### Post by Ming.Jiang on 2011-05-23
Um, to be honest, not surprised[B].
[/B]nvidia doesn't support Linux well at all, especially for new products. Probably needs more time to wait for more updates.

Basically, you should use MacBookPro if you want better support for Linux. However, I am really a big fan of Thinkpad, and I just ordered my new ThinkPad T520 last week  It would take up to 3 weeks for handling and shipping. I just did some google work to get the above link, but have not got the chance to actually test it. I may find more after I get my new laptop. I usually use Fedora instead of Ubuntu though. But I may get the same problem.

We will see...

---

### Post by oguhhhacker on 2011-06-02
Hi, I am also considering to buy an ThinkPad T420s.
My other choice is an HP Elite Book 8460p, but that is not so well-equipped and the grafiks sucks pretty much.
Will the grafik issue work out, or should I go with the Elite Book even though I don't like it so much ?

---

### Post by charliemanson on 2011-06-03
same problem here with the same model of thinkpad t420s..
I just tried to downgrade to 10.10 but after installing drivers v270.xx it freezes.

---

### Post by charliemanson on 2011-06-12
did anybody solved this issue?


Now I'm running with the integrated vga, but it seems such a waste to me..

---

