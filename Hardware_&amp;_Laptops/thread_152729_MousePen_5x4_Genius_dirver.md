---
title: "MousePen 5x4 Genius dirver"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by gmaisg on 2006-03-30
Hi, i have Ubuntu 5.10 (Breezy) installed in my computer. I received as a present the mouse tablet from Genius (MousePen 5x4). After a research on the web, i found the WizardPen driver. On my other OS (Elive) the installation went perfect, and it is based on Debian, just like Ubuntu. But when i tried to install it in Ubuntu it did not go. I installed the requirements, but no luck. I received an error message trying to compile the driver. I searched in Ubuntu forums but the topics i found did not help at all. I would apriciate any help, since i am a graphic designer and the pen tablet is just perfect.

Thanks,

Ton

---

### Post by Tom Tiger on 2006-04-22
hmm.... you're not the only one,  I'm trying to get my old wintime USB tablet to work.  It is seen as a hid so therefor I should be able to use it as kind of mouse but for some reason it won't.....

Then again, I love a good puzzle

---

### Post by conmiweb on 2006-04-26
Have you solved the problem?How?I'm able to use the mouse, but no the pen :'( please help me!!!

---

### Post by daller on 2006-09-07
If your tablet uses the Wizardpen-driver, then look at my guide:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

...And please let me know the output from "lsusb" on your machines!

---

### Post by Tom Tiger on 2006-11-17
I have no idea if mine uses the wizardpen driver but here is the dmesg info

usb 1-1: new low speed USB device using uhci_hcd and address 3
usb 1-1: configuration #1 chosen from 1 choice
hiddev96: USB HID v1.00 Device [Wintime USB Tablet] on usb-0000:00:1d.0-1

this is actually very hopefull, at least it is detected :-)

lsusb returns 

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 08f3:00e5  
Bus 001 Device 001: ID 0000:0000 

which is interesting

I think I'm pretty close to getting it to work, I'll try your guide and see what it does with this little tablet.

L8tr... Tom

---

