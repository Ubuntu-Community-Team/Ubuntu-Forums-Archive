---
title: "Mouse Pointer Spins indefinitely while adding HP LaserJet Printer over network"
date: 2014-08-15
forum: Hardware
---

### Post by Pidge66 on 2014-08-15
After successful installation of Lubuntu, getting the Chrome browser working, my next step is to be able to print on my HP LaserJet 2100 over the network:

System Tools | Printers | Add

I was at first very pleasantly surprised when Lubuntu was able to discover the network printers running off my Windows XP, without me having to mess with workgroup.  Even clicking "Verify if desired" button displayed "Printer Share Verified. This printer is accessible".  HOWEVER, it fell short at the final step:  clicking the "Forward" button simply left the mouse pointer  spinning  forever (yes, I left it trying overnight!)

I then downloaded HPLIP from HP and successfully downloaded and installed missing dependent components.  The HPLIP status service is up and running on the System Tray.  I tried adding the network printer again, unfortunately, same result.

I then remember I had to type the **hp**-**setup** command after restart so I did.  It tried to discover but failed: 

```
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
error: No devices found on bus: net

```
I am running out of ideas.  Help!

---

### Post by kc1di on 2014-08-15
do you know the IP address of the printer?  
it should have it's own address on the network.
if you do try plugging  it in then hit search.
I always assign my printer an unique address that well out side the normal DHCP range 
10.0.0.50 for instance.

---

### Post by Pidge66 on 2014-08-15
Dave,

My printer is connected to a Windows XP's parallel port and then shared to the network.  My Windows 7 desktop and laptop have no problem connecting to it.

I don't need an IP as the hostname appeared to be resolved and even obtained available shared printers off that host.

Thanks!

---

