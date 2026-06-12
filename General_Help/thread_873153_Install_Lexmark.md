---
title: "Install Lexmark"
date: 2008-07-28
forum: General Help
---

### Post by jakespet on 2008-07-28
Can someone give me some help on how to install my Lexmark z25-z35 printer on Ubuntu 8.4?  I'm fairly new to Ubuntu but I know there's a way to do it.
Thank you.
R Howard

---

### Post by gobbles414 on 2008-07-28
Printer drivers in Ubuntu have matured a lot in the past couple of years. Installing many mainstream printers used to require lots of manual configuration. But today, chances are good that your printer will automatically be recognized. Try this:

* Turn your computer off
* Connect your printer to a USB port on your computer that you're sure works.
* Turn your printer on, and then turn your computer on.
* Log into Ubuntu.
* Go *System => Administration => Printing*. You should see a category in the left column called *Local Printers*.
* In Local Printers, you should see a virtual PDF printer. Hopefully, your Lexmark printer is also in the list.
* If your printer is in the list, click on it and then use the tabs to configure it.
* If your printer is not in the list, click the *New Printer* button. A new list will appear. Your printer may be listed here.
* If your Lexmark isn't listed, choose USB and then go to Lexmark in the list of manufactures.
* Your exact printer may not be listed in the Lexmark drivers list. Try a few of the model numbers which are closest to your printer, until you find one that works.

Let me know if this procedure succeeds for you.

---

### Post by nick_h on 2008-07-29
If you can't get it working then drivers are available from the Lexmark site.

I have written a howto for the [Lexmark Z55](http://ubuntuforums.org/showthread.php?t=803958) which may help.  It includes a link to the main Lexmark Printer howto.

---

### Post by LowSky on 2008-07-29
found this too
[http://ubuntuforums.org/showthread.php?t=4252](http://ubuntuforums.org/showthread.php?t=4252)

---

### Post by gobbles414 on 2008-07-29
> **LowSky said:**
> found this too
[http://ubuntuforums.org/showthread.php?t=4252](http://ubuntuforums.org/showthread.php?t=4252) Well that's discouraging... The very last post in that thread says that a solution which works in Feisty fails in Hardy.

I've found a possible solution at [http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25-z35]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25-z35"), but it may seem rather complicated to a newbie. It may still be worth taking a moment and trying the procedure that I posted in my original reply.

Jakespet, how much money is your time worth to you? I ask because depending on your situation and the success of the ideas we've given to you so far, it may be less of a hassle to just buy a printer that is known to work well in Linux. If you choose to purchase a new printer, consult [http://www.linuxfoundation.org/en/OpenPrinting]("http://www.linuxfoundation.org/en/OpenPrinting"). Be sure to read the entire entry for the printer you choose before you buy it; it would be unpleasant for you to buy an new printer only to have it fail to meet your expectations.

---

### Post by nick_h on 2008-07-29
> It may still be worth taking a moment and trying the procedure that I posted in my original reply.
Yes, this is certainly worth a try.

All the other methods involve converting rpm files extracted from the Lexmark drivers.  In my howto I convert them to deb files and install them.  I had no problems with the z55 drivers in Hardy.  I would ignore the discouraging post and try installing the z25-35 drivers anyway.

---

