---
title: "Very odd delayed boot"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by mperedithe on 2008-02-04
Please Help!!!

I have installed Ubuntu 7.10 on my Gateway laptop twice now and am experiencing the same problem.  When I boot up the laptop it goes through the normal motions until it gets to past the startup where normally I would imagine seeing the text as the drivers are all loaded and everything else that usually displays during boot up.  With this OS however the screen goes blank after it announces that it is loading the grub and remains blank for at least 3 minutes at which point the login screen appears.

As I said this is very odd in my experience and rather annoying to wait all that time.
Any help will be greatly appreciated.

Thanks in advance.
Mperedithe

---

### Post by stalker145 on 2008-02-04
> **mperedithe said:**
> Please Help!!!

I have installed Ubuntu 7.10 on my Gateway laptop twice now and am experiencing the same problem.  When I boot up the laptop it goes through the normal motions until it gets to past the startup where normally I would imagine seeing the text as the drivers are all loaded and everything else that usually displays during boot up.  With this OS however the screen goes blank after it announces that it is loading the grub and remains blank for at least 3 minutes at which point the login screen appears.

As I said this is very odd in my experience and rather annoying to wait all that time.
Any help will be greatly appreciated.

Thanks in advance.
Mperedithe

This sounds like the same problem I had when I installed 7.10 on my Dell. Try this out and see if it works:```
sudo nano /boot/grub/menu.lst
```Find your primary boot which probably looks like this:```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic boot=UUID=5a9e8f79-40ed-4897-a16e-3d8b4b21d3d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```and delete the word "splash" from the kernel line. Reboot your computer and all should be well in the world.

---

### Post by mperedithe on 2008-02-07
Thank you, thank you.  This appears to have helped.  The laptop boots much faster and displays the proper series of whats going on.

---

