---
title: "Ubuntu Lamp server VM picked up a Hamachi IP address...How is this possible?"
date: 2008-11-18
forum: General Help
---

### Post by greavette on 2008-11-18
Hello,

On my Widows XP Home laptop, I started up an Ubuntu Hardy Lamp server in  VMWare and discovered that the IP address assigned to this VM was given an IP address that seems to be in the Hamachi range - 5.xx.x.xxx.  I do have a router on my home network that gives out IP address in the 192.168.x.xxx range.  All my other PC's and VM's always receive an IP from my router.  This is the first I've seen this happen?

This Lamp server does not have the IP staticly set either...I've used this exact VM on other networks and have always received an IP from that networks router.

Any ideas on how this could happen?

Thanks.

---

### Post by gpsmikey on 2008-11-18
If you are wireless with the laptop, any chance it got that address from a nearby router that is mis-configured ???  It either had to invent that address on it's own, or it was given that address.  If it was given that address, the only thing that comes to mind is somehow something else gave it out which is why wireless comes to mind.

mikey

---

### Post by dcstar on 2008-11-19
> **greavette said:**
> Hello,

On my Widows XP Home laptop, I started up an Ubuntu Hardy Lamp server in  VMWare and discovered that the IP address assigned to this VM was given an IP address that seems to be in the Hamachi range - 5.xx.x.xxx.  I do have a router on my home network that gives out IP address in the 192.168.x.xxx range.  All my other PC's and VM's always receive an IP from my router.  This is the first I've seen this happen?
......
VMWare VMs get their DHCP IP addresses from the host (Bridge mode) or from the VMWare server's configuration (Host or NAT modes).

---

### Post by graphic on 2008-12-23
Just disable the net adapter for Hamachi and type "sudo /etc/init.d/networking restart" I believe Hamachi's DHCP reply holds precedence over the the Router's because it is a "bigger" network. Afterward just re-enable the Hamachi net adapter. In case you don't know where that is (assuming your using Windows XP) its under Network Places -> Network Connections (In the sidebar). It should be called something like "Hamachi blah blah blah" or whatever. Use a static IP in the future to avoid this.

I know he didnt ask for a solution but someone might and they'd probably find this in the search.

---

