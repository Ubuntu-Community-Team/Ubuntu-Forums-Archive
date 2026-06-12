---
title: "SCSI scanner"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by Rick O'Brien on 2005-02-08
I am having trouble getting a SCSI scanner to work.

System: Dell Dimension 4100 733Mhz, 256 MB RAM
Card: Adaptec AHA 2940 AU (PCI)
Scanner: UMAX Astra 1200S

Scanner is turned on and showing steady green light.

BIOS recognizes scanner by name as system starts.

Ubuntu Device Manager sees adapter card.

Have tried HOWTO: UDEV/SCSI Scanner Configuration

sudo modprobe sg -- done
add sg to end of /etc/modules -- done
install sane-utils package -- done

sudo sane-find-scanner reports no SCSI scanner found
Xsane reports no devices available

sane-backends does not seem to be in Synaptic Package manager

I've downloaded and decompressed a newer version of sane-backends but can't figure out where or how to install them.

I'm stumped.

---

### Post by wandalalakers on 2008-06-17
I have this same scanner and kubuntu 8.04.
Anyone with kubuntu 7.10 or 8.04 get a Umax Astra 1200S to work?

---

