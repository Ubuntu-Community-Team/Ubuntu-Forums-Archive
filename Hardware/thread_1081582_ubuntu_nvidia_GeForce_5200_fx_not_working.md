---
title: "ubuntu nvidia GeForce 5200 fx not working"
date: 2009-02-26
forum: Hardware
---

### Post by JavaJax on 2009-02-26
i have installed the drivers from the hardware driver windows.
version 173
version 96

and have installed
version 71
version 96
version 173
version 177
version 180
with apt-get install in recover mode as root
and removing each package before installing the next.

every time i install a driver on reboot ubuntu startup screen loads but no login screen it just turns black and stays black i have to go into recovery mode and reset the xserver.

last thing i did was in recover mode go to root and connect to the internet :using idconfig eth0 up then :dhclienteth0.
then sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
the program ran and it could not download or build the kernel.

any ideas on which is the right driver and how to install it

---

### Post by meznaric on 2009-03-03
Well if none of these drivers work then you should probably try the nv driver. It will not provide any 3D acceleration, unfortunately, so you will not be able to use Compiz or any complex OpenGL applications (well technically they should work but will probably be quite slow). Other than that it works fine for everything else.

---

### Post by JavaJax on 2009-03-16
i thought i did install the nv diver by downloading the driver from the nvidia site and installing it from root
if this is wronge how do i install the nv driver any instructions?

---

### Post by JavaJax on 2009-03-17
i am having no luck with [www.driverguide.com](www.driverguide.com)
i have downloaded 3 diffrent drivers and the all say they cannot find a pre compiled kernel and cannnot compile one
what kernel would the driver be talking about and how do i find out wich one i have

---

