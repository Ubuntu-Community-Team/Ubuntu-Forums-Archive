---
title: "Printing over the internet?"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-08-13
I am a complete retard when it comes to configuring CUPS, so any help here is appreciated. What I want to do is set up one of my computers as a print server that will allow print requests over the internet. For example, so I can print to a printer in my dorm room while I am at home. I realize this will open up a security risk, so additionally, how can I limit access to the print server by using a username or password for the printer? Is this possible?

All I've tried so far is to open up /etc/cups/cupsd.conf and add:

ServerName my.server.net

but adding the printer to my Ubuntu laptop (running on a separate connection) did not allow me to print.

---

### Post by audax321 on 2005-08-14
Nice I got it set up. I just needed to add:

Listen <MY_LOCAL_IP_ON_ETH0>:631

to get cups to check that port for incoming print requests.

Also, I needed to edit:

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

and just add:

Allow From <THE_IP_ADDRESS_OF_THE_REMOTE_COMPUTER_PRINTING_TO_SERVER>


Now, the only problem that I would like to clear up is how to specify the IP addresses as words. For example, I would like to change 

Listen <MY_LOCAL_IP>:631

to:

Listen <MY_HOSTNAME_ON_ETH0>:631

and change

Allow From <THE_IP_ADDRESS_OF_THE_REMOTE_COMPUTER_PRINTING_TO_SERVER>

to

Allow From host.domain.net

(I already have a host.domain.net format address for the remote IP, but cups doesn't seem to resolve the hostname to an IP and always denies access if I try to connect.)

Thanks for any help...

---

