---
title: "Recognizes non-existent hardware..."
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by hajk on 2006-03-16
Gnome network manager (System --> Administration --> Networking) shows a ppp0 dial-up interface on my desktop computer, while there is no dial-up modem attached to it. Luckily, it shows as "not configured", and "not active"...

Now, this interface appeared recently, I think after the recent upgrading of the kernel (k7-smp). Checking through dmesg shows nothing untoward (no pppd stuff) in the boot messages.

Why would the network manager think there is a ppp0? Where does it look?

---

### Post by bscbrit on 2006-03-16
My only guess is that the software is mis-identifying something that is built in to the mobo.  I don't suppose it will cause you any problems though, so you can simply ignore it.

---

