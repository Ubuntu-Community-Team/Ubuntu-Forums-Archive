---
title: "New Printer; Can't Upgrade to HPLIP ver. 3.9.2"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by CamanoAlan on 2009-04-16
I'm trying to install a HP Officejet Pro 8000 printer - a809a on a PC using Ubuntu 8.04. HP says use HPLIP ver. 3.9.2. I currently have HPLIP ver. 2.8.2-Oubuntu8.1. 
This should be simple right? 

1. I downloaded hplip-3.9.2.run to my desktop. 

2. Following HP install instructions I typed: 

cd desktop
sudo sh hplip-3.9.2.run 

3. the reply: 

sh: Can't open hplip-3.9.2.run



Found the problem. I needed to type 'cd Desktop' (that's Desktop with a capital "D")and then it worked.

---

### Post by bartek2 on 2011-02-11
Upgrading hplip is a nightmare, for some reason it has never worked for me. Why don't you try a newer ubuntu, version 10.04 LTS already has hplip 3.10.2. But I was able to set the same printer up only for USB, it doesn't work with wireless connection, or it could work but nobody including me know how to do it.

---

