---
title: "Module options and dependencies"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by nvn on 2005-06-15
Hi to all

I've been looking everywhere, but still haven't found a clear answer to this:

I have an irda-usb apdator/hub. It uses the module 'stir4200', which loads automatically when I insert the adaptor in the usb port.

The problem is that I have to manually load another module and execute a command to be able to transfer files through infrarred to my cell phone. The commands I execute are:

modprobe ircomm
irattach irda0 -s

So, the question is: how can I have the extra module (ircomm) loaded and the 'irattach' command executed when the fisrt module (stir4200) is loaded (ie, when I connect the adaptor)

Thanks in advance for your answers
nvn

---

### Post by nvn on 2005-06-15
[QUOTE=nvn]Hi to all

I've been looking everywhere, but still haven't found a clear answer to this:

I have an irda-usb apdator/hub. It uses the module 'stir4200', which loads automatically when I insert the adaptor in the usb port.

The problem is that I have to manually load another module and execute a command to be able to transfer files through infrarred to my cell phone. The commands I execute are:

modprobe ircomm
irattach irda0 -s

So, the question is: how can I have the extra module (ircomm) loaded and the 'irattach' command executed when the fisrt module (stir4200) is loaded (ie, when I connect the adaptor)

Thanks in advance for your answers
nvn[/QUOTE]

Ok I finally figured it out. I'm leaving the solution here so it can help anybody else having the same problem.

Short story:

- The files actually parsed by modprobe are the ones in /etc/modprobe.d/
- Read the manpages for modprobe.conf, as it shows the commands you can use

- Finally, what I did was add this line to /etc/modprobe.d/irda-utils:

install stir4200 /sbin/modprobe ircomm; /sbin/modprobe  --ignore-install stir4200; /usr/sbin/irattach irda0 -s

Greetings
nvn

---

