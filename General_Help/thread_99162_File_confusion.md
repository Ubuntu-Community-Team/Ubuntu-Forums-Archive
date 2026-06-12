---
title: "File confusion"
date: 2005-12-05
forum: General Help
---

### Post by Lydia on 2005-12-05
Hi,

I'm trying to set up Ubuntu since three weeks now, but it doesn't work. So I try to build a new Kernel - Version 2.6.14 - got it running but with some errors.

To fix them I need some infos about the Ubuntu File structure as its a little confusing...

Searching google always brings up files like /etc/modules.conf or modprobe.conf but they don't exist with ubuntu. Right now I guess that modules.conf is modules in Ubuntu - but that doesnt really match.

Kernel-info gives something like eg: 
"To compile this driver as a module, choose M here: the module will be called microcode.
If you use modprobe or kmod you may also want to add the line
'alias char-major-10-184 microcode' to your /etc/modules.conf file."

Well but such lines don't exist in the modules file.

But found them in /etc/modprobe.d/aliases

Taking this example - is it 

micocode in /etc/modules
and
alias char-major-10-184 microcode in /etc/modprobe.d/aliases ?

Can anyone help me with these files? I just don't find info about how modules / modprobe is working in Ubuntu. Maybe then I can fix the errors and get a working system.

greez
Lydia

---

### Post by timfrost on 2005-12-05
In my system (breezy), I have in /etc/modprobe.d/aliases:
alias char-major-10-184 microcode


So my guess is that the answers are yes and yes.

---

### Post by kairu0 on 2005-12-05
A module is basically a hot-pluggable driver for Linux. They can be added and removed dynamically without rebooting. That is why we modprobe exists: to initiate them after you've already booted up.

modules.conf is /etc/modules in Ubuntu

the aliases are saved in /etc/modprobe.d/aliases

When asked if you want to install in the kernel or as a module, it is best to choose module (usually) just in case you upgrade the hardware, connect it spontaneously, or need to troubleshoot.

---

### Post by Lydia on 2005-12-05
ok thx

and how can I find out which modules are loaded on startup? Because watching lsmod gives much more loaded modules than are written in my modules file. 
And booting with the self-build kernel brings up depmod erros with no file name given and inmod errors with not found x.ko files. Unfortuantly those erros don't appear in any of my logfile, even turning on bootlog gives no more information.

[QUOTE=timfrost]In my system (breezy), I have in /etc/modprobe.d/aliases:
alias char-major-10-184 microcode


So my guess is that the answers are yes and yes.[/QUOTE]

---

### Post by Lydia on 2005-12-05
ok, but the drivers for build-in sound and graphics should be in the kernel or am I wrong? 

[QUOTE=kairu0]A module is basically a hot-pluggable driver for Linux. They can be added and removed dynamically without rebooting. That is why we modprobe exists: to initiate them after you've already booted up.

modules.conf is /etc/modules in Ubuntu

the aliases are saved in /etc/modprobe.d/aliases

When asked if you want to install in the kernel or as a module, it is best to choose module (usually) just in case you upgrade the hardware, connect it spontaneously, or need to troubleshoot.[/QUOTE]

---

