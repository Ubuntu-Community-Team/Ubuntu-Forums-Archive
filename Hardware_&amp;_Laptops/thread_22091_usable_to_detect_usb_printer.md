---
title: "usable to detect usb printer"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by chz on 2005-03-25
i was able to detect my epson cx-5400 in warty no problem (i just had to use the cx5200 driver). now it doesnt even detect it through the "Add Printer". I checked through device manager, and it seems that i cannot find it through there either. USB does work, because i've tested each port with my thumbdrive. What could be wrong with the printer..?

---

### Post by KLineD on 2005-03-25
Were you able to print when it first detected with the cx5200 driver?

---

### Post by chz on 2005-03-25
yes. just in case theres any confusion...its not working in Hoary, but was working in Warty before the upgrade.

---

### Post by teumima on 2005-03-26
I had issues with my epson stylus c44 plus.

Was detected in warty and not in hoary.

You need to add more drivers, i forgot what u need to apt-get. Sux sorry. Search for it in the forum. It works well now.

You'll have to manually add it though.

An issue with the usb is also that it gives you like 16 options, so unplug all your usb devices except for your printer, and then choose usb 1 choose your printer, and it should work.

it did for me at least.

---

### Post by chz on 2005-03-29
apparently i have the driver that i need. is there something else that i need besides a printer driver? i've tried manually adding the printer when the only usb device connected is my usb printer. in the Printer Window it says that my printer is ready...which is odd, but still when i send a test print....nothing comes out. Any other ideas?

---

### Post by teumima on 2005-03-29
[QUOTE=chz]apparently i have the driver that i need. is there something else that i need besides a printer driver? i've tried manually adding the printer when the only usb device connected is my usb printer. in the Printer Window it says that my printer is ready...which is odd, but still when i send a test print....nothing comes out. Any other ideas?[/QUOTE]
 printer being ready doesn't mean anything.

u found your printer on the list?

also try [www.linuxprinting.org](www.linuxprinting.org) and look up ur printer

---

### Post by chz on 2005-03-29
have no idea what was going on before, but now it works, and the printer is detected. only thing now is that the printer doesnt print as cleanly as it used to. i tried changing the drivers from CX 5400 to C84 drivers (as recommended by linuxprinting.org), but same thing. maybe the heads need to be cleaned, but thats for another forum i guess =P. thank you all for your help =)

---

