---
title: "Network Drives?!"
date: 2010-08-17
forum: Hardware
---

### Post by kaspar_silas on 2010-08-17
Hi,

Bit baffled right now. In a nutshell my inquiry is "How the hell do you use a network drive on Linux"? 

To elucidate a little:
I have a WD World Edition which I plug into my network card 
(configured and normally working as a gateway)
The drive lights up and all seems happy. However the very useful supplied instructions do not give anything other than screens shots and buttons relating to shiny buttons to press on the software for Macintosh and Windows.

I guess then I have to mount it or samba mount somehow. Alas this isn't the easiest think to work out. Plus how? I didn't set an ip for it so how does it know where it is. Do I have to alter my network to be DHCP just for the network drive? And if I do do that is there an equivalent of the "Finder" application on Mac

Any help or nods in appropriate directions greatly appreciated.

---

### Post by kaspar_silas on 2010-10-25
Just in case it helps anyone else I worked out how to set it all up. 
Here is the procedure I followed.

1/ Turned on dynamic ip assignment ( dhcp ) on my LAN.
2/ Plugged in the network drive.
3/ Scanned the network and got the network drive's assigned ip
4/ Typed the ip into firefox and signed into the drive using the info that came with it.
5/ Searched the options settings and activated ssh and ftp
6/ Selected static ip and set it at say 192.168.3.200
6/ Added a new admin user and password for when I lose the instructions.
7/ Edited /etc/hosts adding 
192.168.3.200 networkdrive
8/ On the desktop Clicked Places->Connect to Server.
9/ Selected 
ssh 
server: networkdrive
user: [the new user I set up]
10/ Entered the password and selected remember for ever.
 
Viola a mounted and setup network drive :-)

---

