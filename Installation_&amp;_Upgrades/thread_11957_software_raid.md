---
title: "software raid"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2005-01-20
Hi,

I did a fresh Ubuntu install. Accidentilly I didn't do the software raid configuration (I did partition them right). How do I get back to the software raid configuration ? I couldn't find it in base-config. (easier/faster than finding out how to do it manually)

thnx guys

---

### Post by ubuntu_demon on 2005-01-21
[QUOTE=demon666_nl]Hi,

I did a fresh Ubuntu install. Accidentilly I didn't do the software raid configuration (I did partition them right). How do I get back to the software raid configuration ? I couldn't find it in base-config. (easier/faster than finding out how to do it manually)

thnx guys[/QUOTE]
 I did it the manual way :

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

it's easy btw.

---

### Post by Gibbz on 2005-01-21
how do you do it, that was just explainning what raid is, it wont ruin my hardware raid will it?

im guessing i need to setup LVM somehow? ive already got my partitions setup, i just need to format the linux partition to ext3.....

---

### Post by ubuntu_demon on 2005-01-22
[QUOTE=Gibbz]how do you do it, that was just explainning what raid is, it wont ruin my hardware raid will it?

im guessing i need to setup LVM somehow? ive already got my partitions setup, i just need to format the linux partition to ext3.....[/QUOTE]
 When you create a new software raid array all information previously on those harddrives will be lost.

here's explained how to setup your software raid array :
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html)

after this just use mkfs to format the partition (for example to ext3) and then edit your fstab

---

### Post by Gibbz on 2005-01-23
okay id rather not lose all my data :P is there any other way to set it up?

---

### Post by ubuntu_demon on 2005-01-23
[QUOTE=Gibbz]okay id rather not lose all my data :P is there any other way to set it up?[/QUOTE]
 if you set up a new raid array (hardware or software) you always lose all your data on the drives that participate in that raid array (so you have to back up your data first)

---

### Post by Gibbz on 2005-01-23
well i have a hardware raid atm, i though software raid was to get this working under linux?
how do i keep my current hardware raid running and get linux on there?

---

### Post by Gibbz on 2005-01-24
[ftp://www.uli.com.tw/driver/ULi_SATA%20RAID_Linux_%20v0.0p.txt](ftp://www.uli.com.tw/driver/ULi_SATA%20RAID_Linux_%20v0.0p.txt)

found a drive, this is the guide for red hat, how do i get this working on ubuntu?

---

### Post by ubuntu_demon on 2005-01-26
[QUOTE=Gibbz][ftp://www.uli.com.tw/driver/ULi_SATA%20RAID_Linux_%20v0.0p.txt](ftp://www.uli.com.tw/driver/ULi_SATA%20RAID_Linux_%20v0.0p.txt)

found a drive, this is the guide for red hat, how do i get this working on ubuntu?[/QUOTE]
 I don't think there's a way to use a red hat binary driver in ubuntu. You should start a new thread about your hardware raid configuration.

---

