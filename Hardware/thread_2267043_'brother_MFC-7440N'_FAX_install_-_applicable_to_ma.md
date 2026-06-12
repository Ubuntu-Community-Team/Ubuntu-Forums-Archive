---
title: "'brother MFC-7440N' FAX install - applicable to many brother 4 in 1 machines"
date: 2015-02-27
forum: Hardware
---

### Post by Li_Wu on 2015-02-27
This thread discusses possible install quirks with brother hardware and integration with efax-gtk and tk-fax and sane scan software.[B]

brother[/B] is a cool manufacturer because they release their drivers open source and the driver design is sticking to a clear kewl plan.
unlike others, **bro** support Linux very well. But itz kinda striking: bro delivers cool office machines that withstand ultra heavy business use, e.g. in German industry. Yet the fax productivity features are in stark contrast with the very superior hardware design of bro machinery. Their paper transport is real excellent and doesnt wear down in 15 yrs of heavy duty industry deployment. But if u wanna fax from Linux? all u are offered is a minimal GUI which is tricky to set up. printing and scanning - however - works 100% flawlessly like a kikbut company like bro is expected to deliver. xsane and cups printing setup works like a charm. PC FAX is where it gets tricky.

To set up fax, scan & print brother drivers with their 64 bit .deb files is no biggie.
though the fax module is avail as .c source there are 2 binaries w/o sourcecode: **brfaxd** the bro's fax daemon and **[COLOR=#a52a2a]usb4[/COLOR]brfaxd** some USB tool for it. 

Basically the instruction by **bro** work very well. But their fax GUI is pretty limited. Still open-office integration works well (fax out of libre-office writer document asf.)

After install is finished, one finds the printers in the CUPS page like   [http://localhost:631/printers/BRFAX](http://localhost:631/printers/BRFAX)

bro sets up some daemons asf. for scan and fax:
/opt/brother/modem/brfaxd
/opt/brother/modem/src/brfax_service.h
/opt/brother/modem/brfax-service.pid
/var/log/brfaxservice-log

/etc/opt/brother/modem/brfaxservice.conf
/etc/init.d/brfaxservice

```
/usr/local/Brother/       
```  some bin & stuff in here

/usr/local/Brother/sane/binaries  to config the [B]bro


[/B]I wonder whether the faxmodem can be used with cutecom too for dial-in ppp


typically , you'd need the following files for install:

brmfc-src-1.0.0-1.i386.tar.gz
brfaxmodem-1.1.3-1.i386.deb --- contains daemon

brmfcfaxlpd-1.0.0-1.i386.deb
brmfcfaxcups-1.0.0-1.i386.deb


cupswrapperMFC7440N-2.0.2-1.i386.deb
brother-laser2-cups-driver-2.0.2-1.tar.gz
brother-udev-rule-type1-1.0.0-1.all.deb

brscan3-0.2.11-5.amd64.deb
brscan3-src-0.2.11-5.tar.gz
brscan-skey-0.2.4-1.amd64.deb

linux-brprinter-installer-2.0.0-1.gz




[COLOR=#000000]lpr driver system:[/COLOR]



[LIST]
[*]the configuration filename for your distribution.
[B]
Ubuntu, Debian : /etc/printcap
[/B] 
[*]Edit the file according to your connection.
_**For USB Connection (Default)**_
Check if the parameter of ":lp" is ":lp=/dev/usb/lp0"
_**For Network Connection**_
replace ":lp" line to the following 2 lines
:rm=(ip address of your printer)\
:rp=lp\ 
[*]Restart the print system. [B]
Command (for lpr): /etc/init.d/lpr restart
Command (for lprng) : /etc/init.d/lprng restart[/B] 
[/LIST]


[COLOR=#000000](lprng not to confuse with a real rng = random # gen)


I have 10 beans now but I am sure they will reduce me to 9 or less real soon.

That's why I discontinued this article. they keep taking my beans away. 
[/COLOR]

---

### Post by Bucky Ball on 2015-02-27
*Thread moved to **Hardware**.*

---

