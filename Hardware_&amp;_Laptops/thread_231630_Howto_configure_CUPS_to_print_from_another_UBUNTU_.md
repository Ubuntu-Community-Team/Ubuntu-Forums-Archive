---
title: "Howto configure CUPS to print from another UBUNTU machine"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Smeuf on 2006-08-07
I am currently for the first time installing UBUNTU as a server on my local network using CUPS as printer server for the attached HP Deskjet 5550.
I followed the directions in the UBUNTU Server Guide and also looked at the directions in the Server section (ch 19) of the Unofficial Ubuntu 6.06 Starter Guide.
The installation went fine and I am able to print testpages from the server.
However the server cant be contacted from my UBUNTU pc attached to this network and printing from the only remaining Windows XP machine is not possible.
The lpq command at my UBUNTU desktop leads to the message "Unable to connect to server".

The CUPS config file is printed below:
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock

Can anyone tell me what I am missing, forgetting or doing wrong.
Please in a simple straightforward way as I am a Linux/Ubuntu newbee.

Thanks in advance for your trouble.

---

### Post by Matchless on 2006-08-12
Hi,
    This is what I was given and it solved my problem:
On the server, open the terminal and run:
sudo /usr/share/cups/enable_browsing 1
sudo /usr/share/cups/enable_sharing 1

Also check that you have the latest cupsys installed - version 1.2.2
Hope it helps you

---

### Post by vkohli on 2006-08-19
Smeuf,

If I understand you correctly you have installed the Ubuntu server and you want to print from Ubuntu server to a printer located on another Ubuntu box. Right? If so I have managed to print from my Ubuntu server to another Ubuntu box. This is how I did it.

First I will assume you already have the printer installed on your other machine. Make sure you know the ip address and the name of the printer you installed. 

As you already know to install a printer you must have the base cups packages installed. I assume you have these installed (i.e. cupsys, cupsys-bsd and cupsys-client).

First you have to add yourself to the lpadmin group. To do so type in terminal:   sudo adduser username lpadmin 

Since your printer is attached to another box, and assuming you are not using samba to print to the printer, than you must modify your cupsd.conf file to include this line:

FileDevice yes

To install a new printer run the lpadmin command:

lpadmin -p (printer name) -E - v [http://ip_address:631/printers/printer_name](http://ip_address:631/printers/printer_name)

You should now be able to print. Type lpq -p printer_name to see the status. 

If you still have problems it is likely that you have either a firewall for which you have not allowed traffic through port 631 (port cups uses). Or, in your cupsd.conf file of your box which the printer is connected too you have not commented out Listen localhost:631. You have to comment this out and add the syntax Port 631 to the /etc/cups/cups.d/ports.conf file. Make sure you have specified Include /etc/cups/cups.d/ports.conf in your cupsd.conf as well. 

As for the browsing. Browsing should be enabled on the machine which is running the printer. Check to make sure that /etc/cups/cups.d/browse.conf  has the statement Browsing on in it. 

If you had to make changes to the cupsd.conf file make sure you restart the daemon (i.e. sudo /etc/init.d/cupsys restart) 

If you are running a firewall on either box make sure you have allowed service for port 631. 

Hope this helps.

Cheers,
Vkohli

---

### Post by shanepardue on 2006-10-16
[QUOTE=Matchless;1372525]Hi,
    This is what I was given and it solved my problem:
On the server, open the terminal and run:
sudo /usr/share/cups/enable_browsing 1
sudo /usr/share/cups/enable_sharing 1

this worked for me..also accessing cups' web-based utility allows for this command through a gui.

---

### Post by aparsons on 2006-11-06
If i wanted to print between two ISPs - how would I secure cups to only accept connections over ssh?  Can I even send print jobs to a remote ubuntu machine on a different ISP via ssh?

thanks.

---

