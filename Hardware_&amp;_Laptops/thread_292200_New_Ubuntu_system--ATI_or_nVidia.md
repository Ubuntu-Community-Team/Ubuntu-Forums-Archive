---
title: "New Ubuntu system--ATI or nVidia?"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by Towermax on 2006-11-03
I'm basically an absolute Linux noob--I've played with various distros in the past and got them working without much problem, but it's been a couple of years since my last install.

I've decided to get serious and set up a dedicated Linux box using some older hardware:  Abit AT7 Max2 motherboard, Athlon Barton 2800+, 2GB Corsair PC3200 ram, 120GB Seagate IDE drive. 

The only thing I'm not sure of is the video card.  I'm not a gamer and don't plan to do anything graphics intensive, but would still like to have all the eye candy available in Ubuntu.  

I have two ATI cards available--a 9550 and a 9600, both AGP and 128MB each.  However, everyone says to use nVidia with Linux.  So, I'm open to getting an nVidia card.  

I want the easiest to configure setup--I want to spend my time learning Linux, not messing with hardware problems/configuration.

So what graphics card should I use?  Needs to be a good match for the Barton 2800+, have DVI, and AGP, of course.

---

### Post by Predius on 2006-11-03
I'd suggest you stay with your ATi cards. Other than the most cutting edge, the free ATi drivers are very good, sometimes even better than the propietary fglrx. However, nVidia's free driver isn't very good, and you'd probably have to go with the nvidia-glx driver if you needed 3d, something which is provided by many of the open source ATi drivers.

---

### Post by dbott67 on 2006-11-03
Well... nVidia offers better support for the linux movemnet, where as ATI seems to like to keep the cookie jar all locked up.  ATI has released drivers for Linux to support most of the latest cards (and I'm using them on my laptop with ATI Radeon x1400).

The problem is that they are slow to release the drivers, so if you buy leading edge cards, you basically can't reach the full potential of the card until ATI releases updated drivers.

having said that, the current ATI drivers support both cards:

[LIST]
[*][Drivers]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")
[*][Cards supported]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.30.3.html")
[/LIST]

So, I would just use the existing cards, but keep the nVidia in the back of your mind for the NEXT purchase.

-Dave

[]()

---

### Post by RudolfMDLT on 2006-11-03
Both those cards would be fine. Nvidia does setup easier but the Ati cards do work fine. I run a 9600 Pro. Just please install the Dapper Drake release of Ubuntu. For setting up Ati cards in Ubuntu, just click the Ati link at the bottom of this post.

Goodluck,

Rudolf

---

### Post by Towermax on 2006-11-03
Thanks everyone for the *very* quick responses.  I'll use one of my ATI cards.

> Just please install the Dapper Drake release of Ubuntu.

Why Dapper Drake?  I had planned to go with the latest release--is there a problem with it?

---

### Post by Predius on 2006-11-03
There are some stability problems with some people. I suggest you try Dapper, and if you like it, try to upgrade.

---

### Post by RudolfMDLT on 2006-11-04
No, the stabilty will be fine but Edgy uses, well, edgy technology and Ati are yet to release a driver full compatible with the AIGLX system Edgy uses. Loading dapper and then Beryl or Compiz would give you awesome eye candy. For a starter I would load Dapper, it's as solid as a rock and supported for a long time still to come.

---

### Post by Towermax on 2006-11-04
OK, I'll use Dapper.  Thanks again.

---

### Post by chicos on 2006-11-04
i bet it's a bit late, but i have sort of "experience" with ati cards (i was using these for over 6 years) and i would lie if i said these are easier to configure than nvidia.

worst thing about ati cards is something that is yet to be fixed in xorg (there was no way to allocate a fullscreen framebuffer on my 1680x1050 lcd because "1680 mod 32 does not give 0", so i could basically forget about any support for 3d till it is fixed). you will also have to struggle some weirdo ati issues (i have to say that ubuntu already fixes whatever it could except for one thing -- the last time i used my x700 pro with ati drivers it kept crashing system completely if i just moved my mouse - some usb conflicts).

i am using nvidia card for the first time since 1999. and although i was afraid of change, being an ati fan [;)] i can't say i did wrong. not only everything just works (ok, almost everything, but the issue i have has nothing to do with card & soft i believe), but also it is totally silent (7600GT with coolpipes) leaving my system almost completely quiet :)

btw, i made dapper working with aiglx (which was impossible with ati for me), i got compiz up & running (same), i could even use composite extensions with just kde (no compiz) and this didn't work for me either.

so..

you know my opinion. anyways, i don't think i will go back to ati myself.

cheers.

---

### Post by frank05 on 2006-11-04
I think it depends where you're priorities lie. I have used both ATI and nvidia on several linux system over the past few years. If 3d acceleration is more important than using open-source drivers then I'd go nvidia. 

The closed source drivers for ati (known as fglrx) are poorly documented and thus won't give you the flexibility to make a dual-head setup (at least I had to resort to open source drivers, hence losing 3d acc.). That said I haven't tried dual head on an nvidia.

Using closed source drivers from nvidia may cause some kernel compatibility problems because kernel maintainers won't support closed source drivers (and understandably so). However if you use the version of the nvidia drivers in the ubuntu repos, chances are you won't have a problem.

I'm also running silent pipe 7600GT (GIGABYTE) in my rig and would definitely recommend it.

edit: I re-read your post. If you already have the ati cards, I'd definitely try them. Don't spend money unless you're sure an ati won't suit your needs.

---

