---
title: "how to set firewall options"
date: 2008-08-06
forum: General Help
---

### Post by Pacopag on 2008-08-06
Hi.  I'm trying to run Maple on Ubuntu 8.  It starts up fine, but everytime I try to execute a command, it says that it is waiting to connect to the Maple Kernel, then it times out.  It says that it is often a firewall that prevents connection to the Maple Kernel.

Does anyone know how to configure the firewall to let Maple do what it wants?  I find this whole firewall business strange because, as I understand it, a firewall is an internet security thing, but Maple is installed on my computer and shouldn't even need internet connection to work...or am I just not understanding the whole idea of a firewall.

---

### Post by Nepherte on 2008-08-06
Maple requires a connection to the maple servers to finish the registration/verification process. It's strange though, because by default the firewall allows outgoing connections. Maybe you should verify this is actually the case (A GUI for the firewall is probably the easiest way to do so, 'firestarter' for example).

---

### Post by Pacopag on 2008-08-06
Ok.  I installed firestarter, but I have no idea how to use it to let maple do its thing.

---

### Post by Nepherte on 2008-08-06
Under policy, outgoing make sure that outbound connections are allowed. You could also let firestarter on and see if you get a blocked connection when you try to run it.

---

### Post by Pacopag on 2008-08-06
It is set to "Permissive by defaule, blacklist traffic"
I also tried just shutting the firewall off completely, but it still doesn't work.

---

### Post by Nepherte on 2008-08-06
I'm afraid I can only direct you to Maplesoft itself then: [http://www.maplesoft.com/](http://www.maplesoft.com/)

---

### Post by Pacopag on 2008-08-06
Ok thanks.

---

