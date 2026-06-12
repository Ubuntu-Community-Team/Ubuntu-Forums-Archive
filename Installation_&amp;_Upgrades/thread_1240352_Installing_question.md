---
title: "Installing question"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by Merrib64 on 2009-08-14
As per a previous thread I am trying to install Ubuntu on a 2 HD system. The second drive is split into D: and E: drives. I will be using drive D: which is formatted as a NTFS drive. The question that I have is: When I select to install Ubuntu on drive d: I am presented with the question as to how to format the hard drive from a drop down file, which do I select so that Ubuntu will be totally installed on drive D: which is roughly 40GB in size and will be used only for Ubuntu. I don't want to format the drive incorrectly.

Bob

---

### Post by AmerNewbieInDE on 2009-08-14
ok, since you are familiar with windows, c. being your main,  d: and e: being your slave, delete partition d:(making sure all date you want is off it first)

reboot with your linux cd/dvd. and select the unpartitioned area. allow linux to partition it itself. you will need to install the bootloader on the first drive which will give you a boot option everythime you start the pc

---

### Post by oldos2er on 2009-08-14
If you're asking which filesystem to use on D:, I'd choose ext3.

---

