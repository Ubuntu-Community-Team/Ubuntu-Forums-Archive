---
title: "accessing ftp server over the web"
date: 2005-11-22
forum: General Help
---

### Post by Thymen on 2005-11-22
Hi folks,

I just installed proftpd as an ftp server, and in my network it appears to be working fine. I can access it from a windows machine using Smartftp client, using the IP address of my Ubuntu box, and the port I specified in the proftpd.conf file.

I used the info from the Howto on the Ubuntu Document Storage facility, great help. I opened a port on my router that is connected to my cable modem, set the passive ports as indicated in the user guide, all appears to be working fine.

But.... what if I wat to access the server from outside my network? I have the IP address the provider set for my cable modem, but if I use that IP + the ftp server name (like 123.456.789.123/ubuntu) to connect, I get a refusal.

How do I make my server available from outside? Any documentations somewhere? Any suggestions?

Thymen

---

### Post by soulestream on 2005-11-22
just use the IP address. 

check the ftp server logs, to see if it is denying the request or the router.

and hope your ISP isnt blocking FTP on your subnet ;) 

soule

---

### Post by ed_d on 2005-11-22
or try putty or something of the like.

---

### Post by Thymen on 2005-11-22
[QUOTE=soulestream] just use the IP address.
[/QUOTE]Did that, and any combination of IP/names/ports I could think of... same result

[QUOTE=soulestream] check the ftp server logs, to see if it is denying the request or the router.
[/QUOTE]no connection because machine is actively refusing it...

[QUOTE=soulestream]and hope your ISP isnt blocking FTP on your subnet ;) 
[/QUOTE]I am afraid this may be the case... I'll ask my provider...:rolleyes: 

Thymen

---

### Post by cmiz on 2005-11-22
do you mean that you forwarded the passive ports through your router as well as the port your ftp server is running on? i recall having issues of my ftp server not going through my router without some fine tuning with ports (D-Link router). 

if you have ssh installed, try forwarding port 22 through your router then connecting to your ubuntu box via port 22 with some sort of ssh client. that way at least you can find out if you're getting to your ubuntu box and if need be, could use sftp server functionality instead of the ftp server?

as for the hostname you're connecting to, the ports that get forwarded through your router do all the work of specifying the box that it goes to, attempting to connect to (your ip address)/Ubuntu or something like that will only further confuse things.

---

### Post by Thymen on 2005-11-23
I'll wait for info from my provider. I tried by opening all kinds of ports, putting the cmputer outside the DMZ, clising down the firewall (temporary,ofcourse), but to no avail.

Curious what my provider has to say. 

Thymen

---

