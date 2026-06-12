---
title: "Brother laser printer installation how to?"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by user_stu on 2005-04-01
hi all,

Just trying to get a 5140 working via USB... Ultimately I wanna use this printer via a Win XP machine over the network, but first things first...

I know little about linux

[B]Background

[/B]It is not listed under the printers that Ubuntu knows about.

I therefore tried adding a generic PCL 6 printer (which it is). (Note that first I had to install it as a non generic printer and then edit the driver to generic -- otherwise the "new" printer would not appear in my list of configured printers). Even after this the Print Test Page sends it to the queue but nothing happens. So I've given up on this for the moment.

Although Brother don't claim to support this particular model, a quick Google led me to:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de)

[B]Question
[/B]Do I just download the corresponding .deb file (because Ubuntu is Debian based???) and then open up a terminal window and  us the command
sudo dpkg -i --force-overwrite xxxx.deb*
*where xxxx.deb is the name of the DEB file.
?

If this is correct then I have a problem because I get the following error and have no idea what to do about it :confused: : 

-- please see attached file 

Regards
Stuart

---

