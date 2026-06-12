---
title: "CUPS Server Error."
date: 2010-03-22
forum: Hardware
---

### Post by unsquaredance on 2010-03-22
Hi,
I use Ubuntu 9.10 on a lenovo T400. My printing seems to be suddenly broken. I connect to the network printer to print -- 
Using the printer configuration tool, I can connect to the cups server. However, clicking on Settings leads to the following error:

CUPS Server error There was an error during the CUPS operation: ''.

I can find my desired printer, and opening Printer Properties for this printer shows a
"Conflict" with the following message.

There are conflicting options.
Changes can only be applied after
these conflicts are resolved.

2-Sided Printing
Duplex Unit


However, I am unable to change these settings -- If I change and apply, I get the following error message:

CUPS Server error
There was an error during the CUPS operation: 'client-error-forbidden'


I wonder if anyone else has faced this problem, or better still knows how to fix it. 

Thanks in advance,
R.

---

### Post by snowfire22 on 2010-06-07
yep, I'm having the problem also. Things work working on June 4 but not June 7. I didn't explicitly make changes to my config.  I'm trying to print to a printer on a mac.  The mac is sharing. I can force a test page to work from Linux by Server/Connect/"machost.local". My printer then shows and "Print Test Page" works from the printer Settings dialog..  But Apply and Ok are disabled.  Can't seem to save the config.

---

### Post by snowfire22 on 2010-06-08
I got mine working:
  sudo service cups start

got hint from the Printer dialog, Troubleshooting button. It referred to the main menu: /System/Administration/Services which doesn't exist in 9.10 but the following set me straight
[http://blog.ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html#comment-2888](http://blog.ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html#comment-2888)

Don't know why my cups services stopped or if it will be there after next reboot.

---

