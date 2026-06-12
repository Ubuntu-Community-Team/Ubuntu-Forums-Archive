---
title: "Previously unsupported scanners Now supported"
date: 2018-09-01
forum: Hardware
---

### Post by markosjal on 2018-09-01
Okay, its  inSANE because its not SANE , Not WIA, not Twain, but here it is. 

I put together support for some scanners that are officially "unsupported" under Ubunu/Linux. This will probably work with most any Linux flavour. It was developed and tested on Ubuntu 14.04 and 16.04 most recently.

[IMG]http://teknogeekz.com/images/s400wScanners.jpg[/IMG]

It should support the following scanners:
[LIST]
[*]ION AirCopy
[*]ION AirCopy E-Post Edition
[*]Halo Magic Scanner
[*]Mustek iScan Air / S400W
[*]Century CPS-A4WF
[*]Transcription Patri Kun A4 Wi-Fi Portable Scanner
[*]&#36578;&#20889;&#12497;&#12483;&#12488;&#12522;&#12367;&#12435; A4 Wi-Fi&#12509;&#12540;&#12479;&#12502;&#12523;&#12473;&#12461;&#12515;&#12490;&#12540;
[/LIST]


I call it PHPScan because it uses PHP and works from a web interface. You must have Apache or other web server and PHP installed. It saves all scans and copy/print jobs to the host with clickable links for downloading to local the device. You can also share the scans folde via SMB or NFS.

from there scanning is done on a web browser either to the host IP address or localhost. The good news is it even allows scanningfrom a smart TV or any device with a web browser. 

here is an animtaed GIF of how it works:
[IMG]http://teknogeekz.com/images/phpscananimbig.gif[/IMG]

I give credit to the Bastel site for creating the executable:
[http://bastel.dyndns.info/~public/s400w/](http://bastel.dyndns.info/~public/s400w/)

More information and download available at: 
[http://teknogeekz.com/#projects](http://teknogeekz.com/#projects)


Mark

---

