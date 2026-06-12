---
title: "IBM T60 Ethernet Card Not Detected"
date: 2006-05-25
forum: Hardware &amp; Laptops
---

### Post by b_chris on 2006-05-25
Just installed Ubuntu onto my T60p and am bit frustrated, for some reason the ethernet card is not being detected, and I cannot work out why.

pppoeconf does not help and neither does modconf.

Anyone have any ideas??

Description		Integrated Intel PRO/1000 Gigabit Ethernet
Interface	         Gigabit Ethernet- Integrated

Regards.](*,)

---

### Post by b_chris on 2006-05-25
Tried modprobe e1000 and nothing......](*,)

---

### Post by agurk on 2006-05-26
I never tried Breezy, but I can say it works fine on Dapper. Perhaps wait a week for Dapper, or install the release candidate? ([http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/))

---

### Post by b_chris on 2006-06-01
Gold!!

---

### Post by arinto on 2006-09-26
By the way, so what's is the solution? My T60's ethernet card still not work :S Ubuntu 6.06 able to detect it, but it doesn't work properly, cannot get any DHCP OFFER

arinto

---

### Post by Ken Nishimura on 2007-10-05
[http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid](http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid)

This seems to be a perfect description of the problem. There are some solutions
that you might want to use. 

-- 
Ken

---

