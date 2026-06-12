---
title: "Asus Essentio IR"
date: 2009-05-05
forum: Hardware
---

### Post by woodsby on 2009-05-05
I just bought an Asus Essentio CS5111 with an onboard CIR (consumer infrared) receiver.  The vista driver provided with the computer is an ITE CIR driver.  Unfortunately in Ubuntu, I am unable to load this module and start lirc.  LSPCI and LSHW list nothing resembling an ITE IR receiver.  Any thoughts on where to start?

---

### Post by jama999 on 2009-05-19
> **woodsby said:**
> I just bought an Asus Essentio CS5111 with an onboard CIR (consumer infrared) receiver.  The vista driver provided with the computer is an ITE CIR driver.  Unfortunately in Ubuntu, I am unable to load this module and start lirc.  LSPCI and LSHW list nothing resembling an ITE IR receiver.  Any thoughts on where to start?

Did you ever get anywhere with this?  I have the same box and have not had much luck with it either.

---

### Post by woodsby on 2009-06-15
I determined it was unsupported, so I bought a cheap windows mce usb ir receiver.  I was/am trying to use this with a harmony 890 pro remote, so I just used the default mce codes, but added the power button from the asus remote, since that is the only function that works.
Other than that, I'm loving the machine... i use it as my htpc with a myth frontend and some other media stuff.  the 1080p w/ audio over hdmi is pretty sweet.

---

### Post by jama999 on 2009-06-16
> **woodsby said:**
> I determined it was unsupported, so I bought a cheap windows mce usb ir receiver.  I was/am trying to use this with a harmony 890 pro remote, so I just used the default mce codes, but added the power button from the asus remote, since that is the only function that works.
Other than that, I'm loving the machine... i use it as my htpc with a myth frontend and some other media stuff.  the 1080p w/ audio over hdmi is pretty sweet.

Hmm, thanks for the feedback.  I love mine as well.  I upgraded the processor to an e5400 and it will play 1080p all day long using VLC from an NFS share I have to another Ubuntu box on my home network.  I actually got SPDIF *and* HDMI audio working simultaneously with some trickery in pulseaudio.  Surround only works over the SPDIF, but thats ok cos my old school receiver only has fiber/coax anyway.

RE: the remote, it is a standard CIR RC6 with a very common IR transmitter receiver pair so it *should* be able to be used with the standard Philips/MCE remote extensions in the latest Jaunty supported versions of Lirc.  I am going to keep working on this since it is literally the only thing left is my very cheap/slick setup that doesn't work.

Film at 11,

J

---

### Post by kapad on 2009-09-02
I also have a dell studio 15 which was sent with ITE CIR drivers for vista but i am trying to get the dell media remote to work with ubuntu. 
any ideas that may help

---

### Post by chel88 on 2009-09-02
I have a question that may be stupid 

Can you use any type of monitor with a ASUS Essentio Desktop CS5111- AP007 ?


I want to use a LG W1943TB-PF LCD Monitor[B]
[/B]

---

### Post by jimbo333 on 2009-12-25
I just uploaded a patch that adds support for the chip in the Asus Essentio, the ITE8704 / ITE8718 (this device only appears in the ACPI device list, it is not a PCI device). The patch can be found here: [http://sourceforge.net/tracker/?func=detail&aid=2920966&group_id=5444&atid=305444](http://sourceforge.net/tracker/?func=detail&aid=2920966&group_id=5444&atid=305444). At this time, you will have to download the LIRC source, apply this patch, and compile manually.

---

### Post by jjmatt on 2011-01-18
Has this patch been added to the latest LIRC?

---

### Post by jimbo333 on 2011-01-18
It had been commuted to trunk a few weeks after the patch was posted
  It is on the latest release and in the latest linux kernel now.

---

