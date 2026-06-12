---
title: "Install New Video Card"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by charles.g.moore on 2006-08-10
I just bought a new Nvidia G-force6200 because I couldnt get my ATI Radeon9800 working.

My question is: Do I just unplug the box, switch out cards and restart my Kubuntu 6.06?

The guy at the store said I might want to disable the ATI drivers first but I don't know how you could disable them while running X

I'm obviously not too saavy with the Linux but I have been using it for the past two weeks and love it...

Any help would really help this noob out...

---

### Post by John.Michael.Kane on 2006-08-10
charles.g.moore switch out cards and restart Kubuntu 6.06. from there you should be able to run **[COLOR="Navy"]sudo dpkg-reconfigure xserver-xorg[/COLOR]** that should get the card seen, and allow you select your resolution. from there you could use this [**[COLOR="Red"]HOWTO: Latest NVIDIA drivers[/COLOR]**]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") to get your 3d ect running.



Hope this has been of help.

---

