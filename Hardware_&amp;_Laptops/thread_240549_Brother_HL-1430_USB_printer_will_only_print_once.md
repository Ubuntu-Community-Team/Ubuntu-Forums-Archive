---
title: "Brother HL-1430 USB printer will only print once"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by peterbutler on 2006-08-21
I have a Brother HL-1430 printer connected via USB to a PC running Ubuntu 6.06 with all updates installed.  The printer will print the first document I send to it perfectly, but any subsequent documents are held in the queue and not printed.  The status in the printing applet is shown as "job-printing".

I set the log level in /etc/cups/cupsd.conf to debug, and /var/log/cups/error_log now shows the following (trimmed):

D [21/Aug/2006:17:11:32 +1200] [Job 113] End of page header
D [21/Aug/2006:17:11:32 +1200] [Job 113] Stopping search for page header options
D [21/Aug/2006:17:11:32 +1200] [Job 113] Found:
D [21/Aug/2006:17:11:32 +1200] [Job 113] ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff
D [21/Aug/2006:17:11:32 +1200] [Job 113] --> Output goes directly to the renderer now.
D [21/Aug/2006:17:11:32 +1200] [Job 113]
D [21/Aug/2006:17:11:35 +1200] cupsdReadClient: 6 POST / HTTP/1.1
D [21/Aug/2006:17:11:35 +1200] cupsdAuthorize: No authentication data provided.
D [21/Aug/2006:17:11:35 +1200] CUPS-Get-Printers
D [21/Aug/2006:17:11:35 +1200] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)

The last set of messages (about the authentication) are repeated every 10-30 seconds.

The output of lpstat gives:

# lpstat -a -p
HL-1430 accepting requests since Mon 21 Aug 2006 17:11:32 NZST
printer HL-1430 now printing HL-1430-113.  enabled since Mon 21 Aug 2006 17:11:32 NZST
        Printer not connected; will retry in 30 seconds...

This setup worked perfectly under Breezy (and other Linux distros such as Fedora Core 2), so I know there is no problem with the hardware.  Does anyone have any idea as to how this can be fixed?

As a side note, this seems to have happened to other people as well: [http://www.ubuntuforums.org/showthread.php?t=222157](http://www.ubuntuforums.org/showthread.php?t=222157)

Cheers

Peter

Update: I have also tried the following:
- Added cupsys to the "shadow" group
- Changed "Browsing" to "on" in /etc/cups/cups.d/browse.conf
- Changed all "deny, allow" lines in /etc/cups/cupsd.conf to "deny, allow"
- Changed permissions on /dev/lp0 to 777

I restarted cupsys (using /etc/init.d/cupsys restart) after each of these changes but the printer will still not print anything after the first job I send to it.  I've also tried restarting via localhost:631 but no result.

I've also noticed that disconnecting the USB cable and reconnecting it causes all pending jobs to be printed.  Does this point to a USB/udev problem rather than a CUPS problem?

Cheers

Peter

---

### Post by encompass on 2006-08-21
I can second that... But after I updated my computer, wether it fixed it or not, it fixed my problem.  I was running the brother hl-1240 printer.  I would as you say unplug it from the usb and it would work again.  If you have a printer port... try that one to so we can try to document the problem.
Thanks for posting.
I did none of the fancy things that you did.
Are you using more than one user at a time?  I do.  Maybe there is some relation between our problems.

---

### Post by peterbutler on 2006-08-21
Thanks for your reply.  Sorry, I'm not sure what you mean by "after I updated my computer".  Do you mean that the problem was fixed after updating via the update manager?  I have applied all current updates but I am still seeing the problem.

Good point about using a parallel printer cable.  I've tried this and it works fine, so it looks like a problem in the interaction between CUPS and USB.  At least I can print now, although I would like to get USB working as well.

---

### Post by encompass on 2006-08-21
Yeah... I just updated my computer and everything started to work fine... infact my post on it is somewhere still on this forum.
[http://ubuntuforums.org/showthread.php?t=211879&highlight=HL-1240+print](http://ubuntuforums.org/showthread.php?t=211879&highlight=HL-1240+print)
Don't know how else to help you.  Do you use multiple users... it could be that you have issues with that... as I remember katri being able to print perfect on her restricted account and my admin account gave me issues.  Weird huh?
Try printing like twice in a row fast... and then try printing 5 minutes apart... it may have something to do with the timing.
I am just swinging, trying to help.

---

### Post by peterbutler on 2006-08-21
Very strange.  I'll try running as another user and see if that fixes things.    If it works it seems like a permissions problem rather than CUPS?

---

### Post by AlterEgo on 2006-08-27
Just a "me too". I believe it's not a cups-issue. I have tried several ubuntu and debian version with the same outcome.

---

### Post by peterbutler on 2006-08-27
This same setup used to work under Breezy, it's only broken since I installed Dapper.  I have resolved it for the moment by using a parallel cable instead of the USB cable.

---

### Post by bananabob on 2007-02-12
Just want to point out that this problem is still there in Edgy. I have an hl-1430 and it will only print once. If I unplug the USB cable and replug it it works for the next item in the queue.

Anyone got a fix for this yet?

---

### Post by sheilnaik on 2008-02-04
I want to bump this topic because I'm having the same problem with my Samsung ML-1710 laser printer.  I can print one document fine, but any subsequent documents require me to turn off the printer and turn it back on.  Anyone have any solutions?

---

### Post by bananabob on 2008-02-04
here is what I did to fix the problem
[http://linux.eaton.net.nz/?p=28](http://linux.eaton.net.nz/?p=28)

---

