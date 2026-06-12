---
title: "eSata port in Dell Latitude E6400 not working in Ubuntu Desktop 14.04.3"
date: 2016-01-21
forum: Hardware
---

### Post by davidesweden on 2016-01-21
Hi,

I installed Ubuntu Desktop 14.04.3 in my laptop Dell Latitude E6400.
This laptop has an eSATA port, configurable in the bios as ATA, AHCI and IRRT. I used to connect an external drive bay to such a port.

This was working in the past with previous Ubuntu/kernel versions, when configured as IRRT. It was able to recognize all drives connected in the external drive bay. With the latest Ubuntu version, it stopped working. The OS does not recognize the disks at all. 

Perhaps the eSATA support has been removed in the latest kernels?

Thank you in advance for your help.
David

---

### Post by sudodus on 2016-01-21
I can even boot a computer via eSATA just like it were a standard SATA drive. To be 100% sure I just tested with Lubuntu Xenial alpha 1 (to become 16.04 LTS in April). eSATA is supported and will be supported for a long time. Actually I think eSATA is 'seen' as SATA by the linux system :-)

If you have problems, something else is wrong. Have you checked if it works with older versions of Ubuntu now? You can test it live, booted from a DVD disk or USB pendrive (without installing).

-o-

I don't know, if there is some electronics or firmware in your laptop, that might cause problems. Maybe there is an updated version of the UEFI/BIOS system, and eSATA might work after updating?

---

### Post by davidesweden on 2016-01-21
Thank you for the reply. [COLOR=#000000] I just tested live with Lubuntu Xenial alpha 1 ([/COLOR]http://cdimage.ubuntu.com/lubuntu/releases/xenial/alpha-1/[COLOR=#000000]), booted from USB drive. Same result, no drive is seen at all.

The bios version I have is the latest, release A34. I tried to change the SATA setup in the bios, tried both AHCI and IRRT. Which one do you have?

Is there any check I can do from the command line to see if some error occurs during bootup?[/COLOR]

---

### Post by sudodus on 2016-01-22
It works with AHCI for me, but I think it works also with the other settings.

We have eSATA ports in laptops as well as in desktops in my family, and I have never had the kind of problems you describe. Our laptops are HP brand. Maybe someone else, who reads this thread, has a Dell and knows if there are compatibility problems with the eSATA port.

Have you checked if you can connect via eSATA when you run an older linux operating system?

The problem might also be the electronics in the external drive bay, that it is not recognized by any driver in the new versions of Ubuntu. If you get a SATA to eSATA cable, you might be able to test with a 'naked' SATA disk connected via the eSATA port.

---

