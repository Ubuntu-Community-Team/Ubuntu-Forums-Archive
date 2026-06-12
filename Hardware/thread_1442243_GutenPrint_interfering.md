---
title: "GutenPrint interfering?"
date: 2010-03-29
forum: Hardware
---

### Post by Rocket J Squirrel on 2010-03-29
My Ubuntu laptop is connected to a Windows network that has four shared printers. 

From the laptop I can print test pages, etc., with two of the printers. I cannot with the other two. 

On another machine, a Windows machine, also connected to the network, I can print to all four of the shared printers. So I know that the printers are fine.

Looking at the drivers used by Ubuntu for the four printers, I see:

Printer 1 uses an hpijs driver. This one works.
Printer 2 uses an hpcups driver. This one also works.
Printer 3 uses a CUPS+Gutenprint driver. This one does not work. 
Printer 4 uses a CUPS+Gutenprint driver. This one also does not work. 

When I say "does not work," I mean that I get a dialog box that says, "there was a problem processing document `test page' (Job nn)."

Printing Troubleshooter for these printers says that the Server is not  Exporting Shared Printers to the network. But as mentioned, they work fine using a Windows client. 

The common feature seems to be the CUPS+Gutenprint drivers. 

[I]Note: For Printer 3, an Epson Stylus Photo R2400, I want to use the (recommended) Gutenprint driver, as I will use it with the GIMP. A couple Foomatic drivers are also offered, but not listed as recommended ones.  

For Printer 4, a Canon PIXMA iP5000, I don't care what kind of driver I use, but the CUPS+Gutenprint one is the only one showing as an option. [/I]

Maybe I have a broken Gutenprint install or something?

My thanks in advance for any help that might be provided.

---

### Post by Rocket J Squirrel on 2010-03-29
Followup to above:

For Printer 3, I changed the driver to a Foomatic+gutenprint one and the printer works. I don't know if I lose any color fidelity or quality using the Foomatic+gutenprint in the GIMP vs using the CUPS+Gutenprint driver. 

For Printer 4, as mentioned, all Printer Properties is offering for a driver is a CUPS+Gutenprint one.

---

