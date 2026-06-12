---
title: "kernel upgrade"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by alimahmoudy on 2009-02-25
Hello, I'm currently using kernel version 2.6.24-23, everything is working fine, but i figured if i upgraded my kernel it would be better, especially for my atheros wlan usb (driver is zd1211rw) which currently doesn't show the connection strength correctly and i seem to suffer from very low transfer rate.
So i upgraded to kernel version 2.6.28.7 using "KernelCheck", and installed everything correctly. But both my sound card (realtek) and usb wlan device stopped working. Any help ? thanks in advance. 

P.S: after the installation of the new kernel, in my boot screen i got a new kernel called 2.6.24-23-rt. What is that ?

---

### Post by cariboo on 2009-02-25
Why not just install the kernels that are available in the repositories, instead of building a kernel.

You have built a real time kernel, and unless you are running Ubuntu Studio you don't really need it.

Go to System--.Administratiion-->Synaptic Package Manager and search for **linux-image-generic**

Jim

---

### Post by surj08 on 2009-02-25
Wouldnt apt-get work also? just wondering

---

### Post by alimahmoudy on 2009-02-25
Thanks for your reply. Well I'm using ubuntu hardy heron 8.04, and yesterday i downloaded and installed all the ubuntu studio applications via sudo apt-get install ubuntustudio*. 
So i guess i need it right ?
the thing i can't understand is why won't my drivers be installed ? even though it's the newest kernel version ?

---

