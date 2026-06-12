---
title: "wireless problem with old gateway 450sx4"
date: 2011-01-08
forum: Hardware
---

### Post by efone on 2011-01-08
Hi guys, 

I installed xubuntu on an old gateway 450sx4 and after a couple of glitches it seems to be running fine. The only problem is the wireless card (Lucent WaveLAN). With the orinoco drivers it scans the network; however, it wont connect or it would connect only for few seconds.

The command "hwinfo --netcard" suggests 2 drivers: orinoco_cs and hostap_cs. I figured I would try hostap_cs; unfortunatel, when I modprobe it I get:

FATAL: Error inserting hostap_cs (/lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko): Invalid argument

I have been googling for few days now and tried different fixes to no avail. Any help in getting the wireless card working or debugging the problem is very appreciated.

Thanks,

Efone

---

### Post by efone on 2011-01-08
Another piece of information; I tried ndiswrapper and ndisgtk displays:

"Hardwarepresent: no" 

when I load WLLUC48.INF.

---

### Post by efone on 2011-01-08
Could the problem be in the kernel? I read something about ipv6, but I am not sure how to change the setting...

---

### Post by efone on 2011-01-09
I am trying to recompile the kernel now, but I get the following message when I run "make":

  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2

---

### Post by efone on 2011-01-17
I ended up installing gentoo with xfce4. MADWIFI is working fine with the modules built in the kernel (using it right now). It also solved a previous problem I had: when I did "shutdown" the system it would always reboot unless I disabled LAN in the BIOS.

---

