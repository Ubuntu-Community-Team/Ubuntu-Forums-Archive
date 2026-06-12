---
title: "Apogee CCD camera"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by nurbl on 2007-12-10
Hi,

I've been using an Apogee CCD usb camera ("Alta U 2000") with Ubuntu "Feisty" without trouble, but since I upgraded to "Gutsy" it stopped working, just giving me a segmentation fault. The same thing happens under Hardy. Using Feisty's kernel under Gutsy doesn't solve the problem, which leads me to think that the problem is not related to the kernel. Has something else changed with regard to usb handling?

I'm using the linux drivers from [http://www.randomfactory.com/downloads/](http://www.randomfactory.com/downloads/) which are free but the software is kind of primitive... haven't found any alternatives though, and they seem reliable when they work. The camera server is based on tcl/tk.

"dmsg" reports the following when the camera is connected. I'm almost positive that the messages are the same under Feisty with the camera working though, so it's hard to say if it's connected to the problem.

[INDENT]
[23815.864000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[23815.996000] usb 5-4: string descriptor 0 read error: -32
[23816.000000] usb 5-4: string descriptor 0 read error: -32
[23816.000000] usb 5-4: configuration #1 chosen from 1 choice
[23816.004000] usb 5-4: string descriptor 0 read error: -32
[/INDENT]

Any clues are welcome!

/Nurbl

---

