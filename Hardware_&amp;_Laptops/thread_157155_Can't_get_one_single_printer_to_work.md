---
title: "Can't get one single printer to work"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by cerebro on 2006-04-08
I've installed Ubuntu on a spare PC we have here at our cybercafe in Panama, because I'm considering to move away from Windows and start using Linux instead, possibly with thin clients. 

In any case, I tried several distributions and found Ubuntu to be the easiest to work with. Connecting to the web went smoothly, everything works as it should work, the scanner scans, sounds play etc. etc.

Except for printing. I've spent two days on it now, but I can't get one of our printers to even print a test page. It's not the USB ports - they're fine. I found all the drivers and installed them as they should. In the add printer utility, the printers are even recognized and print jobs are queued to them. But no prints. The machines don't move.

I tried these printers:

Epson EPL 6200L
Kyocera FS1010
HP Deskjet 990 Cxi

I copied this from the error log:

[I]I [08/Apr/2006:20:22:58 -0400] Adding start banner page "none" to job 22.
I [08/Apr/2006:20:22:58 -0400] Adding end banner page "none" to job 22.
I [08/Apr/2006:20:22:58 -0400] Job 22 queued on 'EPL-6200L' by 'cerebro'.
I [08/Apr/2006:20:22:58 -0400] Started filter /usr/lib/cups/filter/pstops (PID 7776) for job 22.
I [08/Apr/2006:20:22:58 -0400] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7777) for job 22.
I [08/Apr/2006:20:22:58 -0400] Started backend /usr/lib/cups/backend/usb (PID 7778) for job 22.
E [08/Apr/2006:20:23:03 -0400] PID 7777 stopped with status 3![/I]

We also have a Canon i560 and a Canon Imagerunner 1310. Haven't tried these yet as they're constantly being used. 

Can anyone please tell me what I'm doing wrong?

---

### Post by Studymore on 2006-04-09
I have been having the same problem.  I did manage to get it to work for a short time using this command:

sudo chmod a+rw /dev/usb/lp0

This changes this permissions to the printer.  

You can view a similar thread at:

[http://www.ubuntuforums.org/archive/index.php/t-22871.html](http://www.ubuntuforums.org/archive/index.php/t-22871.html)

At this point, I am back to having the same problems.  The worst part about my printer is that the error log does not show an actual problem, but the printer just goes haywire and stops.  In any case, try to change the permissions with chmod, and see if it works for you.

---

### Post by cerebro on 2006-04-09
That did not help, unfortunately. I looked at the permissions of the file you mentioned as well as the usb files in usr/lib/cups/backend, but that's not where the problem is. I can't find anything in the drivers either that would cancel the print job, but maybe I'm overlooking it. 

I really didn't want to have a windows print server, but from what I read in other threads that seems to be the easiest way out of the Linux printing mess.

---

### Post by Studymore on 2006-04-10
In localhost:631, what is the status of your printer?  If it says "stopped, accepting jobs," you have a very simple problem.

In that case, you need to start the printer.  You may have to modify the printer administrator priveleges to do this.  

Working for many hours on a friend's computer recently, I found out that there was a simple fix of simply hitting the start button in managing printers at localhost:631.

Finally, after the chmod command, did you restart the CUPS server?

---

