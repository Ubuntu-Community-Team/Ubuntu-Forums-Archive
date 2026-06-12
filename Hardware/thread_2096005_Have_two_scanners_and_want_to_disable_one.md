---
title: "Have two scanners and want to disable one"
date: 2012-12-18
forum: Hardware
---

### Post by maxplantperson on 2012-12-18
I have two scanners.

One is legit, a Fujitsu SnapScan s1500. The other is lame, it's part of my old Canon multi-function inkjet printer/scanner combo.

What annoys me to no end is that when I try to use simple-scan (or another utility), the Canon is always selected as the default scanner option.

What I'd like to do is disable the Canon scanner since I never use it (being able to re-order the scanners so the Fujitsu was the default would also work). I can't figure out how to do that - whether it's using some sort of sane config or what. Any help would be very appreciated.

---

### Post by pqwoerituytrueiwoq on 2012-12-18
i do know a workaround, the php scanner server (link in signature) has this feature, if your connected directly to a modem i suggest using a firewall on port 80
it does not fix your simple scan issue, it is a alternate front end software for scanimage

you may be able to remove or blacklist the scanner driver

---

### Post by maxplantperson on 2012-12-19
The blacklist comment gave me an idea. Thank you.

I was able to remove support for the Canon Pixma device by commenting out "pixma" in the /etc/sane.d/dll.conf file.

Problem solved. Thanks.

---

