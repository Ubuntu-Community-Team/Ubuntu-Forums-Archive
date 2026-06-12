---
title: "firewire panic"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by toastball on 2008-02-14
I have a Firewire video converter (Canopus ADVC-55).  When I plug it in to my computer's firewire port, I get a kernel panic.  I've tried this a few times now, and it happens every time.  I've also been having trouble getting a DV camcorder to work -- dvgrab acts as if it isn't plugged in.  Both of these devices worked with no problems on a different computer (now dead, alas).  I don't have any other Firewire devices handy.  My computer is brand new -- there's no Firewire on the motherboard so I'm using a 4-port IEEE-1394 card made by PPA Int'l.  I'm using the x86_64 version of Ubuntu 7.10 (Gutsy).  I'm new to Ubuntu and to these forums, and I'm not even sure this is the right place to be asking about this.... Can anyone point me in the right direction?  I took a picture of the kernel panic in case that might be helpful. Fourth line from the bottom mentions RIP and ohci:1394:ohci_irq_handler+0x943/0x980; last line says "Kernel panic - not syncing: Aiee, killing interrupt handler!"  I'll see if this thing will allow me to attach the picture.  Thanks in advance for your help!

---

### Post by toastball on 2008-02-16
I guess the Firewire card was bad -- I returned it and got a different one and now everything works.  Thanks again for your help!

---

