---
title: "Conexant laptop modem"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Bulltitan on 2007-04-27
Hi my system specs are :
Compaq Presario 1700
PIII 600, 192Mb, 40Gb, sound allegro ess pci, ati Rage M1 and the subject of this post the modem.
After running the scanmodem script this was the output:

PCIDEV=14f1:2013
CLASS="Class 0780: 14f1:2013"
NAME="Communication controller: Conexant HSF 56k Data/Fax Modem "
Vendor=14f1
Device=2013
SUBSYS=0e11:b195
SUBNAME=" Compaq Computer Corporation Bear"
SUBven=0e11
IRQ=9
Test="./scanModem test 14f1:2013 0e11:b195"
IDENT=hsfmodem
TST=

Now, the system has detected something or that's what i think after taking a look at the restricted
drivers manager utility, it has in the list a lucent agere linmodem which is marked in the check box but its not in use.
Just to see what happens i opened the network manager and try to have the modem detected but
nothing  was detected. I've read some instructions in this forum on how to have it installed but
i've also seen the process in linuxant website wich is different from the thinks posted here, so
my question is what should i do, follow the linuxant instructions or the ones here and why is that
lucent agere detected in restricted drivers manager what is it for?.

thanks in advance

---

### Post by Matchless on 2007-04-28
Your test shows that it is a Conexant modem and vendor id 14f1confirms it. If you are running any Edgy or Feisty version only the Linuxant drivers will work, but you will be limited to 14400 and will need to register and pay a fee to get a  key code to open up the driver to full 56k. Older kernel versions from Dapper and back can use the old open source drivers. I suggest downloading the linuxant driver which is free and use it to test your modem. Once you know that it works, then you can decide on purchasing a keycode from them or not.

---

