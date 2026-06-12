---
title: "Network Card Dies after a few minutes"
date: 2012-12-31
forum: Hardware
---

### Post by jnunez on 2012-12-31
Running Ubuntu 12.04 on a Intel i5 Gigabyte PC.

The system will boot with no major issues. I do see some ACPI errors but these disappeared when I disabled VirtualBox at boot time. I lost power after Hurricane Sandy hit and I notice that afterwards the PC will boot and all of the apps will run but all network activity will fail about 5 minutes after startup. I have checked all of the logs and no network related issues. I have added a working PCI Ethernet card and the same thing occurs.

I figured that the issue was probably software related so I decided to wipe out the drive with a new ubuntu install. Using the same USB Key, I make it to the grub window but selecting any option will cause the screen to go blank and nothing ever appears. I have left the machine on for 4 hours and came back to the same blank screen. I created various versions of ubuntu from 10 to 12 and they all fail. I have created a DVD and I noticed that after selecting the option it will attempt to load but then it stops after a few seconds and no activity.

What can I do? Wonder if the Bios is damaged?  It's an Ami EFI Bios. I know there are programs I can run via EFI.  Does anyone know how I can use this to troubleshoot the system?

Thanks,
John Nunez

---

### Post by ahallubuntu on 2012-12-31
Sounds like an issue with your modem or router that the Ubuntu computer is attached to.  Have you tried resetting it?  If you are aware of the settings, you might reset it to factory settings and set it up again.

Also, obviously check the cabling - make sure everything is securely plugged into the router, etc.

Was your modem/router connected to a surge protector?  If not - it's always possible you zapped something if you had multiple power outages during the storm.

---

### Post by jnunez on 2012-12-31
There is a printer, 2 other servers and my desktop on that same switch and everyone works find. In fact on my Mac it displays this server on the sidebar but before I can do anything it fails to connect and the ubuntu box starts having network issues.  I have disconnected all of the devices from the network and the ubuntu box has the same issue.

Everything is on Surge Protectors. The 2 old servers are on UPS but this is a new box I just got in.

---

