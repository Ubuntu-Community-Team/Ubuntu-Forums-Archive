---
title: "Lexmark s405 printer"
date: 2013-05-21
forum: Hardware
---

### Post by mreyna16 on 2013-05-21
hey guys, i looked around to where to post this thread but since im a begginer i thought id post this here...

i have a Lexmark s405 printer and i have Ubuntu 13.04 x64 installed and cannot setup my printer. below is the website for the printer support in lexmark.com but if you see there the latest Ubuntu supported is 12.04 and installed those drivers (downloaded all three x64 packages and installed them). when i go into system settings>printers i see two printers set up and both with a red circle with a white exclamation point in the middle. can anybody help me setup my printer? thanks in advance

[http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_INTERPRET_S405&page=product&frompage=null#2](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_INTERPRET_S405&page=product&frompage=null#2)

---

### Post by mreyna16 on 2013-05-22
can anybody help on this?

---

### Post by kurt18947 on 2013-05-22
I am not at all familiar with Lexmark.  Maybe uninstall, reboot then reinstall?  You have two icons indicating problems.  What happens if you right-click one?  My version of Unity uses an informative version of 'printers'.  It will tell me quite a bit about the status or problems.  I also installed the  older-better  version of 'printers' for gnome-shell so that might be showing up in Unity as well, I'm not sure.  If right-click is informative, you have the better version.  If right-click doesn't really tell you anything you have the less desireable (IMO) version.

---

### Post by mreyna16 on 2013-05-22
yea im able to right click on the printers icon in settings

---

### Post by kurt18947 on 2013-05-23
When you right-click on the printers icon, what does the title bar say, "Printers"? or "printers-localhost"? The app I find more infomative is the one that says "Printers-localhost".  The newer app that just says "Printers" seems like it underwent a lobotomy ;).  I don't know which version the latest Raring has by default.  I don't know if you're aware of it but Lexmark is discontinuing the manufacture of inkjet printers this year and closing the supplies plant in 2015.  I don't expect much effort on the part of developers to make Lexmark inkjet printers work better.  If you want to spend the time, I think PCLinuxOS might have better Lexmark support.  When I had PCL installed, I recall seeing Lexmark packages that are not present in Ubuntu AFAIK.

---

### Post by mreyna16 on 2013-05-23
yea its the one that says printers-localhost, and i didnt know that... good thing im dualbooting windows but id like to depend on windows the least i can, ohh well hopefully theres a solution in the future

---

### Post by kurt18947 on 2013-05-24
Good, the one that says 'Printers-localhost' is more informative IMO.  When I right-click the printer icon, I can verify that Enabled & Shared are checked.  Left-clicking properties  -> settings shows things like Device URI & Make and model/driver in use.  Device URI should show something like usb://something assuming you're using a USB connection.   Policies list 'Enabled', 'Accepting jobs' and 'Shared'. All those are checked on my install.  Beyond that there's CUPS web admin pages but I'm mostly lost there.

---

### Post by MirrorUniverse on 2013-05-30
If you are still seeing two printers (assuming you only have one) I would delete both of them, reboot and reinstall like kurt18947 suggested.  Are you having a cups-insecure-filter problem?  [SIZE=2]I tried looking up a solution to Lexmark S405 printers and that seems to be a common problem.  If it is I can provide links to the pertinent threads.[/SIZE]

---

