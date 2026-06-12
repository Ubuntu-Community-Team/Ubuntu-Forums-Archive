---
title: "Installing NVIDIA x86-1.0-9746-pkg1.run in Edgy 6.10"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by vrod74 on 2007-02-23
Hi,

I'm fairly new to Ubuntu 6.10 edgy...

i'm trying to install the latest nvidia driver so I can render the graphics in goole earth program. When I try to install using the following command:

sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run

It gives me the following error: 

" You appear to be running an X server; please exit X befor installing".

How do get into this X server  from Edgy?  

Any help is much appreciated.

---

### Post by dekalbave on 2007-02-23
When you boot, GRUB gives you the option for (recovery mode).  Select that when you boot, and you'll be at a command prompt, no X-server running.  Then type in that command, you don't need the 'sudo', and then follow the prompts from the install script.

BTW, before you do this, you might want to check in Synaptic whether or not you have libc6-dev installed, as the nvidia install script will stop if you don't have it installed.

---

### Post by vrod74 on 2007-02-23
Ok thanks, I will try this.

---

