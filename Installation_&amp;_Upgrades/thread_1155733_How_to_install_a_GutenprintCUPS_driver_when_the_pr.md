---
title: "How to install a Gutenprint/CUPS driver when the printer is not connected?"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by ub40d on 2009-05-11
I have to configure an ubuntu installation for a very non-technical person who is in another location. In particular I have to ensure that they can print. I know the exact model of printer they have (an Epson DX4400 connected by usb) and I have established that there isn't a printer driver for it in the normal "known printers" database, but that it is supported by Gutenprint. 

I have installed CUPS and Gutenprint. I now want to install and configure the computer to use that printer (which I don't have) before sending off the computer. However (THE PROBLEM) when I do the CUPS "add printer" thing, it asks me where it's connected and it doesn't SHOW me the option of "connected through usb". It only does so when I plug in a usb printer.

I've done so with my Canon and it recognized its model and maker etc etc. All very nice, but it means it later only lets me choose a Canon driver for it.

So THE QUESTION: how can I pre-add a CUPS/Gutenprint printer to the system before it being connected? How can I tell it, "trust me, let me install an epson driver for the usb port even if there's nothing there right now"?

---

### Post by Mark Phelps on 2009-05-11
If you can hunt down the appropriate ppd file, I believe that when you go to setup the printer in CUPS, it gives you the option of selecting the printer model or providing a ppd file.  If you provide the file, that should take care of it.

---

### Post by ub40d on 2009-05-11
> **Mark Phelps said:**
> If you can hunt down the appropriate ppd file, I believe that when you go to setup the printer in CUPS, it gives you the option of selecting the printer model or providing a ppd file.  If you provide the file, that should take care of it.

Unfortunately with this setup I have to use the other choice, where you have a drop-down list of drivers, not the one where you quote a ppd. So, still on the lookout for a way to select a driver (which I know Gutenprint provides) even though the matching printer is not at that point attached to the usb port.

---

### Post by ub40d on 2009-05-11
Maybe getting there...

Experimenting with another computer at work, where I have a totally different Epson (it's a laser rather than an inkjet-all-in-one) it seems as if, with that connected, I am able to select ANY Epson driver. 

Tomorrow I'll bring the target laptop here and see if I can do it that way. Still short of the ideal solution but it may get me out of trouble!

---

