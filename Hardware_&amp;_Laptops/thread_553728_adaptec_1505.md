---
title: "adaptec 1505"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by jonegr on 2007-09-18
I have just installed Ubuntu on an old P3. It has an adaptec 1505 scsi card to allow a Scanmaker X6 scanner to be used. I have a reasonable amount of experience with Windows environments BUT none with LINUX.
I was hoping someone could tell me
1. Is it possible to use the 1505 and the Scanmaker with Ubuntu?
2. If so can you point me to some directions for achieving this keeping in mind that I know next to nothing about Linux?

I will be very grateful for any assistance.
Greg Jones

PS I am very impressed with Ubuntu in the short time I have been using it

---

### Post by linuxwizard on 2007-09-20
According to this that scanner will work complete
[http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK)
complete: means the backends supports everything the device can do.

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)
[http://tldp.org/HOWTO/Scanner-HOWTO/index.html](http://tldp.org/HOWTO/Scanner-HOWTO/index.html)

This shows SCSI Adaptec 1505 is supported
[http://tldp.org/HOWTO/Hardware-HOWTO/scsi.html](http://tldp.org/HOWTO/Hardware-HOWTO/scsi.html)

---

### Post by jonegr on 2007-10-17
Thanks for the reply. I have been away hence the delay in reply. 

In device manager  (screenshot attached) the card is shown as a PNP device. I have set the bios to non PNP supporting OS and changed IRQ 10 to ISA. Still showing up as PnP in device manager. Don't know if this is problem or not.
If this is a problem I will create a DOS boot floppy with the scsiselect utility and modify the card settings.

xSane scanning utility is installed but does not detect the scanner.

I am not sure how to proceed. Any further suggestions would be gratefully received.

Thanks in anticipation
Greg Jones

---

