---
title: "Can't install ATI fglrx on 12.04 &amp; 11.10 on dell 3350 with radeon hd6470m"
date: 2012-05-27
forum: Hardware
---

### Post by ciesla.tomasz on 2012-05-27
hi,
I've tried almost everything:
-automatic driver installation via additional drivers,
-installation from amd: amd-driver-installer-12-4-x86.x86_64.run (and almost all older versions from 10)
-manual installation: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)
Ubuntu 11.10 and 12.04 both 32 and 64-bit


i'm always getting an error:
Uninstalling any previously installed drivers.
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.961 to DKMS
[Reboot] Kernel Module : update-initramfs
 

It's crucial to install the ati driver on hybrid graphic cards  laptops - without it you can't switch to standard intel HD3000 graphic  card to lower power consumption, heat generation and fan noise...
 Only way to switch off raden hd6470m is to modify /etc/modprobe.d/blacklist.conf  with "blacklist radeon" but it will still work after starting up the  system - you have to start-up computer, then suspend it and the turn it  on to work only on intel HD3000
Any ideas what can be wrong?

---

