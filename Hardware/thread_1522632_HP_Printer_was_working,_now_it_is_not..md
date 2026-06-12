---
title: "HP Printer was working, now it is not."
date: 2010-07-02
forum: Hardware
---

### Post by fillmont on 2010-07-02
Hello all! I have an HP LasterJet1320 and Ubuntu 10.04. Everything was hunky dory - printing was a breeze. That is, until today, because every time I try to print, Ubuntu just says in the print queue that the HP may not be connected (the message occurs in the Document Print Status queue that appears in the top right corner, not the actual Printer queue, which says nothing). Repeated reboots of both computer and printer reveal no changes.

The printer is able to test print within itself (by pushing the green button) but any attempts to force a test print through Ubuntu results in the same ''Processing - Not Connected?" message. I have tried moving around the USB connections, and as far as I can tell, if there is a problem with the connections, it is not with the computer. Unfortunately I don't have any spare USB connectors, so I can't check if the USB wire has gone bad (I'm not even sure if that's a reasonable thing to conclude - can USBs go bad?)

So I'm basically asking what troubleshooting can be done through Ubuntu to see why it is that it suddenly can't connect to the printer. Maybe some command line goodness?

---

### Post by riddell on 2010-07-03
This just happened to me as well. HP 1012. Working yesterday and suddenly not.

The line shows up on lsusb:

Bus 001 Device 004: ID 03f0:0d17 Hewlett-Packard LaserJet 1012

All I get is the cryptic message Printer may not be connected.

I can delete the printer and re-add it with no problems (the wizard finds it) but it still wont print anything.

Cheers

---

### Post by jrifkin on 2010-07-04
Same problem, but I found three workarounds that work.

PROBLEM
  Same error in Gnome Printer Panel Applet, "Processing - Not connected?"
This happened on two computers running Ubuntu 10.04, when connecting to an HP 1320 over USB.

WORKAROUND 1 - RAW PRINTING VIA USB
  I can 'cat' a postscript file directly to the usblp0 devices, 
   > cat test.ps > /dev/usblp0

WORKAROUND 2 - USE PARALLEL PORT
  When I connect my desktop to the HP 1320 using a parallel cable, everything works fine.

WORKAROUND 3 - USE DIFFERENT PRINTER MODEL VIA USB
  By default, CUPS configures the printer as Make-Model HP-1320.  After the printer first installed I went back and changed the driver, choosing the Make-Model as GENERIC-PCL6/PCL XL Printer, and the Driver as "Generic PCL6/PCL XL Printer Foomatic/pxlmono".  After that, printing seems fine.

---

### Post by riddell on 2010-07-04
I'm still not sure why the error happened in the first place. This is the solution that worked for me:

System->Administration->Printing

Right click on the problematic printer.

On the line Device URI: there was a hp://.... line, I clicked on "Change..." and changed it to a usb:// URI

Kept Make and Model the same.

---

### Post by ario on 2010-07-05
I have the same problem with HP LazerJet 1320 connected to my desktop with Ubuntu 10.04. I used to work properly but after updating, it's not!
I did workaround 1 of jrifkin it worked for me but only when I was in super user mode. But this is not an easy solution to print to file, open a terminal, sudo, run the command and... every time I want to print!
I never followed workaround 2, because I don't want to buy a parallel cabel just because of a software problem. I can connect the printer to my laptop with same operating system and it works like a charm. But not on my desktop.
I did workaround 3, But it's not working. I shows the same error "Processing - Not connected?".
I did workaround of riddell, But it's not working too. I tried a bunch of different addresses:
```

hp:/usb/hp_LaserJet_1320_series?serial=00CNRJ71Y202
hp://usb/hp_LaserJet_1320_series?serial=00CNRJ71Y202
usb:/usb/hp_LaserJet_1320_series?serial=00CNRJ71Y202
usb://usb/hp_LaserJet_1320_series?serial=00CNRJ71Y202
usb://hp_LaserJet_1320_series?serial=00CNRJ71Y202
and ...

```
but none of the above worked for me.
I think the problem "Not connected?" is related to something with address because whenever I get angry and type some rubbish in address box, It will show me the same error. How can I find the trough address of my printer without typing billions of accidental addresses?

---

### Post by ario on 2010-07-05
I tried the solution in [http://swiss.ubuntuforums.org/showthread.php?p=9549620#post9549620](http://swiss.ubuntuforums.org/showthread.php?p=9549620#post9549620) .
It says:
> Not sure if it helps but I had a similar problem with my HP laserjet 1320. After upgrading to 10.04 it would give the message "Processing - Not connected?" even though the printer seemed to be initially recognised.

I deleted the printer using the Printing Dialog (System>Administration>Printing) and added it again.

When I added it again, I selected USB connection rather the HPLIP and now it seems to work fine. Maybe something similar would work for you.

It worked for me.
But only when I right clicked in **an empty area** of printers window and selected view print queue and deleted all prints in queue. Some of theme required me to restart my pc again and again and each time delete one of them from the queue. It was just like those crazy behavioral of windows. After deleting all queues printer statue was Online and ready to printing.
So it solved for me. See the post I linked. It has a screenshot which may help you.

---

### Post by fillmont on 2010-07-13
> **ario said:**
> I tried the solution in [http://swiss.ubuntuforums.org/showthread.php?p=9549620#post9549620](http://swiss.ubuntuforums.org/showthread.php?p=9549620#post9549620) .
It says:

It worked for me.
But only when I right clicked in **an empty area** of printers window and selected view print queue and deleted all prints in queue. Some of theme required me to restart my pc again and again and each time delete one of them from the queue. It was just like those crazy behavioral of windows. After deleting all queues printer statue was Online and ready to printing.
So it solved for me. See the post I linked. It has a screenshot which may help you.

This worked wonders. I didn't have your additional problem with the queued items - simply deleting the printer and reinstalling with the USB connection did the trick. Thank you ario, and everyone else in the thread for their suggestions!

---

### Post by MG37221 on 2010-07-18
I have an Officejet 7600-E709n and I don't know how to enable the print queue in 10.04.  Was trying to print a mailing envelope.  Worked once, some time ago but I've forgotten it all (it took lots of research the first time.  These manuals from HP aren't terribly useful.  Regardless, another issue came up and a page needed to be printed now.  Envelopes in the queue (on the printer) and now a couple of more print jobs?  Forget it! Where the heck is the reset button?  So, I disconnect both power and USB since not even the power button will allow printer to shut down.  Wait for at least a minute or so hoping RAM contents (Stuff I'd sent over) will finally drop out of memory.  Reconnect power.  Reconnect USB.  LCD on printer shows a communications error, which I can't quite make go away.

I did find a way to do a full reset in Windows and, I think OSX.  Only a partial reset for others (figures) and I can't quite try it just yet due to my own physical limitations but hope to this afternoon.  Partial reset for mine is as follows:

1. Disconnect power
2. Wait 20 seconds
3. Press and hold # and 3 while reconnecting the power
4. When power returns to printer, release both buttons
5. Try printing again


I found this after scouring HP's Website.  My son has a netbook running Windows XP.  It has no CD but I think I may be able to copy my printer's install CD to a thumb drive and go from there.  If I could move faster, I sure could get a lot more done!  

I'll post back after I try the Windows route (temporarily as I ain't never goin' back to Windows!!)

---

