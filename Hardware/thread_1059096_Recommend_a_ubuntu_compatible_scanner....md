---
title: "Recommend a ubuntu compatible scanner..."
date: 2009-02-03
forum: Hardware
---

### Post by trooperchix on 2009-02-03
I need recommendations for a portable scanner that will work with this OS.  I am running Intrepid...

---

### Post by theDaveTheRave on 2009-02-03
trooperchix

If you are planing on using a "portable" scanner, I guess that means you are also using a laptop??

if so can you not take your laptop down to the local store and ask if you can plug in the various scanners to see which ones work?

My recent experience with scanners is that most seem to work straight off. Mostly however they have been "desktop" devices that are part of a printer/scanner device. Best results for me have been from HP devices.

hope this helps.

David

---

### Post by trooperchix on 2009-02-04
Yes, I run a laptop and have an insane amount of documents daily to scan, so leaving to get things scanned doesn't really work for me.  I'll check into HP products.  Thanks for your help!

---

### Post by trooperchix on 2009-02-04
I think I found one, but not sure.  Does anyone know the compatability for the Pentax DS Mobile Scanner?

---

### Post by desertdog on 2009-02-18
You can visit the sane web site to find which scanners are currently supported.

The Syscan Travelscan 464 is fully supported. It is no longer marketed, but you can pick these up on ebay. In the US it is usually sold under the Ambir label.

The Plustek OpticSlim M12 is partially supported in the current Sane release. The Neat Receipts Scanalizer is probably the same scanner and should partially work too. 

The Syscan TravelScan 662 is fully supported, but handles the smaller, A6 paper size.

If you are willing to download the cvs and rebuild Sane from source, there is partial support for the Visioneer XP Strobe 100, 200 and 300 models. But this is not something a beginning linux user would want to do.

The Docketport line of scanners [http://www.docucap.com/](http://www.docucap.com/) have a proprietary commandline linux driver, that is not Sane compatible. These are sold under the ambir label in the US. You have to email docucap to get the linux driver. They might tell you that the linux driver is only for resellers of their product, but if you keep bugging them, they will give it to you. I've been told by someone at the company that they will have SANE support for the newest DocketPorts in the near future.

There is a proprietary linux driver with a GUI frontend for the Pentax DS Mobile. This model is no longer sold new. You can find them on ebay. The Pentax DS Mobile 600 does not have sane support or a proprietary driver. To get the proprietary linux driver for the DS Mobile, you have to email Pentax support.

---

### Post by trooperchix on 2009-03-03
> **desertdog said:**
> You can visit the sane web site to find which scanners are currently supported.

The Syscan Travelscan 464 is fully supported. It is no longer marketed, but you can pick these up on ebay. In the US it is usually sold under the Ambir label. 


Thanks a ton!!  I found exactly that model under the syscan Travelscan name, and got it for $30.  You rock man..


:guitar:

---

### Post by Pa Blum on 2009-10-15
Hey!  Thanks to this thread, I also got a 464, followed the SANE instructions, and am now scanning my little brains out.
Thanks ever so....

---

### Post by desertdog on 2010-01-24
Support for several additional sheetfed scanners has been added since my previous post.

Calibration has been added for the Plustek OpticSlim M12, Neat Receipts Scanalizer, and Iriscan Express 2 line of scanners.

The Visioneer RoadWarrior, Pentax DS Mobile 600 are supported, including calibration.

Duplex scanners (Visioneer XP300, DocketPort 485 and 487) are not completely supported yet.

The Visioneer XP200 is fully supported as well.

To enable the above scanners, you must download and compile from source. [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html) is a good description of how to do this.

---

### Post by shanepardue on 2010-07-03
> **desertdog said:**
> Support for several additional sheetfed scanners has been added since my previous post.

Calibration has been added for the Plustek OpticSlim M12, Neat Receipts Scanalizer, and Iriscan Express 2 line of scanners.

The Visioneer RoadWarrior, Pentax DS Mobile 600 are supported, including calibration.

Duplex scanners (Visioneer XP300, DocketPort 485 and 487) are not completely supported yet.

The Visioneer XP200 is fully supported as well.

To enable the above scanners, you must download and compile from source. [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html) is a good description of how to do this.
I'm running into a wall with the Iriscan Express 2 on 10.04 with the Sane backend 1.0.22git. No scanning software will recognize it.

---

### Post by desertdog on 2010-07-04
The Irisscan express 2 uses the gt68xx backend.

See: [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

First thing that comes to mind is, did you extract the firmware file cism216.fw from the windows cd and place it in the directory specified in /etc/sane.d/gtxx.conf?

Also, you might have to make an entry in /etc/sane.d/gtxx.conf for your scanner, with the "override" command.

Edit:
Forget the override command that I mentioned above.
You do want to have an entry for this scanner in /etc/sane.d/gtxx.conf that reads like:
> ##############################################################################
# Iriscan Express 2
usb 0x07b3 0x045f

##############################################################################

---

