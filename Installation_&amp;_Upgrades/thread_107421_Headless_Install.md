---
title: "Headless Install"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by Connollyir on 2005-12-23
I need to put an operating system in a server without a video output in a 2u case. I want to know if I can plug the drive that I am going to use into my own pc, get Ubuntu Server ed. set there and just migrate the drive or will that cause a hardware issue? Does Ubuntu compile specifically at install for present hardware and need to recompile for other hardware, like the stuff it would encounter in this swap?

Thanks

-Ian

---

### Post by Joey French on 2005-12-23
Yes, i would love to know as well. I want to do a headless install to a mini-itx with server install, and would love to set up the disc on my desktop, then transfer it to the mini box.

---

### Post by kosmic on 2005-12-23
If all the hardware in the 2u case is suported in Ubuntu then it should work out of the box :)

---

### Post by Connollyir on 2005-12-23
[QUOTE=kosmic]If all the hardware in the 2u case is suported in Ubuntu then it should work out of the box :)[/QUOTE]

Well I guess thats the key phrase, if all the hardware is supported. I'll just have to throw down with it and see how it goes.


Thanks

-Ian

---

### Post by kosmic on 2005-12-24
Hi, Don't forget to post here the result :)

---

### Post by xmastree on 2005-12-24
Is it not possible to temporarily add a video card to the unit just for the install?
I realise that it might not fit the case, but you could do it out of the case then build it.
However, I'm not sure how well it would cope with **no** video hardware available.

FWIW, I recently moved a HD from one motherboard to another, and it had no problems despite the new one being VIA based wheras the old one was Intel.

---

### Post by Connollyir on 2006-01-04
Ok sorry about the time-lag between posts but its been a really busy couple of weeks!

To conclude: 

The server is up and running, and configuring the hard disk in another machine and transplanting it worked almost flawlessly. The only problem I ran into came not from the Ubuntu distrobution on the disk but from the bios of the motherboard I used - I needed to disable the warnings for no video card in order to get it to post. 

It is probably important to note that I used the Server version of Ubuntu for the project so I didn't have to deal with any gui or graphical problems that could arise with varying hardware in a regular Ubuntu installation.

Thanks for the advice

-Ian

---

