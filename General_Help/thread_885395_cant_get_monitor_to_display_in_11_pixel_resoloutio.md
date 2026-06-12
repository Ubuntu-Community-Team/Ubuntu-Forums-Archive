---
title: "cant get monitor to display in 1:1 pixel resoloution"
date: 2008-08-10
forum: General Help
---

### Post by kitili on 2008-08-10
Hello fellow UFer's

I am having trouble gaetting my monitor to display in 1:1 pixel resoloution, it's fine while in X but durring boot and such, it looks just awfull all streched out. The monitor is a 24" LG flatron wide ( model # L246WP-BN ) with a dvi input. i have attached a picture if it helps. 

Thanks in advance,
Kitili

---

### Post by dexter on 2008-08-10
Try changing the resolution variables in /etc/usplash.conf to your native resolution (1920x1200). This will stop the stretching during startup.

---

### Post by kitili on 2008-08-10
> **dexter said:**
> Try changing the resolution variables in /etc/usplash.conf to your native resolution (1920x1200). This will stop the stretching during startup.

sorry, i dident really mention, but this isant a ubuntu problem persay. I am actualy booting into the arch shell, which is already at a max. but i want to get into true 1:1 mostly for the bios.

---

### Post by cariboo on 2008-08-10
I don't know if this will help, but have a look here:

[http://ubuntuforums.org/showthread.php?t=883192&highlight=terminal+resolution](http://ubuntuforums.org/showthread.php?t=883192&highlight=terminal+resolution)

post #4

Jim

---

