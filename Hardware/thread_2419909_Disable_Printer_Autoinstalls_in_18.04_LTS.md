---
title: "Disable Printer Autoinstalls in 18.04 LTS"
date: 2019-05-27
forum: Hardware
---

### Post by mdamda123 on 2019-05-27
Hi All,

I'm currently upgrading from 12.04 LTS. I'm not a total noob but I'm not very well versed in Ubuntu either.

I have a problem wherein network printers automatically are installed - and this is a problem as the organization has a LOT of printers, and shared printers are listed several times over (this is a different problem!) This wasn't a problem in 12.04 LTS.

I'd like to know how to disable the printers from installing automatically.

Based on a quick search, I have tried the following and with the following results:

1. Editing /etc/cups/cups-browsed.conf - initially disables the search of printers but will repopulate after a while
CreateRemoteCUPSPrinterQueues No
CreateIPPPrinterQueues No
RemoteBrowsing Off
BrowseRemoteProtocols none
BrowseLocalProtocols none
BrowseProtocols none
BrowseDeny All

2. Editing /etc/avahi/avahi-daemon.conf and inserting enable-dbus=no under [server]
This will work but attempting to print in LibreOffice will hang the computer for about a minute before the printer selection screen comes up. Removing this line will also fix the hanging issue.

3. Disabling avahi-daemon from starting up. Not sure if this is a good long term fix.

These are the most common resolutions I've found, but seem to be inadequate.

Is there anything I haven't tried but can do?

Many thanks!

---

### Post by slickymaster on 2019-05-27
Thread moved to **Hardware** for a better fit

---

### Post by mdamda123 on 2019-05-28
For anyone that has encountered a similar problem, I *think* I have resolved it by removing avahi-daemon.

(sudo) apt remove avahi-daemon

As for long term effects, I am not yet so sure.

Also, I don't think this should be in the hardware forum as I think this is primarily an OS issue.

Either way, thanks for looking :)

---

### Post by brian_p on 2019-05-29
> **mdamda123 said:**
> Hi All,

I'm currently upgrading from 12.04 LTS. I'm not a total noob but I'm not very well versed in Ubuntu either.

You are sufficiently versed to have done some research and to have explored some solutions on your own. Good. :D

> I have a problem wherein network printers automatically are installed - and this is a problem as the organization has a LOT of printers, and shared printers are listed several times over (this is a different problem!) This wasn't a problem in 12.04 LTS.

I'd like to know how to disable the printers from installing automatically.

This is a reasonable common request which one can have sympathy with. The difficulty of coming up with a viable and acceptable solution arises out of significant changes in CUPS and cups-browsed. The application being used to print from also has a bearing on the matter. For example, the Firefox and LibreOffice dialogs enumerate printers and print queues using different techniques.

[https://wiki.debian.org/PrintQueuesCUPS#Printing_and_GTK_Applications](https://wiki.debian.org/PrintQueuesCUPS#Printing_and_GTK_Applications)
[https://wiki.debian.org/PrintQueuesCUPS#Temporary_Queue_Creation_by_CUPS](https://wiki.debian.org/PrintQueuesCUPS#Temporary_Queue_Creation_by_CUPS)

> Based on a quick search, I have tried the following and with the following results:

1. Editing /etc/cups/cups-browsed.conf - initially disables the search of printers but will repopulate after a while
CreateRemoteCUPSPrinterQueues No
CreateIPPPrinterQueues No
RemoteBrowsing Off
BrowseRemoteProtocols none
BrowseLocalProtocols none
BrowseProtocols none
BrowseDeny All

These directives affect the discovery behaviour of cups-browsed but not that of CUPS. They also do not alter printer enumeration in the Firefox dialog. cups-browsed is effectively useless  for your intended pupose. It can be purged from the system. (But you could experiment with what BrowseFilter does for you).

> 2. Editing /etc/avahi/avahi-daemon.conf and inserting enable-dbus=no under [server]
This will work but attempting to print in LibreOffice will hang the computer for about a minute before the printer selection screen comes up. Removing this line will also fix the hanging issue.

The worst solution, IMO. It will degrade the system in all cases which do not use the GTK print dialog.

> 3. Disabling avahi-daemon from starting up. Not sure if this is a good long term fix.

avahi-daemon provides a public service announcement service. Think of the display boards at airports; you can have all of it or nothing. By removing avahi-daemon you have chosed "nothing". That's fine, but bear in mind that avahi-daemon also provides name resolution of *.local domains. Its absence will very likely not affect you because there are other ways of doing resolution. Removing avahi-daemon is, IMO, your only sensible solution.

---

