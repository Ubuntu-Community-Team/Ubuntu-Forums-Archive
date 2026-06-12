---
title: "Wireless USB Adapter"
date: 2009-03-24
forum: Hardware
---

### Post by EyJus on 2009-03-24
Hello,
I'm new here and I want some help with my Tenda W302U 11N Wireless USB Adapter. It works perfectly (It's Tested on Windows) but in Kubuntu (I've tried it on the Live CD) It just doesn't work. I can't see it in plugged devices list but the little blue light is on so... Kubuntu just can't reconize it (right?). On a Internet Site I saw that "Supports Windows XP, 2000, ME, 98SE, Vista, Linux, MAC operating systems ". Anyone has that thing? Anyone can help? Thank you! And BEWARE... I'm a complete linux newbie :D !

---

### Post by Fluffmatic on 2009-03-24
You may want to look at ndiswrapper, and simply use the Windows drivers for it, its available from the software repositories and very simple to use

---

### Post by EyJus on 2009-03-24
> **Fluffmatic said:**
> You may want to look at ndiswrapper, and simply use the Windows drivers for it, its available from the software repositories and very simple to use

Thank you! I'll try it right away!

---

### Post by EyJus on 2009-04-16
OK, since I have no internet on Kubuntu I downloaded the ndiswraper and got it on USB device. There is a little problem. I don't know how to install it and what exactly to do after... can you help me a bit with that? Thanks in advance! :)

---

### Post by Big_Croc7 on 2009-04-18
It is possible to install it from that (probably - have you downloaded the package file or the source? Either will work, just say which so someone can point you to the right instructions. If it's a .deb file you have, it's the package, and you should just be able to click on it and install), but the easiest, if you have access to a wired network, will be to plug in temporarily and install ndiswrapper from the repositories over the cable.

Which version of Ubuntu are you using? I read on a review site that this adapter works properly with Intrepid, so if you're using an older version you might want to try upgrading and see if that makes it work automatically.

---

### Post by EyJus on 2009-04-19
> **Big_Croc7 said:**
> It is possible to install it from that (probably - have you downloaded the package file or the source? Either will work, just say which so someone can point you to the right instructions. If it's a .deb file you have, it's the package, and you should just be able to click on it and install), but the easiest, if you have access to a wired network, will be to plug in temporarily and install ndiswrapper from the repositories over the cable.

Which version of Ubuntu are you using? I read on a review site that this adapter works properly with Intrepid, so if you're using an older version you might want to try upgrading and see if that makes it work automatically.

Thanks for the answer. The package is .tgz .My Kubuntu is 8.10 and it doesn't even recognize my network adapter as a device.

---

