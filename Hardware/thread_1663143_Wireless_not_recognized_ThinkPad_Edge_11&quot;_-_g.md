---
title: "Wireless not recognized ThinkPad Edge 11&quot; - generic-pae Kernel"
date: 2011-01-09
forum: Hardware
---

### Post by ideamaestro on 2011-01-09
Hi all,

After solving the microphone problem [http://ubuntuforums.org/showthread.php?t=1662818](http://ubuntuforums.org/showthread.php?t=1662818), I have again the wireless problem with the:

uname -a 
--> 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux

I have the rtl8192CE driver, untarred it with "tar xvfz rtl8192ce_linux_2.6.0005.1116.2010.tar.gz"  
 
"make" command doesn't work with "sudo -s" or "su" (root)

Output of "make" as root:

root@********:~/Drivers/Wireless_LAN/rtl8192ce_linux_2.6.0005.1116.2010# make
make[1]: Entering directory `/lib/modules/2.6.32-27-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-27-generic-pae/build'
make: *** [all] Error 2

lspci:
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

please help.

---

### Post by ideamaestro on 2011-01-09
Problem solved by uninstalling pae kernel to the latest generic kerne 2.6.36.29.generic

Mic, speakers, wireless, ALL of it, everything works.

---

