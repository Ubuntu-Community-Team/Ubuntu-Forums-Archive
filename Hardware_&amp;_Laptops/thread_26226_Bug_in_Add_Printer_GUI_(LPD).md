---
title: "Bug in Add Printer GUI? (LPD)"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by fa2k on 2005-04-12
Hi, I am pretty content with Ubuntu now, ACPI sleep works 80% of the time, but I still have one "fatal" problem. When I try to add a printer using the Administration-->Add printer UI, I get nowhere:S I can get to the page where I select printer type, I choose LPD, and two textboxes appear: host and print queue. I type in 192.168.123.254 for host and lp for queue and press Next. Then the button stays pushed down, and the UI freezes. I think it is "leaking" memory, because leaving it like that for a while causes the computer to become very unresponsive. Killing the process restores it. The printer is a Canon 4400 (I think) attached to a SMC Barricade NAT router. Any suggestions? (seems like not everybody has this problem. Mine is a clean install. I have tried typing "1" for host with same results, so the printer is not the problem).

Edit: using 192.168.123.105 as host, which is another computer which may or may not run a LPD service (it's Windows 2000, how should I know), gave me the "next" screen.

---

### Post by fa2k on 2005-04-12
Temporary work-around. Of course, it is possible to use only the config files, but that may be confusing, at least I like the user-friendlyness of the Gnome tool:

1) Create printer in GUI with "wrong" IP, eg. the LPD server's IP minus one. 

2) Modify IP-address in /etc/cups/printers.conf (it doesn't get saved when changing it in the GUI)

3) Restart computer (maybe you can restart the CUPS daemon)

---

