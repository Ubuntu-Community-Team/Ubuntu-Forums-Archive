---
title: "How I installed my HP Networked printer"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by buddachile on 2005-08-31
In case this helps anyone, here's how I installed my HP printer.
  - 
The printer in question is an HP Laserjet 1320tn and is network enabled. For our purposes here let's say it is on my network at IP address 111.222.333.444.

1) I installed HPLIP:

[INDENT]  % sudo apt-get install hplip [/INDENT]

2) Generated a URI for use later on:

[INDENT] % hp-makeuri 111.222.333.444   [/INDENT]
  - 
The ouput of the command for me was:

[INDENT]  hp:/net/hp_LaserJet_1320_series?ip=111.222.333.444 [/INDENT]

3) Next I edited the /etc/cups/cupsd.config file (you can use gedit or vi) so that the cups web interface would not require a username/password to add the printer.  I commented out the two lines in <Location /admin> section:
[INDENT] 
AuthType Basic
AuthClass System 
[/INDENT]
changing them to:
[INDENT]
#AuthType Basic
#AuthClass System
 [/INDENT]

4) I then restarted cusp daemon so the changes would take effect:

[INDENT] % sudo /etc/init.d/cupsys restart[/INDENT]

5) Next I brought up the CUSP web intervace by pointing my browser to [http://localhost:631/](http://localhost:631/) and then followd the following steps:

[INDENT]
- clicked on: Printer -> Add Printer
  - typed in a name, location and description for the printer and clicked
    'Continue'
  - selected AppSocket/HP JetDirect for 'Device' and clicked 'Continue'
  - typed in the uri obtained in step 2) above in  'Device URI'
    (hp:/net/hp_LaserJet_1320_series?ip=111.222.333.444) and clicked
    'Continue'
  - Selected HP for printer make and clicked 'Continue'
  - Selected my HP printer model and clicked 'Continue'
[/INDENT]

5) At this point I was finished adding the printer so I undid the changes to the CUSP configuration file and made those changes take effect:
[INDENT]
  - I edited /etc/cups/cupsd.config, changing the following lines in <Location /admin> section:
[INDENT]
#AuthType Basic
#AuthClass System
 [/INDENT]
to
[INDENT]
AuthType Basic
AuthClass System
 [/INDENT]
  - I ran "sudo /etc/init.d/cupsys restart" for these changes to take effect
[/INDENT]

6) Now I can manage the printer by selecting (from gnome desktop)
   System -> Preferences -> HPLIP Toolbox


Hope this helps someone!

---

### Post by bobbear4u on 2005-09-04
I have an HP 1200dn.
I installed HPLIP.
HPIJS is the preferred driver says Linuxprinting.org
The hp-makeuri  command fails as follows:

IJS
vl
unable to read client data err=-4

I am calling this command from a root term
# /etc/hp
# hpijs

I cannot find a  HPLIP toolbox having been installed.
The printer works fine under Windows 98 and XP and is on the same network.

---

### Post by bjweeks on 2005-09-04
Thanks for this how to. I was just planing to get a HP neteork printer. :grin: Have you thought of puting this in the how to section?

---

### Post by buddachile on 2005-09-04
[QUOTE=bobbear4u]I have an HP 1200dn.
I installed HPLIP.
HPIJS is the preferred driver says Linuxprinting.org
The hp-makeuri  command fails as follows:

IJS
vl
unable to read client data err=-4

I am calling this command from a root term
# /etc/hp
# hpijs

I cannot find a  HPLIP toolbox having been installed.
The printer works fine under Windows 98 and XP and is on the same network.[/QUOTE]


I found an error in in original post (since corrected).  To install hplip type
[INDENT]sudo apt-get install hplip[/INDENT]
not
[INDENT]sudo apt-get hplip[/INDENT]

Also, make sure you can ping your printer to make sure it is on the network.  For that you'll need the printer's IP address.  For example, if the printer's IP address on your LAN is 192.168.0.10, type:

[INDENT]ping 192.168.0.10[/INDENT]

If you see something like this:
[INDENT]64 bytes from router (192.168.0.10): icmp_seq=1 ttl=127 time=2.13 ms
64 bytes from router (192.168.0.10): icmp_seq=2 ttl=127 time=2.13 ms
64 bytes from router (192.168.0.10): icmp_seq=3 ttl=127 time=2.12 ms[/INDENT]
then your printer is online.  You can press CTRL-C to exit out of the ping command.

After making sure your printer is on the network try the hp-makeuri  command.

---

### Post by S29K on 2005-09-22
I have installed my HP printer the same way as described and it works....for the most part.

Every time I boot up my computer I have to restart both hplip and cups for anything to print.  It works fine after that but it would be nice for the system to initialize the printing systems without having to open up the terminal and restart it.

Any idea how to correct this?

---

### Post by marbel on 2005-09-27
Nice and very useful guide! Thank you!

---

### Post by icco on 2005-10-05
I LOVE YOU!

i have been trying to get this to work for about a year now with various distros and finally it worked. i can print to my hp 5850 via both a wired and wireless network.

you
rock

thank you!

---

### Post by animefreek on 2005-10-06
ubuntu detected my laser printer HP 1010. question how can i share my HP printer so winXP user can access and print, wer on a LAN network, i already installed CUPS and samba tho i cant understand how to edit the config, can anyone help me share my printer 

thnx in advance

---

