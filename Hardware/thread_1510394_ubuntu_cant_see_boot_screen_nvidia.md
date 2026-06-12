---
title: "ubuntu cant see boot screen nvidia"
date: 2010-06-15
forum: Hardware
---

### Post by xenosaga456 on 2010-06-15
wo ehen ever i boot up i cant see anything on screen untill i get to the login screen......i cant use recoverymode ither cuz i cant see the screen??? it just goes blong whenever i ctrl+alt+f4 i cant see nothing??? i cant login in as terminal ither its just a blank screen unless the xserver is running??

---

### Post by dabl on 2010-06-15
u NEed tuh rEMoVe "QUieT" fRUm thE keRNL buTe lINE oN thUH buTE mENu sO U cAN sEE tHuh bUte meSSagES

---

### Post by owise1 on 2010-06-15
I have a similar issue - I did a clean install of 10.04 from a live USB and while to initial boot from the USB showed the normal Ubuntu splash screen with the progress dots under the symbol the next boot and subsequent boots from the hard have a black screen until the gnome desktop comes up.  I assume an issue with grub2?

Dave

---

### Post by dabl on 2010-06-16
I don't think it's a Grub2 issue.  *buntu now uses "Plymouth" for the initial boot screen, following the boot menu.  I don't know lots about Plymouth -- it's a little touchy on my Kubuntu system.  If you delete the "quiet" option on the kernel boot line in the boot menu, then you should be able to view the messages as it boots.

---

### Post by xenosaga456 on 2010-06-17
well could u tell me how to deleat that properaly?

---

### Post by aosmith on 2010-06-17
Whats your chipset?  Try turning off integrated graphics in the bios if you've got 2 cards.

---

### Post by VastOne on 2010-06-17
> **dabl said:**
> u NEed tuh rEMoVe "QUieT" fRUm thE keRNL buTe lINE oN thUH buTE mENu sO U cAN sEE tHuh bUte meSSagES

I cannot stop laughing...., you have done it dabl, you have cut me down to a blubbering mass.
:lolflag:

---

### Post by xenosaga456 on 2010-06-25
i cant do that in my bios cuz i do hav a nvidia chipset vut it is made by hp

---

