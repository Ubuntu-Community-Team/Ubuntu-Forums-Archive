---
title: "Network printer"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by cs_1939 on 2007-02-19
I have installed Ubuntu on its own hard drive, and Kubuntu on its own. I have Win XP on the third drive. I can access and print from XP with no problem. When I try to setup the printer with Ubuntu or Kubuntu I get a message "no printer found at this address or port". I located and printed the IP for each device on the network: default gateway is 192.168.1.1, my PC is 192.168.1.104, my wife's is 192.168.1.100, printer is 192.168.1.101, DNS Server is 12.6.42.1,
Subnet Mask is 255.255.255.0, configuration is DHCP, Port is 9100. No matter which address I enter I get the same message, "no printer at this address or port"

---

### Post by tgalati4 on 2007-02-20
Dear CS

To master printing in Linux, one must become one with CUPS.

In Ubuntu, Firefox what are the results of:

localhost:/631

What is the printer model?

Make sure /etc/hosts has all of the local IP addresses that you care about.

sudo nano /etc/hosts   (to edit the hosts table)

Unfortunately printing in Linux is not plug and play, but with a little study, CUPS will give you printing functionality that Windows can only dream about.

With CUPS, someone in sunny Southern California (such as myself) could print a document in Trapper Creek through the internet.  Try that in Windows.

Good Luck,

Terry

---

### Post by tgalati4 on 2007-02-20
I missed the HP Photosmart 2600 in the tag line.

That is good news.  HP printers are well-supported in Linux.

What are the interesting error messages from: /var/log/cups?

Make sure the printer is not asleep when setting it up.  Make sure it's address is correctly set in the printer's front panel.  I prefer to use a fixed address, outside of the range of DHCP, 192.168.1.150 for example.

Keep the Ubuntu faith,

Terry

---

### Post by stchman on 2007-02-20
> **cs_1939 said:**
> I have installed Ubuntu on its own hard drive, and Kubuntu on its own. I have Win XP on the third drive. I can access and print from XP with no problem. When I try to setup the printer with Ubuntu or Kubuntu I get a message "no printer found at this address or port". I located and printed the IP for each device on the network: default gateway is 192.168.1.1, my PC is 192.168.1.104, my wife's is 192.168.1.100, printer is 192.168.1.101, DNS Server is 12.6.42.1,
Subnet Mask is 255.255.255.0, configuration is DHCP, Port is 9100. No matter which address I enter I get the same message, "no printer at this address or port"

Hello, I have an HP LaserJet 4050tn and I it works great under Ubuntu.  You must first do this give your printer an IP.  If your printer has a network interface there is a way to do this.  Since your router uses the 192.168.1.xxx IPs give your printer an IP say 192.168.1.120.  Next install add a printer from the administrative portion.  Use the HP Jet Direct instead of CUPS.

Leave the port at its default and put the ip address you geve the printer in the box that wants the IP.  I don't know what type of printer you have, but Ubuntu has 1000s of printers listed.  This should work for you.

---

### Post by tgalati4 on 2007-02-20
I have an Officejet 7110 with a jet direct card and a static IP address set up in the printer's menu system.  I use both the CUPS and jet direct.  I find CUPS is more reliable and I can reprint a job from CUPS (if I need extra copies of a printout), plus I have it set up for remote internet printing as well.  

Either way will work.

---

