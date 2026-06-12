---
title: "What am I not doing?  Cannon pixma ip2600"
date: 2009-02-15
forum: Hardware
---

### Post by RedPhoenix on 2009-02-15
Alright, I have a Cannon PIXMA iP2600 printer that is recognized by ubuntu, but I can not get it to print anything.  When I send print jobs to it, the light on it flashes like it is receiving the information, but nothing comes out and the paper is not even pulled into the printer.  I have read other threads that said to go to the openprinting site where I did all they posted with no change.  Any help will be appreciated since my wife is upset with me because the windows program crashed on me and I reloaded this machine with ubuntu.:lolflag:

No worries though, there are 4 other machines in my house that she can work on.

---

### Post by RedPhoenix on 2009-02-15
Can anyone help me out here?

---

### Post by hwttdz on 2009-03-02
You can try the instructions here:
[http://ubuntuforums.org/showthread.php?p=5337771](http://ubuntuforums.org/showthread.php?p=5337771)
let me know if it works, I'm considering that printer myself.

---

### Post by Cyber_Hack on 2009-03-18
I had the same problem with my Cannon IP2600.  It would blink but not print.
You need to go to 
[http://localhost:631/admin](http://localhost:631/admin)
This is "Common UNIX Printing System 1.3.7"  
Click on "Printers Tab"
Delete IP2600
Click on the Administraton tab
Click on "Find New Printers" button
You will now see Two Printers come up.
Cannon IP2600 and Guttenprint_USB_Printer_1
Choose either printer.  They both will work.  
Choose the "Printers Tab" and print out a test page.
Don't forget to keep the paper tray open before printing.
[http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by EGadZooks on 2009-10-09
<:Oo

I have never heard of [http://localhost:631/admin](http://localhost:631/admin) before
thank you for this
I did what you suggested, and it came down do the choice of the driver, so I picked what it wanted, the Canon i80 - CUPS+Gutenprint v5.2.3
and it didn't work.
I'm assuming its because of the canon i80 driver, so if anyone knows of any other drivers that work with the Canon iP 2600 series lemme know please thanks :OD

---

