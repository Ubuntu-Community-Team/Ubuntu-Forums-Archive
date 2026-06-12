---
title: "Problem with CUPS"
date: 2008-10-28
forum: General Help
---

### Post by porchrat on 2008-10-28
Hi all I'm back once again with yet another problem (just doesn't stop does it).

I've been trying to setup CUPS so that I can print to a printer on our LAN.  However I can't seem to get it right.  I know the IP address of the print server and I can ping it no problem, I've tried using both ipp and lpd URI's and haven't had any success.

Is there anyone out there who can offer some advice or better yet, a solution?

The printer is a HP Laserjet 3030 and it is connected to a print server.

---

### Post by porchrat on 2008-10-28
To further clarify I have attempted to add the printer through a web browser as opposed to through the console.  After I have added the printer I go to the "printers" menu and it says this:

"recoverable: Network host 'print_server_IP_address' is busy; will retry in 10 seconds..."

Only the IP addresses have been changed to protect the innocent.

EDIT: also the URI I'm using is: lpd://server_ip_address/queue

---

### Post by porchrat on 2008-10-28
Nevermind all I got the thing working.  Used a "socket" URI with Jetdirect and it worked straight away.

No worries, maybe this will help someone in the future :)

---

### Post by Rayaz on 2008-10-28
Could you please try out a static IP address too. I got mine working that way, wondering if I was right.

---

### Post by porchrat on 2008-10-28
> **Rayaz said:**
> Could you please try out a static IP address too. I got mine working that way, wondering if I was right.

My whole network runs on static IP's.  I hate DHCP as I would have to reconfigure all of my carefully orchestrated and highly specific (bordering on paranoid) firewall pinholes if the IP's kept changing.

---

### Post by porchrat on 2008-10-28
OK got another problem.  Used the same CUPS setup on another ubuntu machine on the network (a laptop running wifi) and while it is communicating with the printer (printer prints when the machine sends a job through), the printer only prints garbage.

When I attempt to print a CUPS test page I get a line of dashes on one page followed closely by another page with this:

"? n n n %n followed by heart symbols and a symbol with 3 parallel lines then LLLL? three parallel lines Ln n"

What the heck is going on?

---

### Post by porchrat on 2008-10-29
to bump or not to bump that is the question

---

