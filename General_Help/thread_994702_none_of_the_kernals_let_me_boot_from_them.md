---
title: "none of the kernals let me boot from them"
date: 2008-11-27
forum: General Help
---

### Post by antec-kev on 2008-11-27
like said above none of them work when i boot from them... ubuntu on my machine i can "sometimes" get to the login screen for username and pw but moslty i cant... when i can i type both in hit enter and it like doesnt ever load the desktop... i have tried burning another live cd with no luck tryn to reinstall it... it wont let me start fresh on install... i boot from md and it goes to the kernals... suggestions?

---

### Post by alwayshere on 2008-11-27
start in safe mode go to sessions and make sure pulse audio manager is there and ticked.

i had same problem when i unticked pulseaudio

---

### Post by doas777 on 2008-11-27
have you configured your bios to attempt to boot from CD before it boots from the HDD?
check your boot order if not. just move the CD rom to the first boot device.

are you able to boot in [recovery mode]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html") (look at item 8.1)? 

otherwise, I would look for a hardware problem. since you said kernel(s) I assume that the computer worked fine until recently, right? did anything change?

---

