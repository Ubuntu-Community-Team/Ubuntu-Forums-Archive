---
title: "cups problem - missing files (printers.conf and classes.conf)"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by padraig on 2005-12-20
Hello

After a recent clean install to Breezy (on a machine that worked well with Warty) I have had a problem with printing. lpq/lpr/lpetc and other tools that want cups to be running aren't working. I've looked in var/log/cups/error_log and it tells me that it is missing two files:
> I [20/Dec/2005:19:14:08 +0000] Listening to 7f000001:631
I [20/Dec/2005:19:14:08 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Dec/2005:19:14:08 +0000] Configured for up to 100 clients.
I [20/Dec/2005:19:14:08 +0000] Allowing up to 100 client connections per host.
I [20/Dec/2005:19:14:08 +0000] Full reload is required.
E [20/Dec/2005:19:14:08 +0000] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [20/Dec/2005:19:14:08 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [20/Dec/2005:19:14:12 +0000] Listening to 7f000001:631
I [20/Dec/2005:19:14:12 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Dec/2005:19:14:12 +0000] Configured for up to 100 clients.
I [20/Dec/2005:19:14:12 +0000] Allowing up to 100 client connections per host.
I [20/Dec/2005:19:14:12 +0000] Full reload is required.
E [20/Dec/2005:19:14:12 +0000] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [20/Dec/2005:19:14:12 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [20/Dec/2005:19:14:16 +0000] LoadPPDs: Wrote "/etc/cups/ppds.dat", 4102 PPDs...
I [20/Dec/2005:19:14:16 +0000] Full reload complete.
E [20/Dec/2005:19:14:16 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.

I've tried to completely remove and reinstall cups-y things using synaptic. Any other suggestions for getting printing working?

cheers

padraig

---

### Post by 11hjpphty76lkjj on 2005-12-20
If someone else has replied sorry, it seems someone forgot to hit the go go gadget ubuntuforums high bandwidth button. (it's horribly slow for me right now)

Forgive me, but did you install a printer?  I believe the printers.conf is created when a printer is setup.  and if not try adding the printer directly into cups, to do that you'll need to turn off the authentication that ubuntu has turned on.

sudo gedit /etc/cups/cupsd.conf

change the section:

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System

to

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

#AuthType Basic
#AuthClass System

restart CUPS

sudo /etc/init.d/cupsys restart

then in your browser:

[http://localhost:631](http://localhost:631)

Click Printers, then add printer.  Follow the steps, try printing test page.

Hope this helps.

---

### Post by padraig on 2005-12-20
Thanks for the suggestion, but unfortunately that hasn't solved the problem. I still can't get to localhost:631 or use System -> Administration -> Printing. Thanks again for your suggestions.

/var/log/cups/error_log

now says:

> I [20/Dec/2005:20:32:27 +0000] Listening to 7f000001:631
I [20/Dec/2005:20:32:27 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Dec/2005:20:32:27 +0000] Configured for up to 100 clients.
I [20/Dec/2005:20:32:27 +0000] Allowing up to 100 client connections per host.
I [20/Dec/2005:20:32:27 +0000] Full reload is required.
E [20/Dec/2005:20:32:27 +0000] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [20/Dec/2005:20:32:27 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [20/Dec/2005:20:32:28 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4102 PPDs...
I [20/Dec/2005:20:32:32 +0000] LoadPPDs: No new or changed PPDs...
I [20/Dec/2005:20:32:32 +0000] Full reload complete.
I [20/Dec/2005:20:45:34 +0000] Scheduler shutting down normally.
I [20/Dec/2005:20:45:34 +0000] Listening to 7f000001:631
I [20/Dec/2005:20:45:34 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Dec/2005:20:45:34 +0000] Configured for up to 100 clients.
I [20/Dec/2005:20:45:34 +0000] Allowing up to 100 client connections per host.
I [20/Dec/2005:20:45:34 +0000] Full reload is required.
E [20/Dec/2005:20:45:34 +0000] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [20/Dec/2005:20:45:34 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [20/Dec/2005:20:45:35 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4102 PPDs...
I [20/Dec/2005:20:45:36 +0000] LoadPPDs: No new or changed PPDs...
I [20/Dec/2005:20:45:36 +0000] Full reload complete.
E [20/Dec/2005:20:45:36 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.
I [20/Dec/2005:20:50:21 +0000] Listening to 7f000001:631
I [20/Dec/2005:20:50:21 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Dec/2005:20:50:21 +0000] Configured for up to 100 clients.
I [20/Dec/2005:20:50:21 +0000] Allowing up to 100 client connections per host.
I [20/Dec/2005:20:50:21 +0000] Full reload is required.
E [20/Dec/2005:20:50:21 +0000] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [20/Dec/2005:20:50:21 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [20/Dec/2005:20:50:21 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4102 PPDs...
I [20/Dec/2005:20:50:22 +0000] LoadPPDs: No new or changed PPDs...
I [20/Dec/2005:20:50:22 +0000] Full reload complete.
E [20/Dec/2005:20:50:22 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.


---

### Post by 11hjpphty76lkjj on 2005-12-20
Hmm what happens when you do 

sudo /etc/init.d/cupsys restart ?

Sounds like cups is broken, you may need to try compling it and installing it that way. via the cups website.

[http://www.cups.org/](http://www.cups.org/)

You should be able to get to the localhost:631, even without changing the cupsd.conf.  If you can't..CUPS is probably broke. Darn CUPS anyway.

What sort of printer are you trying to setup anyway?

---

### Post by padraig on 2005-12-20
Hello again, thanks again for trying to help.

It tells me [ok] when I restart cupsys:

sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

But, it doesn't show up when I ps -A.

Restarting it causes the error_log to be updated as in the previous messages.

I'll have a read on [http://www.cups.org/](http://www.cups.org/) and see if I can find anything useful. Thanks again for your help. Any further suggestions will be gratefully appreciated :-)

---

### Post by padraig on 2005-12-20
I decided that it might actually arise from a misconfiguration elsewhere... I couldn't get localhost:631 to work and then realised I couldn't ping localhost/127.0.0.1 either. So... I need to check my network interface configuration.

[http://www.ubuntuforums.org/showthread.php?t=12069&highlight=cups+127.0.0.1a=](http://www.ubuntuforums.org/showthread.php?t=12069&highlight=cups+127.0.0.1a=)


After I configure loopback, I can get System->Admin->Printers to load, etc.

I'm happier than I was :-) Expect me to appear in the networking forum shortly ;-)

Thanks for the assistance.

---

### Post by padraig on 2005-12-21
Just in case anyone pulls this thread up in a search... fixing the network configuration (specifically loopback) **did** solve my printing problem.

---

