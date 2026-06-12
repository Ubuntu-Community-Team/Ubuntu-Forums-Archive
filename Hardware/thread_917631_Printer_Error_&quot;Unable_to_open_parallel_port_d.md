---
title: "Printer Error &quot;Unable to open parallel port device file: Permission denied&quot;"
date: 2008-09-12
forum: Hardware
---

### Post by PrestonFrom on 2008-09-12
Hello and good evening (or morning...or afternoon...or...)

I'm trying quite desperately to get my printer to do what it's supposed to do: namely print.  I have an Epson Stylus CX8400 (one of those fancy all-in-one deals).  I found a great thread ([http://ubuntuforums.org/showthread.php?t=822003&highlight=epson+stylus+cx8400](http://ubuntuforums.org/showthread.php?t=822003&highlight=epson+stylus+cx8400)) that helped me get the damn thing installed and running...until I restarted my computer.  The scanner still works.  But now my printer doesn't seem to be receiving the print message (or whatever the proper terminology would be).  Instead, if one clicks on the little print icon in the top right hand corner, one can see that all my print jobs' statuses are: Held.  Clicking release means that they will be re-processed and then, again, held.  Additionally, CUPS (and the print screen for Firefox, oddly enough) have a message after the  name of the printer that reads: "Unable to open parallel port device file: Permission denied".

I'm baffled, to be honest.  I've uninstalled and reinstalled everything I can think of.  I've gone through the previously mentioned thread and undone (and then redone) everything mentioned.  The scanner still works (which is nice, I suppose), but I'd really like to be able to print!  I sometimes get a cups error message as well (but I don't have it on hand).  I'm assuming this is a CUPS issue, but I can't figure out what.  I've played around with CUPS and permissions, but nothing seems to work.

So, anyway, HELP!

Thank-you so much!
Preston

---

### Post by jhodges on 2008-09-24
I had a similar issue with my cx4800 - it started happening after i installed sane to access the scanner.

turns out the sane install modified the group of 

/dev/usb/lp0

it was

$ ls -lrt /dev/usb/lp0 
crw-rw-r-- 1 root lp 180, 0 2008-09-24 21:03 /dev/usb/lp0

but after the sane install it was

$ ls -lrt /dev/usb/lp0 
crw-rw-r-- 1 root scanner 180, 0 2008-09-24 21:03 /dev/usb/lp0

I changed this back and could print, but this might break the scanner, so I ended up adding the lp user into the scanner group.. sudo vim /etc/group

that didn't work though.. so for the meantime, i'm leaving the group of /dev/usb/lp0 as "lp" until I can figure it out.

---

### Post by jhodges on 2008-09-24
ahh, sweet. the scanner still works. all you have to do is this: sudo chown root.lp /dev/usb/lp0

---

### Post by PrestonFrom on 2008-09-27
Thank-you!!!

I just tried it, but it says it doesn't exist?  I'm going to do some digging around in my computer now, see if I can't find it.  I'm not at home though, so I won't know if it actually fixes anything or not for about a day...but I'll let you know if does or doesn't!

And, again, thank-you for the help!!!

---

