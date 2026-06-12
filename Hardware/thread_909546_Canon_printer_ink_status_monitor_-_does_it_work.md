---
title: "Canon printer ink status monitor - does it work?"
date: 2008-09-03
forum: Hardware
---

### Post by 2CV67 on 2008-09-03
Hi guys!

Canon (Australia) has the decency to supply Linux drivers for my iP4300 printer ( & others).
Thanks for that!  :)

They also include an Ink Status Monitor.

I can get to see it (by snappy terminal manipulations) but it only says "Ready" & never says it is printing or shows anything about the ink...

The instructions suggest it might not be exactly straightforward (see copy below) but I don't seem to get it working anyhow at all.
I assume item 6 is only for remote network printers? 
Mine is on USB to a desktop, in a wi-fi network but I am only trying to see ink status from the desktop machine.
The printer does not have an IP address.

Does anybody have the ink monitor working in Ubuntu?

Thanks for any information.

Copy of Instructions:
> 	

You can start the Status Monitor easily by creating a command shortcut to launch the Status Monitor on your desktop.

Restriction of the Status Monitor

1. The status is not displayed until printing starts.
If printing has not been started when the Status Monitor is started, only the "Ready" message is displayed because status information cannot be obtained.

2. The Status Monitor does not detect whether the printer power is off. If the printer power is turned off, the Status Monitor does not display a message that indicates the printer status.

3. If a non-root user who is not already logged in tries to start cngpij or the Status Monitor but does not execute xhost, the "cannot open display" message is displayed, and cngpij or the Status Monitor will not start. Therefore be sure to execute the "xhost [hostname]" command.

4. If the Status Monitor is started with a user privilege that differs from that of the user who executed the print job, the monitor can be started, but the status information related to that job cannot be obtained (the status remains "Ready").

5. The status is not displayed in the Status Monitor if printing is performed using the cif command.

6. The Status Monitor may not be displayed properly if the LAN environment has been configured and the IP address has been specified.
If such is the case, you must change the CUPS security setting.
Add the specified IP address in the following section in /etc/cups/cupsd.conf and restart the CUPS daemon.

<Location />

<Location /admin>

Example:

:
:
<Location />
Order Deny,Allow
Deny From All Allow From 127.0.0.1
Allow From XXX.XXX.XXX.XXX <- Add the specified IP address in this row.
</Location>
:
:
<Location /admin>
:
:
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From XXX.XXX.XXX.XXX <- Add the specified IP address in this row.
:
:
</Location>

Where, XXX.XXX.XXX.XXX is the specified IP address.

---

### Post by 2CV67 on 2008-09-09
Nobody?

I no longer need the "snappy terminal manipulations" now I have added a panel launcher for the Canon monitor, but otherwise no progress - still dumbly saying "Ready"...

:(

---

### Post by 2CV67 on 2008-09-27
Last request...

---

### Post by oldsoundguy on 2008-09-27
from my experiences, most ink monitoring programs go on the basis of page count, not what is actually in the cart(s).  The one for Epson IS a "sensor" but works only in Windows.  (I like the SSC service utility better as I use a waste ink recovery system to avoid that dreaded shut down to "get the printer serviced" message.  SSC has a reset utility!)
With HP, their utility is a page count.  If you use rebuilt carts that are filled over the usual HP 50% capacity on the stock carts, that blows their counter all to he**!
Of course, this is all in WINDOWS.
So the best way I have found with printers attached to Linux .. the Mark II eyeball.  Works great.
BUT, I do wish that the manufacturers would get off the dime and make better monitors for printers in the Linux system
Good luck on your Cannon .. at least it is a good printer and not a Lexmark!

---

