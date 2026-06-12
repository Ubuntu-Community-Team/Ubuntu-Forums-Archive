---
title: "root password not accepted?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Tholley on 2009-07-15
This computer is connected to a network printer via wireless network, connected to a router at the main computer. the last time i printed anything was 2 weeks ago and all worked fine.

today it says my printer may not be connected, but it is, and will print from the other computer. So I figured I would try and let it _find_ the printer again which it did, found the drivers, but at the last step, it asks for "Password for root on localhost?". It shows the user name is root and when I type in my normal password for everything else, it says "Not Authorized - the password may be incorrect".

I have tried every imaginable password I have ever used, and even changed the user name to this computer and the other computer, but all the same.

what am I not doing right here?

Help...

---

### Post by lisati on 2009-07-16
The "root" account is switched off by default in Ubuntu, and saying how to enable it is discouraged in the forums.

You might want to look into using the (gk)sudo command in conjunction with whatever you used to install the drivers. For more information, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tholley on 2009-07-16
Ok thanks...

I was able to get the info I needed from your link.

---

