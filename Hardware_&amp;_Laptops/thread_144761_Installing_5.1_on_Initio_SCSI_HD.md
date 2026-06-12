---
title: "Installing 5.1 on Initio SCSI HD"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by ChillyWilly on 2006-03-15
Hello I need some help from the local installation Gurus

I have the Ubuntu Live DVD and it has been working well.
I have decided to load it up on one of my spare SCSI HD's
The SCSI Controller is an Initio 9400UW and it is recognized in 
the BIOS but not by 5.10 Ubuntu.  I can get Ubunto to 
recognize it by typing this in a Terminal Window:

sudo modprobe initio

I have formatted the drive under the live DVD and looks good BUT
how do I get the INSTALL to recognize the initio module?

I have tried a modprobe from the Install utility terminal session but
it doesn't seem to find the initio module anywhere???

Any advice?

---

### Post by John.Michael.Kane on 2006-03-15
This may help [http://ubuntuforums.org/showthread.php?t=82466&highlight=proliant+dl380](http://ubuntuforums.org/showthread.php?t=82466&highlight=proliant+dl380)

---

