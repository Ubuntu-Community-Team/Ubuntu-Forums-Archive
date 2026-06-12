---
title: "Jaunty ATI Radeon HD3400 no desktop"
date: 2009-04-24
forum: Hardware
---

### Post by llama_attack on 2009-04-24
Hi, I've just updated to Jaunty but just as the desktop should load, i get a load of weird graphical corruptions, and I can't see anything at all on my desktop, and have no idea whether the computer is responding or not. There are instructions on the ATI website on how to install the new driver in a desktop environment, but I can't get that far. Could any one tell me how to install these new drivers completely from the command line?

Thanks in advance

---

### Post by prshah on 2009-04-24
> **llama_attack said:**
> i get a load of weird graphical corruptions, 

Please see the linked post; are the graphical corruptions the same? In this case, it was detecting the wrong resolution; see if the posted fix works for you, otherwise post back for another way.

---

### Post by llama_attack on 2009-04-24
I think you forgot to link the post

---

### Post by prshah on 2009-04-24
> **llama_attack said:**
> I think you forgot to link the post

Oops.. [ Re: Upgrade from 8.10 (64-bit) to 9.04 causes system to not fully boot]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2")

---

### Post by llama_attack on 2009-04-24
Nope, Did nothing to fix it, exactly the same corruptions

---

### Post by llama_attack on 2009-04-24
Ok, I've worked around the problem, I had to uninstall fglrx and then reinstall xorg, so now I have a working desktop. No compiz, but I can deal with that until they fix fglrx. Thanks for your help

---

