---
title: "Need help getting ubuntu to work on my laptop -drivers"
date: 2009-02-20
forum: Hardware
---

### Post by Njord on 2009-02-20
You'll have to bare with me, as this is one of the first times I've used linux.

The laptop I'm using: Acer Aspire AS5920-6642 

Searching through the forum I managed to get Ubuntu installed to my 16GB flash drive. Though loading, and browsing on firefox is a bit slow, everything else seems to be ok.

The problem is ubuntu sees my wireless card (intel wm395abg) but I can't connect, or see any networks. I can connect to the internet via wired.
Under hardware drivers I can see my wireless card, and it says its in use (active). Deactivating it and reactivating it, I can see it at the top right of the screen as 'enable wireless' but it does nothing. Network tools doesn't list the device either.

Ubuntu is telling me I have 251 updates, but when I click install the program just hangs indefinitely.

In hardware drivers It lists video card drivers (my video card is: NVIDIA® GeForce® 8600M GS) but both the NVIDIA 173 and 177 give me the error 
"SystemError: E:I wasn't able to locate a file for the nvidia-settings package. This might mean you need to manually fix this package. (due to missing arch"

Any help is greatly appreciated, and thanks!

Edit:
Oh yeah, I dont have any swap space because this is installed onto a flash drive if that makes any difference. The reason is because I have 3GB of ram, and right now I'm only using 300MB anyway.

---

### Post by Njord on 2009-02-22
Bump

---

### Post by Njord on 2009-02-22
bump

---

### Post by ProNux on 2009-02-24
If I am not mistaken, your Intel wireless LAN is Intel 3945abg?  My Acer 4710 has the Intel 3945abg wlan.  Ubuntu 8.04 automatically detected and configured it.

What Ubuntu version you have?

I also read some posts that Ubuntu 8.10 has more built-in support for wireless lan cards.

---

### Post by meep_meep on 2010-05-15
> SystemError: E:I wasn't able to locate a file for the nvidia-settings package. This might mean you need to manually fix this package. (due to missing arch"

I had this issue as well where it wouldn't let me install anything on 10.04 after it had rebooted from installing my nvida drivers.  Then went to update manager and it only had one package in there to update (I had just udated) and it was nvida-settings.  So I updated and it fixed my issue of not being able to install updates/new programs via software centre!

---

