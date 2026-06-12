---
title: "tripple boot using ntldr"
date: 2005-01-11
forum: Installation &amp; Upgrades
---

### Post by srv on 2005-01-11
Hi

My setup:

Samsung 10.2 GB disk hda (Ubuntu)
Seagate 10.2 GB disk hdb (Win98 and XP)

I'm trying to make ubuntu boot using ntldr - I've installed grub in /dev/hda1 that's mounted as /boot

Now - how do I boot my ubuntu so I can make a boot sector file for ntldr to use ?

TIA

/SRV

---

### Post by sas on 2005-01-11
afaik you can't make linux boot using ntldr, you have to have grub/lilo with a choice of linux or windows, with the windows choice leading to ntldr

---

### Post by srv on 2005-01-11
I meant using ntldr to load grub...

But nevermind - I erased my setup and am installing right now...

/Srv

---

