---
title: "brother mfc 5440 CN does not print with  ubuntu 8.10"
date: 2008-11-03
forum: Hardware
---

### Post by HorstJENS on 2008-11-03
after upgrading from ubuntu 8.04 to 8.10 my brother mfc 5440 CN printer (LAN, not USB) is no longer visible in the printer dialog.
I re-installed the packages:

[LIST]
[*]brother lpr drivers extra 
[*]brother cups wrapper extra
[/LIST]
without visible success.
I can not create a new printer with the system-settings-printing dialog because the menu item is not selectable.
Anyone got the brother mfc 5440 cn to print with ubuntu 8.10 ?

---

### Post by brucewestfall on 2008-11-08
Sure wish I could help you, but I'm stuck too.  

I have a Brother MFC665CW multifunction printer, scanner, etc., that has worked well for the last year, but now does not want to print after an upgrade to 8.10

Everything appears OK - the printer shows up as being installed, but once a print job is sent the display on the printer says "Receiving Data" but never coes anything.  No errors are displayed, but i did run the troubleshooting found at:
(Menu bar) System/Administration/Printing: Printer configuration
(Select Printer, then menu) Help/Troubleshoot

It let me save a debug file that makes no sense to me, but at least I've got something!
[http://www.brucewestfall.com/brother_mfc665_printer_troubleshoot.txt](http://www.brucewestfall.com/brother_mfc665_printer_troubleshoot.txt)

Can anyone see where the problem is?  Sure would be great to print again.

---

### Post by volker-j on 2008-11-16
Hi,
I have the same problem with the MFC-7440N

Ubuntu find the printer,
CUPS find the Printer

But it does not print !

Volker

---

### Post by brucewestfall on 2008-11-16
Try following the steps on the Brother Website.
[http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)

Brother has had Linux support for several years now.
Please note this post is Nov 2008 - if you are reading this later, the problem may no longer exist...

I also posted this info at
[http://ubuntuforums.org/showthread.php?t=978802](http://ubuntuforums.org/showthread.php?t=978802)

---

### Post by zbeckerd on 2008-11-28
My printer is 3340 CN  I have followed these instructions and so far this has not been a fix for me.  

Doing this level of fixing is why linux has not been adopted.

My printer is and was seen by cups and system.  So just to make sure I am going to reboot after applying this fix.

I set up this printer originally in 6.06 by following instructions here on the forum.  I did a install of 7.10 on a new disk and it carried my printer over from the 6.06 install (which was great).  I also did a new install of 8.10 by buying a new drive (my preferred method) and installing.  Cups seemed to know the printer was there but I still had to configure.  

When I send a job to the printer the printer shows it is receiving data then goes back to waiting for a job.  The job disappears from my printer Que, but it never prints.  I ran puppy from a live cd and it printed perfectly.

Well off to reboot.  I will return and update my comments...

Reboot did not work.  Will go through the process again to see if I somehow missed something.

---

### Post by albandy on 2008-11-28
If this one is postscript compatible try using the C410DN driver

---

### Post by zbeckerd on 2008-11-28
> **albandy said:**
> If this one is postscript compatible try using the C410DN driver

That worked for me!  Thanks

Also I set it up via cups but it would probably work using the add printer.

For those who may not know how to set up a printer in cups...

[http://localhost:631/printers/](http://localhost:631/printers/)

Copy that into your browser and click add printer and follow the directions.

I just started roasting my own coffee, so a cup to you!

PS it was the mfc410cn driver in my list

---

### Post by brucewestfall on 2010-05-10
Please go to the brother website and follow the instructions EXACTLY.  Make sure you remove any copies of the printer you have already tried to install the wrong way.

I highly recommend Brother Multifunction printers!

If you go directly to the Brother website and follow the instructions, it should only cost you about 10 minutes.  I have spent FAR more time waiting to get Windoze reinstalled with all the key codes you must have.

If MS had not dumbed us all down, we would still feel comfortable TYPING with our computers.

Go to the shell (command prompt) and TYPE.  

Is that so hard?  

Before you flame me, think about how much you use the keyboard every day.  Use google, look it up and learn where to type things.

How much does Vista cost????

---

