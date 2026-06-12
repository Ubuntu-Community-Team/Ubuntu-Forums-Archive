---
title: "HP 2575 all-in-one network install pb"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by jmeuf on 2007-01-16
Hi,

My PC is loaded with Ubuntu 6.06 (but I will soon upgrade to 6.10). I use a WiFi router Netgear VGR614v6. My printer HP Photosmart 2575 (all-in-one) is wired connected to the router. Everything works well when I run Windows XP instead (using SAMBA): got access from my wifi ubuntu remote PC.

When I select 'Network printer' in the wizard, the printer is not detected.
Then, if I select CUPS and input the uri previously got from hp-makeuri (which returns:
"hp:/net/Photosmart_2570_series?ip=192.168.1.2" - 192.168.1.2 is effectively the address of the printer, confirmed by the router).
After copying this in the ipp field, I get:
ipp://hp:/net/Photosmart_2570_series?ip=192.168.1.2

My printer remains desperately silent ...

hplip, the recommended driver, is installed (checked in Synaptic).

Which setup should I select best: CUPS, Windows, Unix, JetDirect? and how to initialize?

Thanks.

---

### Post by andreas64 on 2007-01-17
Hi,

the hplip-drivers included in Dapper are very outdatet. For example, you can't do a 'hplip setup' wich is necessary for full functionality.

If possible, install the newest driver from hplip.sourceforge.net. There is an Ubuntu-Install-Guide too.

Another possibility is to install Edgy, which comes with newer drivers.

Andreas

---

### Post by jmeuf on 2007-01-23
Ok. In any case I had the intention to install Edgy (I just need to start with the Dapper because Edgy won't install directly due to my ATI card, I assume).

Thanks.

---

### Post by susu on 2007-02-19
Cool!  I thought I was the only one stuck with the same printer!  I have Edgy installed but my printer was not detected either even with hplip installed.  I checked Synaptic again and found that the hpoj driver was available for the printer we use.  After that was installed the printer was detected and installed just fine.

---

### Post by 11hjpphty76lkjj on 2007-02-23
We do not recommend using HPOJ at all.  The latest version of HPLIP supports the Photosmart 2575.  HPOJ is very old and outdated, and does not include any of the hplip tools and printer functionality.  

Just for future reference. :)

---

