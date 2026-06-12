---
title: "How do I repair a broken 8.10 installation"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by tulchan on 2009-01-05
I'm an inexperienced Linux user, can someone help with the following?
  
On other distribution CD's, there is often a 'repair' or reinstall option. 

How can I do this (or the equivalent) on a machine which has only got Ubuntu installed. The reason I want to reinstall but not erase the content of the hard disks is that I have set up Samba to allow WinXP single sign-on and shares but in the process cannot connect to the internet any longer.

I can ping some external ip addresses and one or two FQDNs but can only browse the internet using IP addresses and can't install upgrades from ubuntu's sites because the names can't be resolved.

---

### Post by lemming465 on 2009-01-06
Sounds like /etc/resolv.conf got hosed; that's what specifies where DNS nameservers are found (unless you are running a local nameserver of some kind).  Often these are specified by DHCP from your ISP.  Try putting, say a couple of opendns.com IP's in there, say 208.67.222.222 and 208.67.220.220.  You can do this a douple of ways.  A CLI way would be **sudo nano /etc/resolv.conf** and edit it to look like```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

A GUI way would be **gksudo network-manager**, switch to the DNS tab, and enter the above IP addresses.

---

