---
title: "Printer set up with new router"
date: 2012-03-27
forum: Hardware
---

### Post by cbfarrand on 2012-03-27
Upgraded from D-Link router to Netgear WNDR3800 with ReadySHARE printer feature. Had printer set up and working fine with old router, need to get it set up with new router.Still have existing set up from old router if it can be modified. Thanks

---

### Post by skitheo on 2012-04-29
I have this challenge as well. Need to be able to print from a printer connected to a WNDR4500 (Netgear N900) Any suggestions? Bonjour for Ubuntu?

---

### Post by ahallubuntu on 2012-04-29
On the old router, the printer was assigned a unique IP address.  If you did nothing, the router would assign it an IP automatically via the DHCP service - say it got an IP of (for example) 192.168.1.5 .

With the new router, it may get a different IP, no longer 192.168.1.5 . It may be 10.1.10.4 or something like that.  So, your computer can no longer communicate with the printer - like it has a new phone number...

You could either re-install the printer or try to configure your new router just like the old one was setup.  If you still have the old router, try plugging it in, then figuring out what the old IP address was.  Then tell the new router to assign that IP address to your printer - make a "reservation" for it.  And the new router should also use the same subnet as the old one - that is, if the old router was 192.168.1.x, make sure the new one is using 192.168.1.x (not 192.168.0.x or 10.1.10.x or something like that).

You may also be able to edit the printer config in Ubuntu and just change the IP address to the new one your new router has assigned to it.

---

### Post by skitheo on 2012-04-30
Thanks for the response ahallubuntu, but it is not a Wifi or Ethernet printer. It is a USB printer, so while it may be totally correct, it answers the wrong question. A ReadyShare router has USB ports on it to share printers or hard drives. The printer is connected to the USB port on the router. 

Previously, I had a Netgear ProSafe FWG114P that used LPD/LPR protocol to spool print jobs for the USB-connected printer. For the WNDR4500, Netgear want the user to install a cheesy USB Control Center app that inserts itself in the Windows USB driver stack and creates a virtual USB port over the network. NO THANKS!! That app disables VMware's USB device virtualization!!! and there's no Linux equivalent.

---

### Post by tom0812 on 2012-06-13
Hi skitheo,

I have the same problem as you. Does your printer already work with the WNDR4500?

Many thanks, Tom

---

### Post by skitheo on 2012-06-13
Hi Tom,

Unfortunately, my workaround has stuck. I'm using the old FWG114P router as my print server.

---

### Post by tom0812 on 2012-07-07
The same to me, I'm working with a print server now, too.  A sad thing because the manufacturer claims that this router works with Linux. But he miss to say "not for 100%".

Tom :-(

---

### Post by ludobm on 2012-09-11
Still no possibility to access USB printer on Linux, Unix ?
I need a solution for Ubuntu !!

---

### Post by Kivech on 2012-10-21
Hi guys,

I have the same challenge. In my case with a DGND3700v2 modem/router.

Checking the advanced settings, it gives me a list of possible connection methods (https/http/network/ftp).
The insteresting thing is though, that in the top of this configuration screen it shows the Windows default group "Workgroup".

I have no idea how these things work in Windows, but could it be that the answer lies in becoming a member (somehow) of this Workgroup and then using one of the indicated connection methods?
I tried the links myself to configure my printer in Ubuntu 12.10, but it's not working. Ubuntu doesn't recognize the printer or its status.

In my case, it also clearly states that this functionality is only intended for Mac and Windows PCs. It doesn't mention Linux anywhere.

---

