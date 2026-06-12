---
title: "How do I determine the &quot;Device URI&quot; for an HP printer"
date: 2011-04-02
forum: Hardware
---

### Post by Emily13073 on 2011-04-02
I have Ubuntu 10.04 and am trying to get an HP LaserJet 4M Plus printer to work with it.  I have gone to System - Administration - Printing, and the clicked "Add printer."  It then asks me for the "Device URI"  I have spent over an hour online looking for whatever the heck this is and am even more confused than when I started.  Can anyone help me out here?

Sorry if this is an obvious question.  I'm not very well-versed in the way of computers.  All I know is that I can't stand Microsoft; hence, my Linux computer given to me as a gift.  

Also, the plot thickens (perhaps) The printer itself has what I believe you would call a parallel port, but at the end of the cable where it plugs into my computer, it is a USB port.  This particular cable says it is Linux compatible and it came with a small CD.  I am not quite sure how I use this CD or if it is even necessary to use it.

Thank you very much for your help.

Emily

---

### Post by walt.smith1960 on 2011-04-02
The  good news is that HP machines are well supported in Ubuntu/Linux.  The cable is most likely a USB to parallel cable.  Did you have the printer powered up when you did the "find printer" command?  Here is an example of the device URI of a printer connected via USB to give you an idea of what a device URI looks like. I expect yours will be a similar format but different text:
```
hp:/usb/psc_1310_series?serial=xxxxxxxxxxx
```Does your computer have a parallel port connector? It's typically an elongated D shaped affair with two rows of holes--13 holes in top row, 12 holes in the bottom.  It may be colored reddish/purplish.  If your computer has one of those you might try a parallel cable to eliminate one variable.  The cable you have now is for PCs that don't have parallel ports like most portables.  The mini CD probably has drivers to enable Windows to recognize the USB/parallel cable.  I don't know if there are *nix drivers on there but I'd be skeptical. I have a USB/serial cable that Ubuntu recognizes as soon as it's plugged in but I can't say about your device.  Good luck, you should be able to get your HP working.

---

### Post by Emily13073 on 2011-04-08
Walt,  Thank you for your response.  Sorry it has taken me a while to get back to you.

Unfortunately, the computer does not have a parallel port -- only the printer has that.

The "Find Printer" thing didn't work.  It asks for the URI Device Driver.  I'm convinced that the problem is that the cable isn't being "read" by the computer.  The cable came with a disc that I had to install on my two other Windows computers in order for the printer to work with them -- just plugging in the cable didn't work.  So I think it's the same with the Linux computer.  The disk with the cable has choices to use Linux, Windows, or Mac.  The Windows instructions were easy enough to follow on my two other computers, but the Linux option gave me a bunch of gibberish that I couldn't understand.  SO, I will wait until the person who gave me this computer can walk me through how to get the whole thing working.  Thanks for trying to help, though!

Emily

---

### Post by walt.smith1960 on 2011-04-09
Hi Emily

Sorry I don't have any experience with this so don't really have any further suggestions. If your PC is a desktop, it might be possible to find PCI cards that add parallel ports to computers that don't have them.  Here are some examples:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=pci+parallel+port](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=pci+parallel+port)

At least some of them claim Linux support.  I learned through experience with a USB wifi adapter that claiming to have Linux support and having practical workable Linux support can be two different things. Perhaps someone who has had experience with these cards will check in.

---

