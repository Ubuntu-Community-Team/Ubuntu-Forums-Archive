---
title: "Ethernet not working in eeepc 701"
date: 2008-08-10
forum: Hardware
---

### Post by mendieta on 2008-08-10
Hi

I have an eeepc 701, happily running Kubuntu 8.04. However, the wired, ethernet connection is not working. What gives ?

Here are some details:

[LIST]
[*]Ethernet is enabled in the Bios
[*]atl2 is loaded according to lsmod
[*]The network manager app shows both interfaces (ethernet and wireless), but only wifi works.
[*] If I reset the computer while connected to the modem-router via ehternet, I don't get a dhcp lease. All other machines do. It's something about the eeepc.
[*] The ethernet connection used to work in Xandros a couple bios updates ago, but lately it stopped working in (the now replaced forever) Xandros
[/LIST]

Am I missing something ? 

Apparently, Ubuntu provides the ethernet driver OOTB, which is the one loaded, or am I missing something ? Should I compile a better driver by hand, as you need to do for wifi?

Any help would be greatly appreciated. Googling around didn't help much, except for the tip about removing the battery and removing the power cord, which helped me see the eth2 interface, but no more than that. 

Thanks so much!

---

### Post by starcannon on 2008-08-10
This is the script pack I like to use, gets everything all set up nice for me, run the tweakgnome one first, makes life easier right out of the gate.

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

theres a readme file, its all pretty straight forward, it even has an uninstaller if you decide you don't like it later.

---

### Post by mendieta on 2008-08-10
> **starcannon said:**
> This is the script pack I like to use, gets everything all set up nice for me, run the tweakgnome one first, makes life easier right out of the gate.

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

theres a readme file, its all pretty straight forward, it even has an uninstaller if you decide you don't like it later.

Thanks a lot! Pretty much everything is working now, so I'll probably read the script and see what it does for ethernet, in particular. Cheers!

---

