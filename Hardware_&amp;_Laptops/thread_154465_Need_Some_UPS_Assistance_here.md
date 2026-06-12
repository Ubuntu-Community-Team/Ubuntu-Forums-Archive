---
title: "Need Some UPS Assistance here"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by Princey on 2006-04-03
Hi, I've got a CyberPower SP525SL UPS backup power [http://www.cyberpowersystems.com/CPS525SL.asp]("http://www.cyberpowersystems.com/CPS525SL.asp") (have had it for a year now). I've moved it from my Windows XP machine to my main machine running Kubuntu Breezy. Where I live, we get frequent power cuts, as frequent as sometimes 5 or more in a month.

I've been fighting for a while to get it up and running (UPS monitoring software) on my machine. The manufacturer does provide Linux drivers (thank God) so I didn't have to go around searching my head off for the drivers/software. They provide both a tar download and .rpm download. I first downloaded the rpm version and using alien converted it to a .deb package and installed. I followed the directions in the manual to configure but that's as far as I get. Uninstalled the .deb package then tried the .tar one and installed, still no luck. The UPS is monitored via a serial cable. Whenever I type the command from the prompt as directed to bring up the configuration settings I get the error message that it can't connect to the UPS service ](*,) . 

How do I verify that Kubuntu is seeing my UPS via the serial port so that I could configure the port settings? (It used COM1 under Windows). I tried installing upsd and knutclient:confused:  but not much luck either. It's one thing to have the UPS, but I'd really like it functioning so that I can have it automatically shut down my pc if I'm away during one of the mysterious power outages. Thanks for any info that would help.

---

### Post by Princey on 2006-04-03
Update:

I completely removed knutclient, removed the .deb package I made from the .rpm using alien completely, rebooted and tried the tarball package again. Installed using the script and that did work. I can configure it from the terminal but there's no GUI for it that I can monitor my battery performance. Any recommendations? knutclient won't work as it requires a tcp/udp address and mine uses the "ttyS0" (serial port). I'd be grateful for any info on the said matter.

---

