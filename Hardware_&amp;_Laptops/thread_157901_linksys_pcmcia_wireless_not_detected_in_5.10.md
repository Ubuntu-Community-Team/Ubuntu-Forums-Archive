---
title: "linksys pcmcia wireless not detected in 5.10"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by adityasen on 2006-04-10
hi all...
i'm quite new to linux, and i gave ubuntu a shot. its the only distro that worked on my laptop, after successive failures with fedora and suse.
anyhow, the thing is that i cannot get my pcmcia linksys wireless (WPC54G) to work on ubuntu. i've read through most of the articles on how to get wireless working, and  have also tried with ndiswrapper. the thing is, that my card is not detcted by ubuntu at all. so how do i fix that?

thankx
peace
aditya

---

### Post by cusco on 2006-04-10
[QUOTE=adityasen]and  have also tried with ndiswrapper. the thing is, that my card is not detcted by ubuntu at all.
[/QUOTE]

 I had that card before it worked fine with nediswrapper

after installing ndiswrapper, get the driver from the site linksys.com or the cd and then just use: sudo ndiswrapper -i bcm*.sys

it will install the driver .. then check it with ndiswrapper -l to list it and modprobe ndiswrapper

gl

---

### Post by Quirky on 2006-04-10
ndiswrapper -i uses the .inf file, rather than the .sys one. But apart from that, this is the way to go.

---

### Post by taurus on 2006-04-10
Hey, I have the same card and got it to work with Breezy.  I recommand you download the driver from Linksys' v3.  Unpack it and install the driver with ndiswrapper!  I now have it working in Dapper Flight 6 as well.  If you're not sure how to do it, PM me and I will show you...

---

### Post by macdo on 2006-04-26
I wrote a couple of howtos, they might help...
[URL="http://macdo10.free.fr/wordpress/?p=166"]
breezy[/URL]
[dapper]("http://macdo10.free.fr/wordpress/?p=217")

---

