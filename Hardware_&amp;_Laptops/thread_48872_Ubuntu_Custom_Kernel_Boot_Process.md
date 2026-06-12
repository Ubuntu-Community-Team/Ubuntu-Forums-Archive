---
title: "Ubuntu Custom Kernel Boot Process"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by zrr on 2005-07-14
Hi

I installed a custom Kernel 2.6.11.12.2 on my new Ubuntu maschine. When I boot from custom kernel everything works great but I do not get the very first message witch I do get when I boot from the Ubuntu-Kernel witch is "Starting Ubuntu"...

Can anybody point me to a nice Ubuntu-Boot-Howto?

 ](*,) 
Thanks
Zeno

---

### Post by scoon on 2005-07-14
Hey there, 

[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

That is a good place to start. 

regards, 

scoon

---

### Post by zrr on 2005-07-14
Well thanks, for the link. I guess I was not specific enough, sorry about that. My question is: Is there any document that describes the boot process of Ubuntu in a detailed manner. The boot process of Ubuntu seem quite intransparent to me (in comparison to the one of Gentoo where I can just add boot-scrips with ie "rc-update add net. eth0 default").

Somehow when I boot from my custom kernel the "Ubuntu boot" does not start in the right manner as I do not get the very first notice of "Starting Ubuntu ..." also kdm_greeter does not want to start and when I type "StartX" I tells me there is already an xserver running (thoug I can see none ;(.

I installed BUM (Boot Up Manager [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)) but that does not want to start either in the KDE environment, it throws me an GTK-Error.

I'm runng on a PPC. The default Ubuntu Kernel works sweet even with my Prism54 Wireless card, witch is very nice indeed but I want my own custom kernel.

Ok, all is sweet now! I forgot to put the Unix Domain sockets in my Kernel config ;( my stupid. Sorry for the fuss.

 \\:D/ 

Here is my Kernel config for PPC Tibook G4 550 Mhz.
[http://www.ywesee.com/uploads/Main/config-2.6.12.2.txt](http://www.ywesee.com/uploads/Main/config-2.6.12.2.txt)

Thanks for any help and Feedback.
Zeno

---

### Post by scoon on 2005-07-14
Hey there, 

Sorry, not much help with PPC as i am x86.  Good luck and happy google-ing.


regards, 

scoon

---

