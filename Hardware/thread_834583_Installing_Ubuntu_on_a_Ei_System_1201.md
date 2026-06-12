---
title: "Installing Ubuntu on a Ei System 1201"
date: 2008-06-19
forum: Hardware
---

### Post by The Browncoat Cat on 2008-06-19
I have just bought an E-System 1201 notebook laptop and I cannot get Ubuntu to install on it.  The installer starts running, and then immediately hangs.  Am I missing something/
The technical specs are as follows:
# Processor Type: Intel Pentium Dual Core T2370
# Processor speed: 1.73 GHz, 533 MHz FSB, 1 MB Cache
# Memory Size: 1 GB MB
# Memory Type: DDR2 RAM
# Hard Drive Capacity: 120 GB
# Screen Size/Type: 13.3 inches
# Sound Type: Realtek

---

### Post by The Browncoat Cat on 2008-06-19
Additional information.  It seems to be a problem related to the ACPI.  The installation hangs when it gets that far.

---

### Post by Thropcat on 2008-07-01
put noapic nolapic irqpoll=off!. do you know what the wifi chipset is on this notebook?

---

### Post by Thropcat on 2008-07-02
thats with acpi=off btw ;)

---

### Post by The Browncoat Cat on 2008-07-17
> **Thropcat said:**
> put noapic nolapic irqpoll=off!. do you know what the wifi chipset is on this notebook?
The WIFI card is a LITEON NET8187b wireless card.  I have now managed to get Ubuntu to boot on the system, but it refuses to switch on the WIFI card.  NDISGTK  and "NDISWrapper -l" reports that the driver has been installed, but no hardware is present.

---

### Post by walker-d on 2012-01-02
I cannot understand why you had a problem installing ubuntu on that laptop as I have exactly the same machine and had no problems at all . I don't know if it helped but I have upgraded my memory to 2gb improved the performance on end best £12 I ever spent . I also completely deleted my windows vista os , mainly by accident , that's why I installed ubuntu in the first place , turned out to be a lucky accident as I am more than happy with ubuntu , makes you feel sorry for the poor souls using windows with all its viruses and brake downs .

---

