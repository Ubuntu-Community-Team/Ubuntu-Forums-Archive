---
title: "Network Printing: /usr/lib/cups/backend/ipp failed"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by pyjamashark on 2007-07-31
Hi I need some help. I have 3 machines all running ubuntu connected via a wireless network. One of them is connected to an HP Laserjet 1018 printer. I have managed to get it to print from the machine it is connected to but I can not for the life of me get it to print via the network from any of the other two machines. (When that machine was running windows I could print via the network from the other two ubuntu machines using samba - it worked great!) Now that they are all using ubuntu I can't fricking get the network printing working.

This is the error message I get. Paused: /usr/lib/cups/backend/ipp failed

On the server machine I have enabled "Share Printers" and on the client machines I have enabled "Detect LAN Printers"

Then on the client machine I have added a network printer with this URI: ipp://192.168.0.102/printers/<LaserJet-1018> (192.168.0.102 is the ip address of the server machine)

I am fresh out of ideas, both client machines still give the same error message described above!

please help
joe

---

### Post by juantovarm on 2007-08-03
I think your soulution is simple:

in terminal

sudo pico /etc/cups/cupsd.conf

there's an entry that goes:

# Only listen for connections from the local machine.
Listen 631

you need to add right under that last line:

Listen localhost:631

save and exit
 after that in terminal 

 sudo /etc/init.d/cupsys restart

After that you can add the ipp lines in the other machines

By the way, in my pc i have in printers also the "share printers" choice enabled

Hope it helps

---

