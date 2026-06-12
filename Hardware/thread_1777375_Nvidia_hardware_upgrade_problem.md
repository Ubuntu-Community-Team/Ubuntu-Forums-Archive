---
title: "Nvidia hardware upgrade problem"
date: 2011-06-07
forum: Hardware
---

### Post by Pizarro on 2011-06-07
I have just upgraded my nvidia pci-express video card from a GS7600 256mb to a G210 512mb. But as soon as the boot leaves the bios screen I see nothing. The screen does not die or report out of frequency it just shows blank. Any ideas The driver installed is version 173.I have removed the card and placed in a windows machine and it all works fine when I installed the drivers. As soon as I replaced the old card back into the ubuntu machine it works fine. Help I don't want to have wasted my money.

---

### Post by wolfen69 on 2011-06-07
With the old card in the machine, I would uninstall the nvidia drivers, shut down the machine, and put the new card in. Then install the nvidia driver again. Btw, you should be using a newer driver with the new card. The 173 driver is old, and you should be using the 270 driver.

---

### Post by Pizarro on 2011-06-07
What is the best way to uninstall the old drivers ?

Nvidia settings gui  says 173.14.30. Synaptic states 270.40.13

---

### Post by Pizarro on 2011-06-08
I've un-installed the nvidia drivers using the old card and restarted with the new card fitted. Exactly the same result bios screen then monitor goes blank. Only difference was turning off the system by pushing power button caused problem when restarting with old card. I've managed to sort this and old card is working with driver 270.41.19.
I then went back to the working windows machine and installed Super-os as a dual boot. Used the additional drivers as above and it works perfectly !!

I'm now stuck and have no idea what to do to get the machine I bought the card for running with it.

---

### Post by Pizarro on 2011-06-11
Ok now I've tried a new g210 still no joy. Did get it to work twice but only when I put the old card in the other pci-e slot. I even reinstalled ubuntu on a formatted  hard drive,with the old card but didn't install any additional drivers. Tried to boot same blank screen I now wonder if it bios or monitor. Not convinced as puppy linux boots ok from usb drive and judging by fps in glx gears is running fine.
Motherboard is elite group 915PL-A2
Monitor fujitsu siemens 19- lcd wide-screen vga only

 So again help please

---

