---
title: "Atheros AR5007EG / Acer Aspire One wifi"
date: 2008-12-27
forum: Hardware
---

### Post by earnestsoul on 2008-12-27
I have aacer aspire with AMD 64 turion X2 processor 2GB. i hav problem with wireless caard.I succesfully installed driver for my atheros ar5007eg , everytime i start my laptop i need to give "modprobe ath_pci" command to maake my caaaard word. i am tired with it .how could i avoid it . aaand the key ring allways asks paassword aand annoys me how to stop that? pleaaase answer.

---

### Post by teaker1s on 2008-12-30
In order to have the wireless work after reboot, add the following line to /etc/modules ("sudo gedit /etc/modules") to automatically load the module when booting:

ath_pci

You should now have working wireless. However you may want to do the following to prevent problems (the symbol mismatch) when the module is loaded:

Add ath_hal to the DISABLED_MODULES= stanza in /etc/default/linux-restricted-modules-common

(i.e. 'DISABLED_MODULES="ath_hal"')

[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

---

