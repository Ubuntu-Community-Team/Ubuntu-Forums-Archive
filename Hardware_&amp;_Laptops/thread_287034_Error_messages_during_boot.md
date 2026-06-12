---
title: "Error messages during boot"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by italian_boy on 2006-10-28
Hello,
I've upgraded my system to Edgy AMD64 and, thanks to the usplash bug in 
the 64 bit version, I disabled usplash and noticed these strange error 
messages right after the booting of the kernel:

a few lines like this one:

	PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0

then it hangs a few seconds and says:

	hda_intel: azx_get_response timeout, switching to single_cmd mode...

after that, the system boots up normally

I suspect the second error message is related to the sound card because 
I remember alsamixer service had problems during shutdown in Dapper, 
even if sound always works.

Does someone know what do these messages mean?
Thanks in advance for your help,
Alessandro

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

### Post by Healey on 2007-01-27
Hi

Did you resolve this problem as I have a similar problem ?????

I have a Compaq Presario C310EA using dapper but I had the same problem with Edgy

I also have the LATEST BIOS from the HP Compaq site

Regards

healey

---

