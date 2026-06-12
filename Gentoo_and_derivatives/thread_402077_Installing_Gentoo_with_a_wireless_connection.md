---
title: "Installing Gentoo with a wireless connection"
date: 2007-04-05
forum: Gentoo and derivatives
---

### Post by Frostmourne on 2007-04-05
Hello, I would like to install Gentoo on my laptop, but I only have access to a wireless Internet connection. After loading the 2006.1 LiveCD, I noticed it does not have the ipw3945 module available for my wireless card. Is there a way to transfer the module over on a flash drive, or do I have to wait for the next release of the LiveCD, whenever that will be?

Thank you for any help.

---

### Post by cyberdork33 on 2007-04-05
Unfortunately, Gentoo is not likely to give much attention to supporting WiFi on the LiveCD. Trust me I have tried :(

You could try putting the module on a stick. As long as it is compatible with the kernel. You can also install gentoo from "other" LiveCDs (one that might support wifi) pretty much the same way you do it normally. There was instructions on their site somewhere.

---

### Post by igknighted on 2007-04-06
> **cyberdork33 said:**
> Unfortunately, Gentoo is not likely to give much attention to supporting WiFi on the LiveCD. Trust me I have tried :(

You could try putting the module on a stick. As long as it is compatible with the kernel. You can also install gentoo from "other" LiveCDs (one that might support wifi) pretty much the same way you do it normally. There was instructions on their site somewhere.

Why not just get the source and compile it?  I think there is a way to download all the sources you need and then have portage compile them.  If you are using the Live CD, you could do a group install then compile the source for your wireless support and go from there.  Honestly I think the very best way would be to find somewhere to plug in, thats probably your best bet.

---

### Post by VinzClortho on 2007-04-15
Another option is to do an alternate install using Knoppix. Knoppix's support of wireless is pretty good.

---

