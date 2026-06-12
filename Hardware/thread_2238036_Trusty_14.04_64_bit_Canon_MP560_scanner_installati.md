---
title: "Trusty 14.04 64 bit Canon MP560 scanner installation PPA problem"
date: 2014-08-05
forum: Hardware
---

### Post by KieranFitzgerald on 2014-08-05
Canon MP560

Using ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu I have installed my printer driver which is working.  However on the PPA there is the following message under latest updates.

> 
[LIST]
[*]**scangearmp-common** 40 weeks ago 
Failed to build: [amd64]("https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk/+build/5171956") [i386]("https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk/+build/5171957")
[/LIST]


Any ideas as to how to get the scanner working or better the ppa fixed?

Thanks Kieran

---

### Post by pdc on 2014-08-06
Hi Kieran

according to this [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) the sane open-source project supports your device; so does Simple Scan detect your printer? 

try a couple of terminal commands also:

> [COLOR="#FF0000"]sane-find-scanner[/COLOR]

and 

> [COLOR="#FF0000"]scanimage -L[/COLOR]

_________________

you were looking to the Canon programme ScanGearMP that works well.............except your printer only had 32bit drivers released................coz it was released when that was what was used................ so it can be much easier with older printers to use more "compatible" things like 32bit: 

........for the open-source programme SANE, that is not an issue

---

### Post by KieranFitzgerald on 2014-08-08
Simple scan detects the scanner if it is plugged in to a USB port but not wirelessly.

sane-find-scanner does not find it.

---

### Post by KieranFitzgerald on 2014-08-09
Got it working used this

> 
[http://askubuntu.com/questions/200915/how-to-map-network-scanner](http://askubuntu.com/questions/200915/how-to-map-network-scanner)


---

### Post by pdc on 2014-08-09
great; some say that if you use > bjnp://<ip_address> that the address will change; unless you use a static IP for the printer;

let us know how things go as you reboot the computer from time to time

---

