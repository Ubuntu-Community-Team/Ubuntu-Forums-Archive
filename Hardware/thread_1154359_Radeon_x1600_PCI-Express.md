---
title: "Radeon x1600 PCI-Express"
date: 2009-05-09
forum: Hardware
---

### Post by FinAkechi on 2009-05-09
I cant run the Catalyst Control Center because it say no Ati driver is installed. When I go to ***System->Administration->Hardware Drivers*** it only shows my  Wifi Card. I typed

     [B][I] lspci 
[/I][/B]
in the Terminal to see if the PC even recognized it and it did.

[B][I]01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
 [/I][/B]
was the output.

---

### Post by FinAkechi on 2009-05-09
bump

---

### Post by Insane1 on 2009-05-10
I don't believe you can use the control center with the open source drivers installed by default. And to my knowledge, all pre x1900 cards have been discontinued by ATI, and are not supported by the Catalyst 9.4 drivers (the only proprietary drivers compatible with the Xorg version shipped with Ubuntu).

So we're both stuck in the same boat for right now...I have heard Rumors that because of the move ATI may release the 3D components of pre 9.3 catalyst drivers for the open source drivers...but I only heard that once. If you want working FGLRX drivers...you'll need an older distribution (or SimplyMepis, as it uses an older Xorg and fglrx which are still compatible).

---

