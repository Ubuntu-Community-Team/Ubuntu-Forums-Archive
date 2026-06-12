---
title: "quick question about installing graphics card drivers for laptops"
date: 2015-05-15
forum: Hardware
---

### Post by kaitlin3 on 2015-05-15
ok so i have a mobility HD 3659 dedicated card in my laptop and im using Lubuntu with the stock GPU drivers that came with the Lubuntu installer. how ever while browsing the Lubuntu software center i came across this app ati binary x.org driver version 2:15.200-0ubuntu4 (fgrlx) in the info it says this package provides 2D display drivers and open GL for X11 what does that mean and should i install this driver?

---

### Post by QIII on 2015-05-15
Hello!

Unfortunately, AMD has withdrawn Linux driver support for all video adapters prior to the HD 5000 series.  If you attempt to install that driver, you will get a warning that no supported hardware is present.

If you go to AMD's website to download the driver and install it, you will render your system unusable.

The default open source Radeon driver you are currently using is the appropriate one for your hardware.

---

### Post by kaitlin3 on 2015-05-16
but the driver i mentioned above is from the ubuntu software center so doesnt that mean its open source mening the open source driver should support my GPU

---

### Post by deadflowr on 2015-05-16
> **kaitlin3 said:**
> but the driver i mentioned above is from the ubuntu software center so doesnt that mean its open source mening the open source driver should support my GPU

No. 
Look at the license.
The software center lists packages from all the connected repositories, including repositories which contain "non-free" packages.
(it is known as the restricted repository)
the fglrx package is one such package.

Your card, as mentioned, is already using the best driver it can.

---

### Post by kaitlin3 on 2015-05-16
ok thanks for the education didnt know there was a restricted repository

---

### Post by deadflowr on 2015-05-16
Don't worry.
You're not the first the run into this, and most certainly won't be the last.
The fglrx + amd 2XXX to 4XXX cards problem has been a thorn in several a thread here for nearly 3 years when amd dropped support for those cards.

You at least took the time to think about asking first, and saved yourself a bootload of trouble.
Others weren't so smart.

---

