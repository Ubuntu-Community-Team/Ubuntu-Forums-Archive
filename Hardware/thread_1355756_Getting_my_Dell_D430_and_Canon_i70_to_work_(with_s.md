---
title: "Getting my Dell D430 and Canon i70 to work (with solution)"
date: 2009-12-15
forum: Hardware
---

### Post by elbbit on 2009-12-15
Hello Ubuntu community!

I've found a solution to getting my Dell Latitude D430 laptop and Canon i70 printer working. I was going to reply to this forum post (but it's in an archive):
[http://ubuntuforums.org/showthread.php?t=458260](http://ubuntuforums.org/showthread.php?t=458260)

Another lead I got from this guy also recommends getting a commercial solution called TurboPrint:
[http://ubuntuforums.org/showpost.php?p=6317873&postcount=9](http://ubuntuforums.org/showpost.php?p=6317873&postcount=9)

I'm using Linux Mint:```
elbbit@dell ~ $ uname -a 
Linux dell 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
elbbit@dell ~ $ cat /etc/issue
Linux Mint 8 Helena - Main Edition \n \l
elbbit@dell ~ $
```

What I have ended up doing is this:
 - turn laptop on
 - turn printer on
 - connect the USB cable from laptop to printer
 - Ubuntu shows an icon... some disc activity occurs... moments later a screen appears asking for driver information
 - select the option for "Select a driver from database"
 - in the list choose "Canon" and press "Forward"
 - in the list on the left, choose "i450" and continue
 - when asked for test page, you can say yes, but mine came out all messed up
 - get into the Printer Configuration screen, and right click your printer to select the "Properties"
 - on the left, choose "Printer Options"
 - on the right, change "Resolution" to "600 DPI"
 - press "OK" and close all printer related screens.
You can now print your pages from OpenOffice or other program!

Mine works very well with the exception I appear to have gained 5mm margin at the bottom - which I can happily live with!

Karma to the developers and thanks for enabling me to enjoy free software!

elbbit

---

