---
title: "Slmodemd, snd_intel8x0m and suspend"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by damdim on 2007-08-18
Hi,

I have a problem with the internal modem of my laptop. I 've made it work with slmodemd and the snd_intel8x0m module. The problem is that when I resume from suspend it doesn't work. I 've tried to restart the sl-modem-daemon and I 've ran multiple versions of slmodemd, with no success. The modem runs only when I reboot.
The only way to make it work without reboot is the following.
1. I change with CTRL+ALT+F1 to CLI
2. I kill xorg with "sudo killall kdm"
3. I stop the daemon with "sudo /etc/init.d/sl-modem-daemon stop"
4. I unload the module with" sudo rmmod -f snd_intel8x0m"
When I restart xorg everything works fine.
The reason I have to kill xorg is that if I try to unload the module without doing it, the module is in use and it doesn't unload even with the -f parameter. I read somewhere that the kernel has a "Force unload module" option so I guess that it's not selected in precompiled kernels for Ubuntu.
Is the only solution to try a compile a kernel with this option on so that I could unload and reload the module from within xorg. Then maybe the section modules /etc/default/acpi-support would work, because in my case it doesn't...

---

### Post by Wartender on 2008-06-20
hi, listen, i have a laptop and i need the snd_intel8x0m module for the connection to work, but when i search for it in the packages website it doesn't return any results, can anybody give me a link to download it please? i really need it!!
thanks

---

