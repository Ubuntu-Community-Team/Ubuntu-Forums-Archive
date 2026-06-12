---
title: "Lexmark z55 printer for Dell A940"
date: 2008-10-18
forum: General Help
---

### Post by ant1060 on 2008-10-18
Hi!
Recently there was a CUPS update and now my Dell A940 (Lexmark x5150) has stopped working, although it was working perfectly before.

I have just reinstalled the z55 driver using these instructions adapted to my printer driver 
[http://ubuntuforums.org/archive/index.php/t-83456.html](http://ubuntuforums.org/archive/index.php/t-83456.html)

However, no test page prints any more and any document I try to print is sent to the printer, the icon appears in the task bar but disappears again after a few seconds. Nothing prints.
Any ideas please?

---

### Post by phidia on 2008-10-18
Try printing from a terminal using "lp" there hopefully will be more usable error output there.

---

### Post by ant1060 on 2008-10-18
@Phidia
Thanks for your reply but using the lp command does not elicit anything extra at all - it just gives a file ID number, the printer icon appears in the task bar and then disappears again. Nothing happens at all!

---

### Post by ant1060 on 2008-10-19
Nobody else lost their printer after the CUPS update of a few days ago??

---

### Post by rhiensch on 2008-11-03
Yes  after the upgrade to Ubuntu 8.10 (with old stuff removed). I reinstalled this driver according to instructions above. But this was not necessary. This old driver needs libstdc++5
This is not installed by default within 8.10. I installed this compatibility version and now it work again. You can check the driver with /usr/lib/cups/backend/z55
no output means OK

---

### Post by prinny42 on 2008-11-23
Sorry to revive a pretty old thread, but I'm having the same problem.  Whenever I try to print with my Dell A940, it just doesn't work.  The job starts to process and then just disappears.

I have z55 in the right place, and I've purged and reinstalled libstdc++5 just to be sure.  Nonetheless, I still can't get it to work.

Oddly enough, this problem didn't start when I first switched to 8.10 in early November.  I just printed something a couple days ago, but now...

I really have no clue what I'm doing here.  However, this is printed in my daemon.log and looks sort of relevant:

> Nov 23 15:12:02 compy hal_lpadmin: Running hal_lpadmin
Nov 23 15:12:03 compy hal_lpadmin: hal_lpadmin triggered by usblp kernel module
Nov 23 15:12:03 compy hal_lpadmin: Using device ID from HAL database entry
Nov 23 15:12:03 compy hal_lpadmin: remove
Nov 23 15:12:03 compy hal_lpadmin: Found configured printer: A940
Nov 23 15:12:03 compy hal_lpadmin: Disabled printer A940, as the corresponding device was unplugged or turned off
Nov 23 15:12:03 compy hal_lpadmin: Found configured printer: A9402
Nov 23 15:12:03 compy hal_lpadmin: Disabled printer A9402, as the corresponding device was unplugged or turned off
Nov 23 15:12:03 compy hal_lpadmin: Running hal_lpadmin
Nov 23 15:12:04 compy hal_lpadmin: hal_lpadmin triggered by low-level USB device
Nov 23 15:12:04 compy hal_lpadmin: Polling device ID from the printer
Nov 23 15:12:04 compy hal_lpadmin: Written device ID into HAL database entry
Nov 23 15:12:04 compy hal_lpadmin: remove
Nov 23 15:12:08 compy hal_lpadmin: Running hal_lpadmin
Nov 23 15:12:08 compy hal_lpadmin: Running hal_lpadmin
Nov 23 15:12:09 compy hal_lpadmin: hal_lpadmin triggered by low-level USB device
Nov 23 15:12:09 compy hal_lpadmin: Polling device ID from the printer
Nov 23 15:12:09 compy hal_lpadmin: hal_lpadmin triggered by usblp kernel module
Nov 23 15:12:09 compy hal_lpadmin: Using device ID from HAL database entry
Nov 23 15:12:09 compy hal_lpadmin: add
Nov 23 15:12:09 compy hal_lpadmin: URIs: ['usb://Dell%20/A940', 'hal:///org/freedesktop/Hal/devices/usb_device_413c_5103_17K045000040847_if1_printer_noserial']
Nov 23 15:12:09 compy hal_lpadmin: HPLIP Fax URIs: None
Nov 23 15:12:09 compy hal_lpadmin: Not adding printer: A940 already exists
Nov 23 15:12:09 compy hal_lpadmin: Re-enabling printer A940
Nov 23 15:12:09 compy hal_lpadmin: Not adding printer: A9402 already exists
Nov 23 15:12:09 compy hal_lpadmin: Re-enabling printer A9402
Nov 23 15:12:09 compy hal_lpadmin: Device 002:004: /org/freedesktop/Hal/devices/usb_device_413c_5103_17K045000040847_if1
Nov 23 15:12:09 compy hal_lpadmin: Stopping hal_lpadmin triggered by low-level USB device

The relevant printer is A9402.  I don't know; does this reveal anything?

Thank you.

EDIT:  Okay, I don't know what happened, but after unplugging my printer entirely (power, usb, everything) and plugging it back in it works.  Inscrutable things, printers.

---

### Post by waldek_poznan on 2008-11-28
I've got a solution for every printer in ubuntu 8.04 (printer icon disappears and nothing happens - printer doesn't print).
1. Remove/uninstall existing printer driver.
2. Unplug the printer's usb cable from your computer (crucial).
3. Turn off the computer.
4. Turn on the computer.
5. Turn on the printer then connect the printer usb cable to your computer.
6. The ubuntu system will recognize a new printer (a small printer icon in the tray).
7. Click on the printer icon and choose the correct printer (for me it was a canon pixma mp610 although I had a mp600).
8. Install the new printer driver.
9. Here you go. Check the printer - it will print just like before.
10. Don't thank me.
11. I don't need it.

---

