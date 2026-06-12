---
title: "HP Device Manager Problem Ubuntu 6.06"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by Larry B on 2007-02-09
I'm using Ubuntu 6.06 and installed a HP D4160


When i launch HP Device Manager and try to configure the print quality it goes to a web page where when I change the setting - say to Draft - and then click the save setting button it prompts for a username and password. I enter mine and after a moment it pops back up asking for it again. Needless to say the setting doesn't get changed.

I found a tip that is supposed to address this issue:
See Issue #4 at [http://hplip.sourceforge.net/troubleshooting/other.html](http://hplip.sourceforge.net/troubleshooting/other.html) 

However, when i opened for edit the  /etc/cups/cupsd.conf file i discovered that the applicable lines wee already correct as suggested in the fix.

Anyone have any ideas on why then i still can not make changes using Hp Device Manager????

Thanks in advance all.  :)

---

