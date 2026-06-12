---
title: "Canon LBP3000 and Gutsy - working method?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by dryder on 2007-10-26
I've read many posts on the net about how to get the Canon LBP2900 / LBP300 printer working.

Based on [_[COLOR="Blue"]**this article**[/COLOR]_]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900") and (again) a [[COLOR="Blue"]**_French Forum here_**[/COLOR]]("http://72.14.203.104/translate_c?hl=en&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1256378&prev=/search%3Fq%3Dubuntu%2Bgutsy%2Blbp3000%2BOR%2Blbp3000%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DQ3s%26sa%3DX%26as_qdr%3Dallhttp://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1259036viewtopic.php?pid=1256378"), there may be a way to get these printers to work.

You also need to refer to [**_[COLOR="Blue"]this wiki page[/COLOR]_**]("https://help.ubuntu.com/community/AppArmor")

I have NOT tried this (I have not installed Gutsy) but post this for those who, like me, have these good Canon printers and want them to work in Gutsy.

Good luck!

David

---

### Post by silvanus2005 on 2007-10-29
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900). Instead foolowing the first step described there, I downloaded deb drivers from Canon Ausralia:
[www.canon.co.au](www.canon.co.au). When I tried to install the drivers, i had a problem with a missing library: libcupsys2-gnutls10. I found that missing library at:
packages.ubuntu.com. After I installed the missing library and the drivers provided by Canon, I rebooted my laptop and I followed the steps beginning with step 2. My Canon LBP 3000 is working smoothly under Gutsy.

---

### Post by dryder on 2007-10-29
Thanks for sharinr! :-) 

Are you saying the Feisty method worked for you in Gutsy?

[IMG]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]

David

---

