---
title: "Network Printer Test Page Permission Denied"
date: 2021-05-13
forum: Hardware
---

### Post by penguin-fach on 2021-05-13
I have a small server, running 20.04 LTS with a minimal LXDE frontend. This has an HP Envy 5020 printer connected locally via USB and the printer works fine locally. The firewall is UFW and configured to pass CUPS, HPLIP and Samba. At present the printer is setup for sharing with all users. Samba will only be used for file sharing, not printer sharing. The server is connected to a small Wifi router.

I have several laptops, all running Kubuntu 20.04 LTS and I want these to be able to connect to the server over Wifi and print via the printer on the little server. Networking seems to be OK and both ends are talking properly. In each case the printer is detected fine and the drivers install OK. The printer shows as available but when I try to print the test page from any laptop I get 'Unable to open print file: Permission Denied'.

CUPS is installed and I have added the laptop users to lpadmin but I think there may be a CUPS issue. 'wiki.ubuntu.com/Security/Privileges' - 6. Configure Printers, indicates that the CUPS config file , /etc/cups/cupsd.conf, should have a SystemGroup entry assigning print permissions to the lpadmin group. However I have looked at this file and there is no SystemGroup entry.

I would appreciate it if anyone with more experience might have a look at this and advise if.

1. This looks like the likely problem.
2. The correct format for adding the SystemGroup directive to cupsd.conf

---

### Post by brian_p on 2021-05-13
> **penguin-fach said:**
> 

CUPS is installed and I have added the laptop users to lpadmin but I think there may be a CUPS issue. 'wiki.ubuntu.com/Security/Privileges' - 6. Configure Printers, indicates that the CUPS config file , /etc/cups/cupsd.conf, should have a SystemGroup entry assigning print permissions to the lpadmin group. However I have looked at this file and there is no SystemGroup entry.


The SystemGroup entry is in /etc/cups/cups-files.conf.

---

