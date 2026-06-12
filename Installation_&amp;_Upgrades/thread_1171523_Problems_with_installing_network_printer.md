---
title: "Problems with installing network printer"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by mehegelund on 2009-05-27
Hello

I'm new, installed Ubuntu 9.04 a week ago on a new harddesk with dual boot to either Ubuntu or XP.

Everything is working fine and startup is pretty fast !!!

I'm having problems installing my printer: Canon i865 installed as a network printer to my NAS Qnap TS-109 through USB. 

This works fine in XP for me and the rest of the family (running XP) even though Canon i865 is not a network printer, but I can't make it work i Ubuntu...

In XP the printer is known as \\NAS\NASPR, NAS is the name of the NAS (surprise!!!) , NASPR is the name of the printer (more surprise!!!). 

I have tried all of the options under New printer -> Network printer...
I can find the printer and install the driver, but when trying to print a test page I get the message that the printer is not connected.

I can connect to folders on the NAS without problems (well, a very little problem, I'm being prompted for a password, but choosing cancel opens the folder !!!)

I have searched this forum but haven't found any having a problem like mine  :-(

Anybody having good ideas about solving this printer problem ???

---

### Post by mehegelund on 2009-05-27
Tried Help -> Troubleshooting under Printers.

Created this report:
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.1.50', 'remote_server_name': 'NAS'}
Page 5 (Check network server sanity):
{'remote_server_name_resolves': False, 'remote_server_try_connect': 'NAS'}
Page 6 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'da_DK',
 'user_locale_messages': 'da_DK'}

What does it mean ?

---

