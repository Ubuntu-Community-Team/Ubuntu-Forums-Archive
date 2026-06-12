---
title: "[SOLVED] HP c6280 printer problems"
date: 2008-10-21
forum: General Help
---

### Post by jtmedin on 2008-10-21
Went to the HP site & found the linux driver for the c6280 printer. The printer is connected to my router & thus a network printer. Clicked on the file i had downloaded & spent considerable time while it loaded ... . Finally it asked me to unplug the network line & when i went on  it asked me to plug in the network cable. Screen showed the network printer so i highlighted the line & clicked next. Half an hour later it was still stuck. Tried it again & again  but no banana. What did i do wrong or ... . Anyone got any ideas? TIA

---

### Post by jtmedin on 2008-10-21
Well color me confused. Yesterday i spent a lot of time & only got a loop. Today i turned off the printer & unpluged the cable then ran the downloaded file again. Turned on the printer & connected the cable. Everything went as before but no loop & the divers installed & printer is working fine :)

---

### Post by Tictoon on 2008-10-21
where did you find the driver?

I have a Color LaserJet CP1215 that I need to install...

---

### Post by fballem on 2008-10-21
> **Tictoon said:**
> where did you find the driver?

I have a Color LaserJet CP1215 that I need to install...

Probably here, assuming that it was HPLIP that was installed: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Don't forget to check Synaptic and completely remove the existing HPLIP first before you run the downloaded file.

Detailed instructions can be found on one of the posts on this thread: [http://ubuntuforums.org/showthread.php?t=954546](http://ubuntuforums.org/showthread.php?t=954546)

---

### Post by Tictoon on 2008-10-21
> RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in
when you started this installer, you will need to either restart your PC or
unplug and re-plug in your printer (USB cable only). If you choose to restart,
run this command after restarting: sudo hp-setup (Note: If you are using a
parallel connection, you will have to restart your PC. If you are using
network/wireless, you can ignore and continue).

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) : p
Please unplug and re-plugin your printer now.  Press <enter> to continue or 'q' to quit:


PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
error: hp-setup failed. Please run hp-setup manually.
gagan@gagan-desktop:~/Desktop$ sudo hp-setup
[sudo] password for gagan:

HP Linux Imaging and Printing System (ver. 2.8.9)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
warning: Qt/PyQt 3 initialization failed.
error: hp-setup requires GUI support (try running with --qt4). Also, try using interactive (-i) mode.
gagan@gagan-desktop:~/Desktop$ -i
bash: -i: command not found
gagan@gagan-desktop:~/Desktop$ sudo hp-setup--qt4
sudo: hp-setup--qt4: command not found
gagan@gagan-desktop:~/Desktop$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.8.9)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
warning: Qt/PyQt 3 initialization failed.
error: hp-setup requires GUI support (try running with --qt4). Also, try using interactive (-i) mode.
gagan@gagan-desktop:~/Desktop$            

thats what happens, what do I do now?

---

### Post by fballem on 2008-10-21
> **Tictoon said:**
> thats what happens, what do I do now?

Try re-running the original file again and watch carefully. It looks like dependencies were not installed. These are installed as part of the installation process and reading the output from the original installation process should highlight any problems.

During the install process, it asked you for your password. I am suspecting that the password was not correct.

Try it and let me know. By the way, did you restart your computer?

---

### Post by Tictoon on 2008-10-21
I restarted my printer instead, I'll try restarting

EDIT: still not working

---

### Post by fballem on 2008-10-21
> **Tictoon said:**
> I restarted my printer instead, I'll try restarting

EDIT: still not working

Try the suggestion in Post #6 of this thread (re-running the installation program). I have a network printer. I'm assuming that you have a USB printer, in which case, I think you might need to disconnect it until you hit the point in the installation where it is asking you to connect it, then enter 'p'.

---

### Post by Tictoon on 2008-10-21
it worked, I LOVE YOU!

(like a brother)

EDIT: it won't find my printer

---

### Post by fballem on 2008-10-21
Restart your computer, with the printer plugged in. If that doesn't work, then assuming that your printer is plugged in (and yes, that's a joke), you should be able to open the hplip application and add the printer.

Check your menus to see if you can find an application called HPLIP Toolbox. Once you have it open, you should be able to follow the menu without any difficulty.

I'll take the love in the spirit with which it was intended - like a brother:lolflag:

---

