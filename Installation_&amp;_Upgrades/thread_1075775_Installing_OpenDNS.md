---
title: "Installing OpenDNS"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by mrhealthpatriot on 2009-02-20
How to Install Opend DNS In Ubuntu 8.04 or newer:
As root/sudo, you will edit the following:

sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit

then use synaptic (or aptitude or apt-get) to acquire:
ddclient (it works with the dynamic DNS)
After ddclient is installed, you will edit the config file at etc/ddconf.conf
so it looks exactly like this:

ssl=yes # use ssl-support
use=web, web=whatismyip.org
server=updates.opendns.com
protocol=dyndns2
login=opendns_username
password=opendns_password
opendns_network_label

Log into OpenDNS.com, adjust your Dashboard settings, log out and reboot your computer.
Thats it!

---

