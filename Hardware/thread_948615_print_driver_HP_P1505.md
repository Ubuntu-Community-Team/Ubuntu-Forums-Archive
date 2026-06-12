---
title: "print driver HP P1505"
date: 2008-10-15
forum: Hardware
---

### Post by yanosj on 2008-10-15
I installed ubuntu on a system with a usb connected HP 1505.  The driver was installed automatically.
URI: hp:/usb/HP_Laserjet_P1505?serial=CA3479F
make and model: HP Laserjet P1505 Foomatic/foo2xqx (recommended)

It won't print.  I'm sure the printer works (on a different machine), the usb must be OK because it recognized what it was?  What am I doing wrong?

Thanks

---

### Post by cariboo on 2008-10-15
Your printer is well supported in Linux you may need to install the hplip-gui to tweak the settings. Hplip-gui is in the repositories and you can use Add/Remove Programs, Synaptic Package Manger and of course the command line to install it.

Jim

---

### Post by clacroix on 2009-10-21
Hi.

You also possibly need to run [FONT="Courier New"]hp-setup[/FONT] utility as superuser in order to download proprietary HP firmware needed to drive the printer. Worked for my HP P1505 under Ubuntu 9.4.

---

### Post by wmstrome on 2011-04-11
My HP P1505 has quit working in Kubuntu 10.04 as well. Sometimes in the past, I have had to turn it off and back on, and even remove it and add it.

Today, I printed one document. I then tried a second. In the status, it said "Processing", then changed to "Stopped".  I powered off the printer and got it to print the second document. Now, nothing I do will make it work.

I tried installing hplip, and changed the driver to that, but that says it needs a plug-in to work. When I try to install it, it comes back with a message saying "Failed to install plug-in". I followed all the suggestions following that with no luck.

Has anyone succeeded in getting this (or perhaps any HP Printer) to work after the latest updates? If so, how?

Thanks.

Because I needed to print some things, I had to temporarily move the printer to a Windows system. I will move it back once I learn that this problem (either HP printer driver and/or hplip plug-in issue).

---

### Post by windfix on 2011-05-12
THANK you.  I had installed the gui and it was launching hp-setup, but not as root.  Sudo hp-setup did the trick immediately.

EDIT:  It only works until reboot, how annoying.  There is some proprietary plug-in required every time the printer starts.  The only way I can do this is to Uninstall HPLIP from Synaptic (complete), reinstall it, and run "sudo hp-setup" again - EVERY time I boot the machine.  Does anyone have a workaround?

The HPLIP website only has downloads for up through Ubuntu 10.10 right now, and I am on 11.04

> **clacroix said:**
> Hi.

You also possibly need to run [FONT="Courier New"]hp-setup[/FONT] utility as superuser in order to download proprietary HP firmware needed to drive the printer. Worked for my HP P1505 under Ubuntu 9.4.

---

### Post by windfix on 2011-05-20
I downloaded the .run file for hplip 3.11.5 here:  [http://sourceforge.net/projects/hplip/files/hplip/3.11.5/hplip-3.11.5.run/download](http://sourceforge.net/projects/hplip/files/hplip/3.11.5/hplip-3.11.5.run/download)

and did "sh hplip-3.11.5.run" (from the download directory).  This newer version supports 11.04.  Printer works, yet to see if it persists through a reboot.

Update:  It did persist through reboot, however if I send a print job without having powered on my printer first... OOOPs. stops working again, and I have to repeat the above.  

This printer is a lemon.  The key seems to be the proprietary plugin that loads during hplip setup.

You can install the plugin directly using the "sudo hp-plugin" command, however this does not resurrect my printer which is now crapping out every single day.  Time for a NON-HP printer

---

