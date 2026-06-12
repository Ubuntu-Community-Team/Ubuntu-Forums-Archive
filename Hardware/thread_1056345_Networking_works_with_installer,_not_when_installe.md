---
title: "Networking works with installer, not when installed"
date: 2009-01-31
forum: Hardware
---

### Post by superwad on 2009-01-31
I downloaded the 8.10 server edition and installed it on my print server.  During the installation, networking worked just fine.  However, when I booted into the final system, networking no longer worked.  I'm using a PCMCIA network adapter (Linksys PCMPC100) on a Compaq Presario 1685.

So I booted into the installer to see if I could find which modules were being loaded that would cause the networking to work.  I thought I found the modules, but no dice.  I also checked the kernel, and it's no surprise that the installer kernel is the same as the final kernel.

I'm using 'pcnet_cs' and '8390' (both were present in the installer and initially not present in the final system).  However, in the installer, pcnet_cs says there is 1 other module using it, but it doesn't list it.

I noticed that the installer goes through a stage that is "Starting PC card services".  It does this step twice.  Once when detecting hardware, and another time when it's configuring the network.  I'm wondering if perhaps the final system is not doing this?  If that's the case, how would I go about enforcing this?

When I'm booted into the system, I do lspci, and the device is not listed.  If I check dmesg after ejecting and putting the card back in, I'm only told that pccard detected the ejection and insertion, and nothing more.

Could anybody help me figure out what the installer is doing differently so I can get networking working?

Any help is much appreciated :)

---

### Post by superwad on 2009-01-31
Alright, I got everything working.  Here is what I did:

[LIST][*]Add "pcnet_cs" and "8390" to /etc/modules
[*]Install pcmciautils.  I downloaded it from [http://packages.ubuntu.com/intrepid/pcmciautils](http://packages.ubuntu.com/intrepid/pcmciautils) and saved it to a USB key.  Then I put it in /var/cache/apt/archives and installed as usual with `sudo apt-get install pcmciautils'.
[*]Configure /etc/network/interfaces with my network information on eth0.
[*]Restart computer
[*]Great success!
[/LIST]

I hope this helps somebody else out there in internet land to get this card working.

---

