---
title: "Print to fake printer"
date: 2013-03-31
forum: Hardware
---

### Post by pepribal on 2013-03-31
This might sound a bit awkward.

Let's imagine a black box computer, which doesn't accept any kind of input (except for keyboard/mouse), and it doesn't let you output anything but video signal (monitor). However it does let you print documents through an usb printer.

My question: is there any way to attach "whatever device" to the usb printer port so that it replaces the printer, but it's not a printer. Something that stores the printed documents in electronic format. I mean, can I make a "fake printer" using another PC, or a usb stick?

This is a quite general question, so I don't think more details are needed.

Thanks.

---

### Post by wojox on 2013-03-31
Sure,  just write a new driver for your new peripheral.

---

### Post by sudodus on 2013-03-31
You can 'print to file' (a pdf file) instead of a printer in Ubuntu. So you need not print via USB.

File -- Print ... 
or
File -- Preview ... and File -- Print ...

But in Libre Office it is better to 'Export to pdf' instead of writing pdf files via File -- Print ...

---

### Post by pepribal on 2013-03-31
Yes, I can print to a file, however I cannot get the generated pdf out of the black box PC. The only "gate out" of the system is the printing usb port. I was asking in case there was an easier way (I cannot install drivers either).

---

### Post by sudodus on 2013-03-31
What do you want?

You have a USB port. Such a port is very general. Normally you can connect any USB device to it (for example a USB pendrive).

Or are you talking about an old-fashioned serial port. In that case you might be able to use a serial 2 USB adapter. Maybe you also need a powered USB hub, where you can connect a USB pendrive.

---

### Post by pepribal on 2013-04-01
I would like to "capture" the output from the usb port. The document sent out to the printer should end up in a device that stores it as an electronic document. I cannot do anything inside the computer, so I should do everything outside it.

---

### Post by sudodus on 2013-04-01
Is this what you want?

[[COLOR=#ff0000]http://www.pclviewer.com/resources/capture/print2usb.html[/COLOR]]("http://www.pclviewer.com/resources/capture/print2usb.html")

You can find more if you search the internet with the search string ***printer data format***

---

### Post by lisati on 2013-04-01
Reading this thread sparked a memory of something I first read about back in the 1980s. I think what the OP is looking for is similar in concept to a print spool appliance.

---

### Post by pepribal on 2013-04-01
> **sudodus said:**
> Is this what you want?

[[COLOR=#ff0000]http://www.pclviewer.com/resources/capture/print2usb.html[/COLOR]]("http://www.pclviewer.com/resources/capture/print2usb.html")

You can find more if you search the internet with the search string ***printer data format***

Well, yes, it looks like it. I'll check it. Thanks!

---

