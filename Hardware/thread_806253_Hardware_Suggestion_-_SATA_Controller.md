---
title: "Hardware Suggestion - SATA Controller"
date: 2008-05-24
forum: Hardware
---

### Post by chomafin on 2008-05-24
Hello, 
I'm looking for suggestions on hardware.  I'd like to pick up a sub $50 SATA controller.  My mobo only has 2 sata's which are in use (and working).  Looking to find a compatable PCI/PIC-e card that wont be too much of a headache to install.
For reference, I'm using the [Biostar 6100-M7 motherboard]("http://www.biostar-usa.com/mbdetails.asp?model=GEFORCE+6100-M7").

Thanks!

---

### Post by Hydraah on 2008-05-24
Hi,

I just bought one of the cheap silicon image based 4 port SATA cards off ebay for not much more than $10AUD, and it works very well with 8.04. 

Sure it's not as good as the much more expensive cards, but it does the job.

---

### Post by chomafin on 2008-06-03
For anyone interested in similar requests..
I went through and ordered the MASSCOOL PCI Card, XWT-RC040.  This has 4 internal SATA Ports.  It uses the Silicon Image 3114 SATA chip.  Out of the box, the card would recgonize, but would not boot when my 750GB Drive was installed.  According to the user reviews this is due to an outdated firmware.  I used a FreeDOS boot disk to flash the firmware to v5.3.14 (From [SI's website]("http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=15&ctid=2&osid=0&")).  Only the board BIOS needed updating.  Once updated, the device booted and was able to see the full 750gb drive.  I was then able to add it to my LVM w/ ReiserFS with no issues.  
I've just recently installed the card, so have not had any other experience with it thus far, but seems it'll work out like a charm!

---

