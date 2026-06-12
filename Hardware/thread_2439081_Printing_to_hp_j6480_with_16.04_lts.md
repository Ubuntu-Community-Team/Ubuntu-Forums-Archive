---
title: "Printing to hp j6480 with 16.04 lts"
date: 2020-03-22
forum: Hardware
---

### Post by fahrbach on 2020-03-22
Apologies if this is the wrong forum.  I believe have downloaded the software and installed it via command line.  But how do I get my printer to show up in the GNOME Add Printer?

---

### Post by fahrbach on 2020-03-22
and this is a wireless printer.

---

### Post by fahrbach on 2020-03-22
I did get this error:  CUPSEXT could not be loaded.

---

### Post by Furycd001 on 2020-03-23
Looking around online shows that other people have had similar problems. They managed to solve their problems by installing a few files & then re-running the installer. Could you install the following & then re-run the installer....

```
sudo apt-get install hplip-gui hplip hplip-cups hplip-data hpijs hpijs-ppds
```

---

### Post by fahrbach on 2020-03-25
Thank you, Fury!  So I followed your suggestion, re-ran the installer.  What should I see when I go to +Printer?  Do I need to be on the network - this is a networked, wireless printer.  I have not tried that yet.

---

### Post by Autodave on 2020-03-25
Tell the printer to connect wirelessly: it is in the options.  Once you do that, Linux should find it right away.

I did not install anything here: I turned the printer on, went into its menu and chose to connect wirelessly.  It connected just fine.  Hplip and hplip-gui will need to be installed to scan.

---

### Post by slickymaster on 2020-03-25
*Thread moved to **Hardware**.*

---

### Post by fahrbach on 2020-03-26
Thanks, Dave!!

---

