---
title: "Mythtv &amp; Capture Card problems"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by rflook on 2007-04-29
Just installed Ubuntu to get away from my knoppmyth system and so far i really like the system. Unfortunately i have hit a brick wall fairly quickly. One of the key reasons for me using a linux system was to be able to run mythtv. So i followed the instructions from [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) and went on my merry way. Things went wrong when i got the to .... phase.

I would go into the 'Capture Cards' section of the setup and my card (Leadtek Winfast DTV1000T) seemed to have been probed without difficulty as it was immediately listed. However no matter how many times i tried to select my card every time i went to 'Finish' from the capture cards section of the setup my card would not be listed. For some reason the setup seems to be rejecting my selection.  

Id be very grateful if someone could help me with my problem as if i get really stuck ill be forced to either try MythDora or go back to Knoppmyth :-(

---

### Post by rflook on 2007-04-29
Some good news, some bad. I managed to get mythtv-setup to recognise my card, hurrah. Well sort of. Unfortunately because i have a Sky cable box i need to pipe my TV through the composite input in the capture card. Unfortunately mythtv only has an option for DVB, not for SVideo or composite in. Does anyone know of a way around this problem? Id be very grateful for any help that can be offered.

---

### Post by superm1 on 2007-04-30
Are you sure you chose the correct card type during mythtv-setup?  These inputs will be exposed immediately when the right card type is chosen.  They are populated from the standard video4linux2 interface provided with the kernel modules.  (In other words, you will see the same problem in mythdora/knoppmyth if this is caused by chosing the wrong card type)

---

### Post by devehf on 2008-01-06
I think you just need to hit ESC after you are done setting up your capture card so you can go back to the main menu and then go on to "video sources".

---

