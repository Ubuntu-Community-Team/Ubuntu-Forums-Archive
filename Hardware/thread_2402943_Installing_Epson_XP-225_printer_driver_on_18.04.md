---
title: "Installing Epson XP-225 printer driver on 18.04"
date: 2018-10-05
forum: Hardware
---

### Post by Panawe on 2018-10-05
I have installed Ubuntu 18.04 on a friend's computer. Seems okay so far but his printer (Epson XP-225) doesn't run correctly - when I try to print out a test page I get gobbledeggok, although the printer page says that "Epson XP-225 series" is loaded. I think it says somewhere that a generic driver is loaded.

Could someone give me some advice on how to sort this out?

As ever TIA

---

### Post by Panawe on 2018-10-12
Don't know if anyone is following this but I seem to have sorted it.

1) In Terminal:

$ sudo apt-get install lsb

2) I downloaded and installed via Software Installer:

epson-inkjet-printer-escpr_1.6.30-1lsb3.2_amd64.deb

3) In the same way I installed a "printer utilities" package though I'm not sure how much use this is.

4) Went into Activities > Printers and added the newly displayed Epson XP-225 printer and deleted the generic driver.

5) Printed a test page correctly.

---

