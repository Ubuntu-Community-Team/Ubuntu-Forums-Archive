---
title: "Drop in a new kernel? Vaio 560P"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by leaded on 2006-06-22
Hey guys. I've posted previously about how my Vaio doesn't boot without kernel panics. I thought before about building a new kernel but gave up and went back to Windows hoping that Edgy would work for me months down the road. 

I was searching for the package name for the kernel headers the other day because I needed them for the Cisco VPN package for my desktop. Upon searching the boards, I found [this post on compiling a vanilla kernel from kernel.org]("http://ubuntuforums.org/showthread.php?t=157560&highlight=kernel+headers+dapper").

When I was posting about my previous problems, it was suggested that the kernel was the problem because Debian worked fine with 2.6.14 but Ubuntu didn't with 2.6.17 or 16 or whatever.

Is it possible to use my desktop computer with Dapper and build my own kernel and use a live cd and drop it in my laptop's file system? My desktop is a 3.2 GHz P4 with HyperThreading and the Vaio is a 1.86 GHz Pentium M.

---

### Post by leaded on 2006-06-27
Can anyone help me out here?

---

### Post by Hellkeepa on 2006-06-27
HELLo!

Yes, it should be quite possible. However, you need to take heed and make sure you compile the modules and drivers that you need on your laptop. Otherwise you won't be getting far.
I'd be prepared for some trial-and-error testing on this one, so don't go deleting your old kernel until you've thuroughly tested the custom one.

Alternatively you could also update the kernel via Synaptic, which is probably the easiest choice. You'll find the available ones if you search for "linux-headers", and it'll automaticly add any dependancies as well.

Happy codin'!

---

