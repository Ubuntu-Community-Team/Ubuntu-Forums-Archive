---
title: "How to install a modem driver?"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by Bashar on 2005-03-05
Hi
I've installed Ubuntu on a Targa laptop but the SmartLink modem did'nt work.
I have it's driver but was not able to install it.  The make command kept giving me an "Error: 2" and I don't know what that is.  Can someone guide me to the proper way to do the driver installation.  Thanks for your time

---

### Post by az on 2005-03-05
You need to install build-essential and linux-headers-2.6.8.1-3-386 (or whatever version matches your kernel - run uname -a to get your kernel version)

Then extract the driver's source
tar xvzf sl-modem-source*

go into that directory 
cd sl-modem-source*

and run 

debian/rules binary.


Then 
cd ..
dpkg -i sl-modem-modules*.deb

Good luck.

---

### Post by p!=f on 2005-03-05
... or use more comfortable module-assistant to create the package.
```

sudo apt-get install module-assistant
sudo module-assistant

```

---

