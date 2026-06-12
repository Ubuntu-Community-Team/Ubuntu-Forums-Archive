---
title: "Asus Z87Pro flash bios boot from usb"
date: 2018-11-04
forum: Hardware
---

### Post by mcyber4 on 2018-11-04
Hi
I need to completely flash a Asus Z87pro bios but I can't find the button on the Motherboard. Also I tried to boot with freedos from Rufus usb stick but no luck also.
Thanks for help.

---

### Post by dino99 on 2018-11-04
Goto your bios/uefi settings
I does not get that mobo, but an other one where flashing can be done from the uefi menu.
As yours is newer than mine, you should find that feature too.

---

### Post by oldfred on 2018-11-04
In your Asus UEFI, you need to go to the far right tab - tool.
And your update needs to be in a FAT32 formatted partition, so it can be read directly from UEFI.
I typically copy it into my ESP, but have had to change permissions on the ESP to allow me to copy files into it.

---

### Post by him610 on 2018-11-04
Normally a CD comes with each motherboard that has the update bios feature one can run. Don't know if yours has this feature or not, but newer motherboards can be updated through BIOS/UEFI options over the internet as long as you have a good wired internet connection. 
The manual that came with your motherboard has a section explaining how to update/flash your BIOS.

---

