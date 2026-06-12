---
title: "Quagga"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by 2008abcdabcd on 2009-02-20
I am new to Ubuntu.

Does anyone know how to install Quagga?

I have tried many times, but it always told me there were some errors existed.

Thank you.

---

### Post by taurus on 2009-02-20
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install quagga
```

---

### Post by 2008abcdabcd on 2009-02-21
-desktop:/etc/quagga$ sudo /etc/init.d/quagga start
Loading capability module if not yet done.
Starting Quagga daemons (prio:10): zebra (not started without config file) bgpd ripd (not started without config file) ripngd (not started without config file) ospfd (not started without config file) ospf6d (not started without config file) isisd (not started without config file).


Q: Where can I find these config files? Thank you.

---

### Post by d_sotos on 2009-03-25
I have exactly the same problem. After installing quagga 0.99.9-6 with apt-get in Ubuntu 8.10, it keeps giving me this: 
```
Starting Quagga daemons (prio:10): zebra (not started without config file)
``` everytime I try to start quagga.
I am inclined to believe that this is a version specific problem, as quagga runs smoothly on Ubuntu 8.04. Has anyone here come up with a solution? Has anyone installed successfully a version of quagga outside apt-get?

---

