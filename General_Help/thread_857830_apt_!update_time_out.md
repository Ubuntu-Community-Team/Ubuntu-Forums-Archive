---
title: "apt !update? time out"
date: 2008-07-12
forum: General Help
---

### Post by dutler on 2008-07-12
Hello:
I have a Kubuntu 8.04 workstation on the same subnet and DHCP server, DNS, gateway, firewall as the newly installed Ubuntu Server 8.04 server.

The Kubuntu ws works as expected when apt-get update and upgrade are ran from Konsole. But on the server, I can no longer run apt-get update.

When ran, I get the following time out:
> Err [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release.gpg
  Could not connect to mirror.anl.gov:80 (146.137.96.15), connection timed out [IP: 146.137.96.15 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Translation-en_US
  Unable to connect to mirror.anl.gov http: [IP: 146.137.96.15 80]

Note: This the repo I tried after none of the "stock" ones worked - just to make sure it wasnt a repo issue. Also, I do not get a time out running apt-get update to the same repos on the workstation.

The server can resolve the host names - shows the IP and I can ping the repos as well.

I have ran apt-get clean with no improvements.

thanks, tom

---

### Post by dutler on 2008-11-15
Its been awhile, but i think i determined the problem to be with my name server.  Perhaps
[LIST]
[*]apt was showing the symptoms because of shorter time out than firefox?
[*]the workstation didnt have problems with update because it all ready had IPs in the cache?
[/LIST]

---

