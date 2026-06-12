---
title: "Modem not connection to 56k"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by phil66 on 2006-02-08
I have installed Ubuntu 5.0.4 to a duel boot system with Windows ME
My modem is dial up Zoom 3049c serial external 56K v90/v92 v44
It connects to the net but does not show 56k light the connection is slow indicating a low speed,
Windows still connects at 56K

How do I get it to connect at 56K

Thanks
Ray

---

### Post by phil66 on 2006-02-09
This was a software problem
Configured PON 
Bandwith now 43.5kpbs as compared to 4.6lpbs
Ray

---

### Post by Aliby on 2006-03-08
[QUOTE=phil66]This was a software problem
Configured PON 
Bandwith now 43.5kpbs as compared to 4.6lpbs
Ray[/QUOTE]
Can you elaborate please. I have the same situation and it look slike I can only connect at 9800pbs (looks alot like a baud rate to me) instead of around 56kpbs.
How do I configure PON?

---

### Post by phil66 on 2006-03-08
Hi Aliby

After installing Hoary 5.04 I tried using the network panel to login. The login showed to be sucessful but the bandwith was at 4.6 kpbs. I disabled the network panel and configured pon and the bandwith came up to 43.5 kpbs.

In Hoary 5.04 from a terminal type "sudo pppconfig" without the quotes.
A panel will open and guide you through the required information for your system.

To login using pon from the command line type "pon" and to logoff type"poff" without the quotes.

In Breezy 5.10 I installed gnome ppp from the synpathic package manager.
I then opened it from the internet header and configured.

The gnome ppp looks very similiar to Kppp in Kde desktop. I prefer it but don't know if its available in Hoary as I now have breezy installed.

Hope this helps
Ray

---

