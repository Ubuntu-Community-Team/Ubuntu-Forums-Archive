---
title: "HP Photosmart C4680, CUPS"
date: 2014-12-24
forum: Hardware
---

### Post by maiandros on 2014-12-24
Hello to all, 
I`m having some difficulty making my HP Printer work with my new 14.04 x64. 
I  don`t know what`s wrong or how can I help you with more details. My  printer is a HP Photosmart C4680 model and was running fine with my  previous Linux Distribution. Recently I`ve changed back to Ubuntu by installing 14.04 x64bit and I cannot make the printer work  anymore. 
I`ve tried to use the Printer Configuration to set my  printer up with no luck. I`ve also tried to troubleshoot and it keeps  telling me that CUPS service is not running and that is should enable  it. But when I`ve tried in terminal to start the cups service i`m  getting "cups: unrecognized service"...! 
Ok...it seemed pretty wierd to me so I`ve tried to ```
sudo apt-get install --reinstall cups
``` cups and that`s the message that I`ve got : 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cups : Depends: libcups2 (= 1.7.2-0ubuntu1.2) but 1.7.2-0ubuntu1.3 is to be installed
        Depends: libcupscgi1 (>= 1.4.2) but it is not going to be installed
        Depends: libcupsmime1 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsppdc1 (>= 1.4.0) but it is not going to be installed
        Depends: cups-core-drivers (>= 1.7.2-0ubuntu1.2)
        Depends: cups-daemon (>= 1.7.2-0ubuntu1.2)
        Depends: cups-ppdc
        Recommends: printer-driver-gutenprint but it is not going to be installed
E: Unable to correct problems, you have held broken packages. 
After that, eventhough I didn`t have any other problems indicating a  source list or any related problem untill now, I`ve cleaned the *cache,autoclean/upgrade/update* but none of this helped me solve my problem. 
PS: I`ve downloaded the HPLip from the HP site [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)  hoping it was going to make the difference but nothing changed ...

Any help would be great and thank you all in advance!

---

### Post by schragge on 2014-12-24
Looks like you have enabled at some point the **trusty-proposed** repository for pre-released updates. Disable it, then
```

sudo apt-get update
sudo apt-get -f install

```

or just pin trusty
```

sudo apt-get -t trusty --reinstall install cups

```

---

### Post by maiandros on 2014-12-24
> **schragge said:**
> Looks like you have enabled at some point the **trusty-proposed** repository for pre-released updates. Disable it, then
```

sudo apt-get update
sudo apt-get -f install

```

or just pin trusty
```

sudo apt-get -t trusty --reinstall install cups

```

Thanks for your tip...I had indeed the pre-released enabled! But even if I have disable them and follow your steps...I`m still having the same message of error and unmet dependencies.

---

### Post by schragge on 2014-12-24
Well, then do it like this
```
sudo apt-get -t trusty --reinstall --only-upgrade install '[c]ups'
```

---

### Post by maiandros on 2014-12-25
> **schragge said:**
> Well, then do it like this
```
sudo apt-get -t trusty --reinstall --only-upgrade install '[c]ups'
```

Ok...I`ve tried that too : > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'mfc465cncupswrapper' for regex '[c]ups'
Note, selecting 'dcp9042cdncups' for regex '[c]ups'
Note, selecting 'cupsddk' for regex '[c]ups'
Note, selecting 'cupswrapperdcp110c' for regex '[c]ups'
Note, selecting 'hl4050cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8820d' for regex '[c]ups'
Note, selecting 'cupswrapperfax2900' for regex '[c]ups'
Note, selecting 'cups-core-drivers' for regex '[c]ups'
Note, selecting 'cups-server-common' for regex '[c]ups'
Note, selecting 'dcp540cncupswrapper' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-laser' for regex '[c]ups'
Note, selecting 'cupswrapperfax2920' for regex '[c]ups'
Note, selecting 'cupswrapperhl2070n' for regex '[c]ups'
Note, selecting 'cupswrappermfc8420' for regex '[c]ups'
Note, selecting 'cupswrapperhl5240' for regex '[c]ups'
Note, selecting 'mfc850cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax3800' for regex '[c]ups'
Note, selecting 'cupswrapperfax1840c' for regex '[c]ups'
Note, selecting 'hl4050cdncups' for regex '[c]ups'
Note, selecting 'dcp130ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax1920cn' for regex '[c]ups'
Note, selecting 'cupswrappermfc8440' for regex '[c]ups'
Note, selecting 'mfc9440cncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl6050d' for regex '[c]ups'
Note, selecting 'dcp9040cncupswrapper' for regex '[c]ups'
Note, selecting 'gnuspool-cupspy' for regex '[c]ups'
Note, selecting 'cupswrappermfc9800' for regex '[c]ups'
Note, selecting 'cupswrapperhl1430' for regex '[c]ups'
Note, selecting 'python3-cups' for regex '[c]ups'
Note, selecting 'cupswrapperdcp1000' for regex '[c]ups'
Note, selecting 'dcp750cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1440' for regex '[c]ups'
Note, selecting 'dcp9045cdncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1670n' for regex '[c]ups'
Note, selecting 'cupsys-client' for regex '[c]ups'
Note, selecting 'cupswrapperhl1450' for regex '[c]ups'
Note, selecting 'cupswrappermfc7420' for regex '[c]ups'
Note, selecting 'hl4040cncups' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-extra' for regex '[c]ups'
Note, selecting 'mfc845cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp310cn' for regex '[c]ups'
Note, selecting 'libcups2-dev' for regex '[c]ups'
Note, selecting 'cupswrappermfc5840cn' for regex '[c]ups'
Note, selecting 'libcups2' for regex '[c]ups'
Note, selecting 'python-cups' for regex '[c]ups'
Note, selecting 'cups-daemon' for regex '[c]ups'
Note, selecting 'cupswrappermfc9860' for regex '[c]ups'
Note, selecting 'cupswrapperfax2820' for regex '[c]ups'
Note, selecting 'mfc235ccupswrapper' for regex '[c]ups'
Note, selecting 'mfc9440cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5130' for regex '[c]ups'
Note, selecting 'libcupsmime1' for regex '[c]ups'
Note, selecting 'cups-client' for regex '[c]ups'
Note, selecting 'cupswrappermfc9880' for regex '[c]ups'
Note, selecting 'cupswrapperhl5140' for regex '[c]ups'
Note, selecting 'mfc5460cncupswrapper' for regex '[c]ups'
Note, selecting 'libcupsimage2' for regex '[c]ups'
Note, selecting 'dcp9042cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax2850' for regex '[c]ups'
Note, selecting 'dcp150ccupswrapper' for regex '[c]ups'
Note, selecting 'mfc9420cncups' for regex '[c]ups'
Note, selecting 'fax2480ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc9700' for regex '[c]ups'
Note, selecting 'cupswrapperfax4100' for regex '[c]ups'
Note, selecting 'cupswrappermfc210c' for regex '[c]ups'
Note, selecting 'cups' for regex '[c]ups'
Note, selecting 'cups-backend-bjnp' for regex '[c]ups'
Note, selecting 'cupswrapperdcp1400' for regex '[c]ups'
Note, selecting 'cupswrapperhl5170dn' for regex '[c]ups'
Note, selecting 'libcupsimage2-dev' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8020' for regex '[c]ups'
Note, selecting 'fax1860ccupswrapper' for regex '[c]ups'
Note, selecting 'cups-pk-helper' for regex '[c]ups'
Note, selecting 'bluez-cups' for regex '[c]ups'
Note, selecting 'cupswrapperhl6050' for regex '[c]ups'
Note, selecting 'cupswrapperfax1835c' for regex '[c]ups'
Note, selecting 'cupswrappermfc8660dn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1850' for regex '[c]ups'
Note, selecting 'dcp153ccupswrapper' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-bh7' for regex '[c]ups'
Note, selecting 'gkrellmapcupsd' for regex '[c]ups'
Note, selecting 'dcp560cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8040' for regex '[c]ups'
Note, selecting 'dcp9040cncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1470n' for regex '[c]ups'
Note, selecting 'mfc440cncupswrapper' for regex '[c]ups'
Note, selecting 'libcupsmime1-dev' for regex '[c]ups'
Note, selecting 'cupswrapperhl5280dw' for regex '[c]ups'
Note, selecting 'cupswrappermfc9760' for regex '[c]ups'
Note, selecting 'cupswrappermfc420cn' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8060' for regex '[c]ups'
Note, selecting 'cupswrapperhl5030' for regex '[c]ups'
Note, selecting 'dcp330ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7010' for regex '[c]ups'
Note, selecting 'cupswrappermfc3240c' for regex '[c]ups'
Note, selecting 'cupswrappermfc6800' for regex '[c]ups'
Note, selecting 'cups-driver-gutenprint' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8045d' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-laser1' for regex '[c]ups'
Note, selecting 'cupswrapperhl5040' for regex '[c]ups'
Note, selecting 'cupsys-bsd' for regex '[c]ups'
Note, selecting 'cups-browsed' for regex '[c]ups'
Note, selecting 'cupswrapperfax1820c' for regex '[c]ups'
Note, selecting 'cups-pdf' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7020' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7025' for regex '[c]ups'
Note, selecting 'fax2580ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5050' for regex '[c]ups'
Note, selecting 'hl4070cdwcups' for regex '[c]ups'
Note, selecting 'cups-filters-core-drivers' for regex '[c]ups'
Note, selecting 'python2.7-cups' for regex '[c]ups'
Note, selecting 'hl4040cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax4750e' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8065dn' for regex '[c]ups'
Note, selecting 'hl4040cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5270dn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1230' for regex '[c]ups'
Note, selecting 'mfc230ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc5440cn' for regex '[c]ups'
Note, selecting 'cups-bsd' for regex '[c]ups'
Note, selecting 'fax1960ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc410cn' for regex '[c]ups'
Note, selecting 'cupswrapperhl5070n' for regex '[c]ups'
Note, selecting 'mfc860cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1240' for regex '[c]ups'
Note, selecting 'cupswrappermfc3340cn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1250' for regex '[c]ups'
Note, selecting 'cupswrappermfc7220' for regex '[c]ups'
Note, selecting 'mfc885cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8840d' for regex '[c]ups'
Note, selecting 'apcupsd-doc' for regex '[c]ups'
Note, selecting 'cupswrappermfc8870dw' for regex '[c]ups'
Note, selecting 'libcupscgi1' for regex '[c]ups'
Note, selecting 'cupswrappermfc9160' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-mfc9420cn' for regex '[c]ups'
Note, selecting 'mfc665cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc3420c' for regex '[c]ups'
Note, selecting 'cupswrappermfc9660' for regex '[c]ups'
Note, selecting 'hl4040cdncups' for regex '[c]ups'
Note, selecting 'mfc240ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1270n' for regex '[c]ups'
Note, selecting 'cupswrappermfc7225n' for regex '[c]ups'
Note, selecting 'libcupscgi1-dev' for regex '[c]ups'
Note, selecting 'cupswrappermfc3820cn' for regex '[c]ups'
Note, selecting 'cups-filters' for regex '[c]ups'
Note, selecting 'mfc9450cdncupswrapper' for regex '[c]ups'
Note, selecting 'apcupsd-cgi' for regex '[c]ups'
Note, selecting 'mfc685cwcupswrapper' for regex '[c]ups'
Note, selecting 'cups-tea4cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc9180' for regex '[c]ups'
Note, selecting 'hl4070cdwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp350ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax5750e' for regex '[c]ups'
Note, selecting 'cupswrappermfc8460n' for regex '[c]ups'
Note, selecting 'libcupsppdc1' for regex '[c]ups'
Note, selecting 'printer-driver-hpcups' for regex '[c]ups'
Note, selecting 'libcupsfilters-dev' for regex '[c]ups'
Note, selecting 'ghostscript-cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc4800' for regex '[c]ups'
Note, selecting 'mfc660cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8860dn' for regex '[c]ups'
Note, selecting 'apcupsd' for regex '[c]ups'
Note, selecting 'cupswrapperfax2440c' for regex '[c]ups'
Note, selecting 'cups-common' for regex '[c]ups'
Note, selecting 'mfc680cncupswrapper' for regex '[c]ups'
Note, selecting 'dcp353ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc9030' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-ac' for regex '[c]ups'
Note, selecting 'cupswrapperhl5250dn' for regex '[c]ups'
Note, selecting 'cupswrappermfc620cn' for regex '[c]ups'
Note, selecting 'mfc460cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax1815c' for regex '[c]ups'
Note, selecting 'cupswrapperhl1650' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-common' for regex '[c]ups'
Note, selecting 'mfc630cdcupswrapper' for regex '[c]ups'
Note, selecting 'libcupsppdc1-dev' for regex '[c]ups'
Note, selecting 'dcp135ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc3320cn' for regex '[c]ups'
Note, selecting 'python-cupshelpers' for regex '[c]ups'
Note, selecting 'ghostcript-cups' for regex '[c]ups'
Note, selecting 'cupswrapperhl2030' for regex '[c]ups'
Note, selecting 'libnet-cups-perl' for regex '[c]ups'
Note, selecting 'cups-dbg' for regex '[c]ups'
Note, selecting 'mfc5860cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5150d' for regex '[c]ups'
Note, selecting 'cupswrappermfc8500' for regex '[c]ups'
Note, selecting 'cupswrapperhl2040' for regex '[c]ups'
Note, selecting 'cups-ppdc' for regex '[c]ups'
Note, selecting 'cupswrappermfc7820n' for regex '[c]ups'
Note, selecting 'cupswrappermfc9070' for regex '[c]ups'
Note, selecting 'mfc3360ccupswrapper' for regex '[c]ups'
Note, selecting 'dcp9045cdncupswrapper' for regex '[c]ups'
Note, selecting 'mfc260ccupswrapper' for regex '[c]ups'
Note, selecting 'cupsomatic-ppd' for regex '[c]ups'
Note, selecting 'cupswrapperfax1940cn' for regex '[c]ups'
Note, selecting 'hplip-cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc3220c' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8025d' for regex '[c]ups'
Note, selecting 'mfc9840cdwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp750cwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp770cwcupswrapper' for regex '[c]ups'
Note, selecting 'mfc9450cdncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1030' for regex '[c]ups'
Note, selecting 'libcupsfilters1' for regex '[c]ups'
Note, selecting 'mfc9840cdwcups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1870n' for regex '[c]ups'
Note, selecting 'cups-filters' instead of 'ghostscript-cups'
Note, selecting 'python-cups' instead of 'python2.7-cups'
Skipping bluez-cups, it is not installed and only upgrades are requested.
Skipping cups-driver-gutenprint, it is not installed and only upgrades are requested.
Skipping cups-pk-helper, it is not installed and only upgrades are requested.
Skipping apcupsd, it is not installed and only upgrades are requested.
Skipping apcupsd-cgi, it is not installed and only upgrades are requested.
Skipping apcupsd-doc, it is not installed and only upgrades are requested.
Skipping cups-backend-bjnp, it is not installed and only upgrades are requested.
Skipping cups-pdf, it is not installed and only upgrades are requested.
Skipping cups-tea4cups, it is not installed and only upgrades are requested.
Skipping gkrellmapcupsd, it is not installed and only upgrades are requested.
Skipping gnuspool-cupspy, it is not installed and only upgrades are requested.
Skipping libnet-cups-perl, it is not installed and only upgrades are requested.
Skipping python3-cups, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-ac, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-bh7, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-common, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-extra, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-laser, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-laser1, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-mfc9420cn, it is not installed and only upgrades are requested.
Skipping cups, it is not installed and only upgrades are requested.
Skipping cups-core-drivers, it is not installed and only upgrades are requested.
Skipping cups-daemon, it is not installed and only upgrades are requested.
Skipping cups-dbg, it is not installed and only upgrades are requested.
Skipping cups-ppdc, it is not installed and only upgrades are requested.
Skipping cups-server-common, it is not installed and only upgrades are requested.
Skipping libcups2-dev, it is not installed and only upgrades are requested.
Skipping libcupscgi1, it is not installed and only upgrades are requested.
Skipping libcupscgi1-dev, it is not installed and only upgrades are requested.
Skipping libcupsimage2-dev, it is not installed and only upgrades are requested.
Skipping libcupsmime1, it is not installed and only upgrades are requested.
Skipping libcupsmime1-dev, it is not installed and only upgrades are requested.
Skipping libcupsppdc1, it is not installed and only upgrades are requested.
Skipping libcupsppdc1-dev, it is not installed and only upgrades are requested.
Skipping cups-browsed, it is not installed and only upgrades are requested.
Skipping cups-filters, it is not installed and only upgrades are requested.
Skipping cups-filters-core-drivers, it is not installed and only upgrades are requested.
Skipping libcupsfilters-dev, it is not installed and only upgrades are requested.
Skipping printer-driver-hpcups, it is not installed and only upgrades are requested.
Reinstallation of cups-client is not possible, it cannot be downloaded.
Reinstallation of libcupsfilters1 is not possible, it cannot be downloaded.
Reinstallation of cups-common is not possible, it cannot be downloaded.
Reinstallation of libcups2 is not possible, it cannot be downloaded.
Reinstallation of python-cupshelpers is not possible, it cannot be downloaded.
Reinstallation of cups-bsd is not possible, it cannot be downloaded.
Reinstallation of libcupsimage2 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 54,0 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 


---

### Post by schragge on 2014-12-25
> Reinstallation of cups-client is not possible, it cannot be downloaded.
Well, I guess that's because --reinstall refuses downgrade anything. But just to be sure that trusty is really in you sources, could you please post the output of
```
grep '^[^#]' /etc/apt/sources.list
```
Regardless, try it without --reinstall
```
sudo apt-get -t trusty --only-upgrade install '[c]ups'
```

---

### Post by maiandros on 2014-12-25
> **schragge said:**
>  Well, I guess that's because --reinstall refuses downgrade anything. But just to be sure that trusty is really in you sources, could you please post the output of
```
grep '^[^#]' /etc/apt/sources.list
```  

Here is my source list:
>  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://debian.yeasoft.net/btsync](http://debian.yeasoft.net/btsync) trusty main
deb [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) trusty main
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb [http://www.bunkus.org/ubuntu/trusty/](http://www.bunkus.org/ubuntu/trusty/) ./
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main
deb-src [http://debian.yeasoft.net/btsync](http://debian.yeasoft.net/btsync) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://www.bunkus.org/ubuntu/trusty/](http://www.bunkus.org/ubuntu/trusty/) ./
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main  


> **schragge said:**
>  Regardless, try it without --reinstall
```
sudo apt-get -t trusty --only-upgrade install '[c]ups'
```  

And again...nothing changes...I don`t get it! CUPS is a service that is preinstalled in the Distro,right? Why is it so difficult to retrieve it?
>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'mfc465cncupswrapper' for regex '[c]ups'
Note, selecting 'dcp9042cdncups' for regex '[c]ups'
Note, selecting 'cupsddk' for regex '[c]ups'
Note, selecting 'cupswrapperdcp110c' for regex '[c]ups'
Note, selecting 'hl4050cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8820d' for regex '[c]ups'
Note, selecting 'cupswrapperfax2900' for regex '[c]ups'
Note, selecting 'cups-core-drivers' for regex '[c]ups'
Note, selecting 'cups-server-common' for regex '[c]ups'
Note, selecting 'dcp540cncupswrapper' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-laser' for regex '[c]ups'
Note, selecting 'cupswrapperfax2920' for regex '[c]ups'
Note, selecting 'cupswrapperhl2070n' for regex '[c]ups'
Note, selecting 'cupswrappermfc8420' for regex '[c]ups'
Note, selecting 'cupswrapperhl5240' for regex '[c]ups'
Note, selecting 'mfc850cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax3800' for regex '[c]ups'
Note, selecting 'cupswrapperfax1840c' for regex '[c]ups'
Note, selecting 'hl4050cdncups' for regex '[c]ups'
Note, selecting 'dcp130ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax1920cn' for regex '[c]ups'
Note, selecting 'cupswrappermfc8440' for regex '[c]ups'
Note, selecting 'mfc9440cncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl6050d' for regex '[c]ups'
Note, selecting 'dcp9040cncupswrapper' for regex '[c]ups'
Note, selecting 'gnuspool-cupspy' for regex '[c]ups'
Note, selecting 'cupswrappermfc9800' for regex '[c]ups'
Note, selecting 'cupswrapperhl1430' for regex '[c]ups'
Note, selecting 'python3-cups' for regex '[c]ups'
Note, selecting 'cupswrapperdcp1000' for regex '[c]ups'
Note, selecting 'dcp750cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1440' for regex '[c]ups'
Note, selecting 'dcp9045cdncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1670n' for regex '[c]ups'
Note, selecting 'cupsys-client' for regex '[c]ups'
Note, selecting 'cupswrapperhl1450' for regex '[c]ups'
Note, selecting 'cupswrappermfc7420' for regex '[c]ups'
Note, selecting 'hl4040cncups' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-extra' for regex '[c]ups'
Note, selecting 'mfc845cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp310cn' for regex '[c]ups'
Note, selecting 'libcups2-dev' for regex '[c]ups'
Note, selecting 'cupswrappermfc5840cn' for regex '[c]ups'
Note, selecting 'libcups2' for regex '[c]ups'
Note, selecting 'python-cups' for regex '[c]ups'
Note, selecting 'cups-daemon' for regex '[c]ups'
Note, selecting 'cupswrappermfc9860' for regex '[c]ups'
Note, selecting 'cupswrapperfax2820' for regex '[c]ups'
Note, selecting 'mfc235ccupswrapper' for regex '[c]ups'
Note, selecting 'mfc9440cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5130' for regex '[c]ups'
Note, selecting 'libcupsmime1' for regex '[c]ups'
Note, selecting 'cups-client' for regex '[c]ups'
Note, selecting 'cupswrappermfc9880' for regex '[c]ups'
Note, selecting 'cupswrapperhl5140' for regex '[c]ups'
Note, selecting 'mfc5460cncupswrapper' for regex '[c]ups'
Note, selecting 'libcupsimage2' for regex '[c]ups'
Note, selecting 'dcp9042cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax2850' for regex '[c]ups'
Note, selecting 'dcp150ccupswrapper' for regex '[c]ups'
Note, selecting 'mfc9420cncups' for regex '[c]ups'
Note, selecting 'fax2480ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc9700' for regex '[c]ups'
Note, selecting 'cupswrapperfax4100' for regex '[c]ups'
Note, selecting 'cupswrappermfc210c' for regex '[c]ups'
Note, selecting 'cups' for regex '[c]ups'
Note, selecting 'cups-backend-bjnp' for regex '[c]ups'
Note, selecting 'cupswrapperdcp1400' for regex '[c]ups'
Note, selecting 'cupswrapperhl5170dn' for regex '[c]ups'
Note, selecting 'libcupsimage2-dev' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8020' for regex '[c]ups'
Note, selecting 'fax1860ccupswrapper' for regex '[c]ups'
Note, selecting 'cups-pk-helper' for regex '[c]ups'
Note, selecting 'bluez-cups' for regex '[c]ups'
Note, selecting 'cupswrapperhl6050' for regex '[c]ups'
Note, selecting 'cupswrapperfax1835c' for regex '[c]ups'
Note, selecting 'cupswrappermfc8660dn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1850' for regex '[c]ups'
Note, selecting 'dcp153ccupswrapper' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-bh7' for regex '[c]ups'
Note, selecting 'gkrellmapcupsd' for regex '[c]ups'
Note, selecting 'dcp560cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8040' for regex '[c]ups'
Note, selecting 'dcp9040cncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1470n' for regex '[c]ups'
Note, selecting 'mfc440cncupswrapper' for regex '[c]ups'
Note, selecting 'libcupsmime1-dev' for regex '[c]ups'
Note, selecting 'cupswrapperhl5280dw' for regex '[c]ups'
Note, selecting 'cupswrappermfc9760' for regex '[c]ups'
Note, selecting 'cupswrappermfc420cn' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8060' for regex '[c]ups'
Note, selecting 'cupswrapperhl5030' for regex '[c]ups'
Note, selecting 'dcp330ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7010' for regex '[c]ups'
Note, selecting 'cupswrappermfc3240c' for regex '[c]ups'
Note, selecting 'cupswrappermfc6800' for regex '[c]ups'
Note, selecting 'cups-driver-gutenprint' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8045d' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-laser1' for regex '[c]ups'
Note, selecting 'cupswrapperhl5040' for regex '[c]ups'
Note, selecting 'cupsys-bsd' for regex '[c]ups'
Note, selecting 'cups-browsed' for regex '[c]ups'
Note, selecting 'cupswrapperfax1820c' for regex '[c]ups'
Note, selecting 'cups-pdf' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7020' for regex '[c]ups'
Note, selecting 'cupswrapperdcp7025' for regex '[c]ups'
Note, selecting 'fax2580ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5050' for regex '[c]ups'
Note, selecting 'hl4070cdwcups' for regex '[c]ups'
Note, selecting 'cups-filters-core-drivers' for regex '[c]ups'
Note, selecting 'python2.7-cups' for regex '[c]ups'
Note, selecting 'hl4040cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax4750e' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8065dn' for regex '[c]ups'
Note, selecting 'hl4040cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5270dn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1230' for regex '[c]ups'
Note, selecting 'mfc230ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc5440cn' for regex '[c]ups'
Note, selecting 'cups-bsd' for regex '[c]ups'
Note, selecting 'fax1960ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc410cn' for regex '[c]ups'
Note, selecting 'cupswrapperhl5070n' for regex '[c]ups'
Note, selecting 'mfc860cdncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1240' for regex '[c]ups'
Note, selecting 'cupswrappermfc3340cn' for regex '[c]ups'
Note, selecting 'cupswrapperhl1250' for regex '[c]ups'
Note, selecting 'cupswrappermfc7220' for regex '[c]ups'
Note, selecting 'mfc885cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8840d' for regex '[c]ups'
Note, selecting 'apcupsd-doc' for regex '[c]ups'
Note, selecting 'cupswrappermfc8870dw' for regex '[c]ups'
Note, selecting 'libcupscgi1' for regex '[c]ups'
Note, selecting 'cupswrappermfc9160' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-mfc9420cn' for regex '[c]ups'
Note, selecting 'mfc665cwcupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc3420c' for regex '[c]ups'
Note, selecting 'cupswrappermfc9660' for regex '[c]ups'
Note, selecting 'hl4040cdncups' for regex '[c]ups'
Note, selecting 'mfc240ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl1270n' for regex '[c]ups'
Note, selecting 'cupswrappermfc7225n' for regex '[c]ups'
Note, selecting 'libcupscgi1-dev' for regex '[c]ups'
Note, selecting 'cupswrappermfc3820cn' for regex '[c]ups'
Note, selecting 'cups-filters' for regex '[c]ups'
Note, selecting 'mfc9450cdncupswrapper' for regex '[c]ups'
Note, selecting 'apcupsd-cgi' for regex '[c]ups'
Note, selecting 'mfc685cwcupswrapper' for regex '[c]ups'
Note, selecting 'cups-tea4cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc9180' for regex '[c]ups'
Note, selecting 'hl4070cdwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp350ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax5750e' for regex '[c]ups'
Note, selecting 'cupswrappermfc8460n' for regex '[c]ups'
Note, selecting 'libcupsppdc1' for regex '[c]ups'
Note, selecting 'printer-driver-hpcups' for regex '[c]ups'
Note, selecting 'libcupsfilters-dev' for regex '[c]ups'
Note, selecting 'ghostscript-cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc4800' for regex '[c]ups'
Note, selecting 'mfc660cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc8860dn' for regex '[c]ups'
Note, selecting 'apcupsd' for regex '[c]ups'
Note, selecting 'cupswrapperfax2440c' for regex '[c]ups'
Note, selecting 'cups-common' for regex '[c]ups'
Note, selecting 'mfc680cncupswrapper' for regex '[c]ups'
Note, selecting 'dcp353ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc9030' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-ac' for regex '[c]ups'
Note, selecting 'cupswrapperhl5250dn' for regex '[c]ups'
Note, selecting 'cupswrappermfc620cn' for regex '[c]ups'
Note, selecting 'mfc460cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperfax1815c' for regex '[c]ups'
Note, selecting 'cupswrapperhl1650' for regex '[c]ups'
Note, selecting 'brother-cups-wrapper-common' for regex '[c]ups'
Note, selecting 'mfc630cdcupswrapper' for regex '[c]ups'
Note, selecting 'libcupsppdc1-dev' for regex '[c]ups'
Note, selecting 'dcp135ccupswrapper' for regex '[c]ups'
Note, selecting 'cupswrappermfc3320cn' for regex '[c]ups'
Note, selecting 'python-cupshelpers' for regex '[c]ups'
Note, selecting 'ghostcript-cups' for regex '[c]ups'
Note, selecting 'cupswrapperhl2030' for regex '[c]ups'
Note, selecting 'libnet-cups-perl' for regex '[c]ups'
Note, selecting 'cups-dbg' for regex '[c]ups'
Note, selecting 'mfc5860cncupswrapper' for regex '[c]ups'
Note, selecting 'cupswrapperhl5150d' for regex '[c]ups'
Note, selecting 'cupswrappermfc8500' for regex '[c]ups'
Note, selecting 'cupswrapperhl2040' for regex '[c]ups'
Note, selecting 'cups-ppdc' for regex '[c]ups'
Note, selecting 'cupswrappermfc7820n' for regex '[c]ups'
Note, selecting 'cupswrappermfc9070' for regex '[c]ups'
Note, selecting 'mfc3360ccupswrapper' for regex '[c]ups'
Note, selecting 'dcp9045cdncupswrapper' for regex '[c]ups'
Note, selecting 'mfc260ccupswrapper' for regex '[c]ups'
Note, selecting 'cupsomatic-ppd' for regex '[c]ups'
Note, selecting 'cupswrapperfax1940cn' for regex '[c]ups'
Note, selecting 'hplip-cups' for regex '[c]ups'
Note, selecting 'cupswrappermfc3220c' for regex '[c]ups'
Note, selecting 'cupswrapperdcp8025d' for regex '[c]ups'
Note, selecting 'mfc9840cdwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp750cwcupswrapper' for regex '[c]ups'
Note, selecting 'dcp770cwcupswrapper' for regex '[c]ups'
Note, selecting 'mfc9450cdncups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1030' for regex '[c]ups'
Note, selecting 'libcupsfilters1' for regex '[c]ups'
Note, selecting 'mfc9840cdwcups' for regex '[c]ups'
Note, selecting 'cupswrapperhl1870n' for regex '[c]ups'
Note, selecting 'cups-filters' instead of 'ghostscript-cups'
Note, selecting 'python-cups' instead of 'python2.7-cups'
Skipping bluez-cups, it is not installed and only upgrades are requested.
Skipping cups-driver-gutenprint, it is not installed and only upgrades are requested.
Skipping cups-pk-helper, it is not installed and only upgrades are requested.
python-cups is already the newest version.
Skipping apcupsd, it is not installed and only upgrades are requested.
Skipping apcupsd-cgi, it is not installed and only upgrades are requested.
Skipping apcupsd-doc, it is not installed and only upgrades are requested.
Skipping cups-backend-bjnp, it is not installed and only upgrades are requested.
Skipping cups-pdf, it is not installed and only upgrades are requested.
Skipping cups-tea4cups, it is not installed and only upgrades are requested.
Skipping gkrellmapcupsd, it is not installed and only upgrades are requested.
Skipping gnuspool-cupspy, it is not installed and only upgrades are requested.
Skipping libnet-cups-perl, it is not installed and only upgrades are requested.
Skipping python3-cups, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-ac, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-bh7, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-common, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-extra, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-laser, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-laser1, it is not installed and only upgrades are requested.
Skipping brother-cups-wrapper-mfc9420cn, it is not installed and only upgrades are requested.
Skipping cups, it is not installed and only upgrades are requested.
Skipping cups-core-drivers, it is not installed and only upgrades are requested.
Skipping cups-daemon, it is not installed and only upgrades are requested.
Skipping cups-dbg, it is not installed and only upgrades are requested.
Skipping cups-ppdc, it is not installed and only upgrades are requested.
Skipping cups-server-common, it is not installed and only upgrades are requested.
Skipping libcups2-dev, it is not installed and only upgrades are requested.
Skipping libcupscgi1, it is not installed and only upgrades are requested.
Skipping libcupscgi1-dev, it is not installed and only upgrades are requested.
Skipping libcupsimage2-dev, it is not installed and only upgrades are requested.
Skipping libcupsmime1, it is not installed and only upgrades are requested.
Skipping libcupsmime1-dev, it is not installed and only upgrades are requested.
Skipping libcupsppdc1, it is not installed and only upgrades are requested.
Skipping libcupsppdc1-dev, it is not installed and only upgrades are requested.
Skipping cups-browsed, it is not installed and only upgrades are requested.
Skipping cups-filters, it is not installed and only upgrades are requested.
Skipping cups-filters-core-drivers, it is not installed and only upgrades are requested.
Skipping libcupsfilters-dev, it is not installed and only upgrades are requested.
Skipping printer-driver-hpcups, it is not installed and only upgrades are requested.
cups-client is already the newest version.
libcupsfilters1 is already the newest version.
cups-common is already the newest version.
libcups2 is already the newest version.
python-cupshelpers is already the newest version.
cups-bsd is already the newest version.
libcupsimage2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

---

### Post by schragge on 2014-12-25
Hmm, you sources.list looks OK. Could you please also post the output of
```
dpkg -l '*cups*'|colrm 60
```
and
```
apt-cache policy libcups2
```
Next, we'll try to downgrade libcups2 by pinning it to a specific version, but for that I should know what versions of the package are available.

---

### Post by maiandros on 2014-12-25
> **schragge said:**
> Hmm, you sources.list looks OK. Could you please also post the output of
```
dpkg -l '*cups*'|colrm 60
```

Here are the results from the first comand:

> Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/t
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                   
+++-=======================================================
un  apcupsd                                                
un  bluez-cups                                             
un  cups                                                   
ii  cups-bsd                                               
ii  cups-client                                            
ii  cups-common                                            
un  cups-filters                                           
un  cups-pk-helper                                         
un  hplip-cups                                             
ii  libcups2:amd64                                         
ii  libcups2:i386                                          
ii  libcupsfilters1:amd64                                  
ii  libcupsimage2:amd64                                    
ii  python-cups                                            
ii  python-cupshelpers                                     
un  python2.7-cups 


And here is the outcome of the second comand:

> **schragge said:**
> ```
apt-cache policy libcups2
```
Next, we'll try to downgrade libcups2 by pinning it to a specific version, but for that I should know what versions of the package are available.

> libcups2:
  Installed: 1.7.2-0ubuntu1.3
  Candidate: 1.7.2-0ubuntu1.3
  Version table:
 *** 1.7.2-0ubuntu1.3 0
        100 /var/lib/dpkg/status
     1.7.2-0ubuntu1.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.7.2-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


---

### Post by schragge on 2014-12-25
Ok. Now try this
```

sudo dpkg --remove libcups2:i386
sudo apt-get install libcups2=1.7.2-ubuntu1.2 cups

```

---

### Post by maiandros on 2014-12-25
> **schragge said:**
> Ok. Now try this
```

sudo dpkg --remove libcups2:i386
sudo apt-get install libcups2=1.7.2-ubuntu1.2 cups

``` 

It has removed libcups2:
> (Reading database ... 489390 files and directories currently installed.)
Removing libcups2:i386 (1.7.2-0ubuntu1.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...

But when it comes to installing I`ve faced a problem:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.7.2-ubuntu1.2' for 'libcups2' was not found


Before we continue I would like to thank you very much for your effort to help me.

---

### Post by schragge on 2014-12-25
Sorry, my fault. That should have been
```
sudo apt-get install libcups2=1.7.2-[color=red]0[/color]ubuntu1.2 cups
```

---

### Post by maiandros on 2014-12-25
> **schragge said:**
> Sorry, my fault. That should have been
```
sudo apt-get install libcups2=1.7.2-[COLOR=red]0[/COLOR]ubuntu1.2 cups
```

No it`s not your fault...I`m one step away from punching my machine:mad:!!!
Yet again the same errors: 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cups : Depends: libcupsimage2 (>= 1.4.0) but it is not going to be installed
        Depends: cups-core-drivers (>= 1.7.2-0ubuntu1.2)
        Depends: ghostscript (>= 9.02~)
        Depends: cups-client (>= 1.7.2-0ubuntu1.2)
        Depends: cups-filters (>= 1.0.24-3~) but it is not going to be installed
        Recommends: cups-filters (>= 1.0.42) but it is not going to be installed or
                    foomatic-filters (>= 4.0)
        Recommends: printer-driver-gutenprint but it is not going to be installed
        Recommends: cups-filters (>= 1.0.36) but it is not going to be installed or
                    ghostscript-cups (>= 9.02~)
E: Unable to correct problems, you have held broken packages.


What if I try during boot up to clean Broken packeges? Would it make any difference?

---

### Post by schragge on 2014-12-25
No, booting up won't make any difference. What however will is updating the APT database to the latest state:
[
OK. Let's try doing this one by one.

First, update the APT database:
```
sudo apt-get update
```

Next, try (just in case it didn't work last time):
```
sudo apt-get install libcups2=1.7.2-0ubuntu1.2
```

Then
```
sudo apt-get -f install cups
```
It may fail, but perhaps we'll get different and more useful output.

Lastly, let's figure out what packages are still broken:
```
dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p'
```

Yes, it can sometimes be very frustrating.

---

### Post by maiandros on 2014-12-25
> **schragge said:**
> [B]No, booting up won't make any difference. What however will is updating the APT database to the latest state:
OK. Let's try doing this one by one.[/B]

**First, update the APT database:**
```
sudo apt-get update
```

Ok...I did it!

> **schragge said:**
> **Next, try (just in case it didn't work last time):**
```
sudo apt-get install libcups2=1.7.2-0ubuntu1.2
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  eom eom-common ffmpegthumbnailer gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-gtk-2.0 gir1.2-mate-panel gir1.2-rest-0.7 gir1.2-tracker-0.16
  gir1.2-zpj-0.0 gnome-online-miners grilo-plugins-0.2 libcpufreq0
  libdmapsharing-3.0-2 libffmpegthumbnailer4 libgrilo-0.2-1
  libgssapi-krb5-2:i386 libgupnp-av-1.0-2 libiptcdata0 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 libmediaart-1.0-0
  libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0
  libzapojit-0.0-0 mate-applets mate-applets-common mate-calc mate-calc-common
  mate-media mate-media-common mate-media-gstreamer mate-power-manager
  mate-power-manager-common mate-screensaver mate-screensaver-common
  mate-system-monitor mate-themes mate-utils mate-utils-common pluma
  pluma-common tracker ubuntu-wallpapers
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lprng
Suggested packages:
  magicfilter lprng-doc
The following packages will be REMOVED:
  atril cups-bsd cups-client evince ghostscript ghostscript-x gimp
  gimp-brushes gimp-scripts gir1.2-evince-3.0 gnome-documents gnome-sushi
  libcupsimage2 libevdocument3-4 libevview3-3 libgs9 libspectre1
  mate-desktop-environment printer-driver-pnm2ppa ubuntu-gnome-desktop
  ultimate-edition-installation-guide
The following NEW packages will be installed:
  lprng
The following packages will be DOWNGRADED:
  libcups2
0 upgraded, 1 newly installed, 1 downgraded, 21 to remove and 1 not upgraded.
Need to get 1369 kB of archives.
After this operation, 147 MB disk space will be freed.
Do you want to continue? [Y/n]  

Should I proceed? I mean autoremove/downgrade/install? I`m afraid that by trying to install CUPS i might mess up some other software...


> **schragge said:**
> [B]Then
[/B]```
sudo apt-get -f install cups
```[B]
It may fail, but perhaps we'll get different and more useful output.[/B]

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cups : Depends: libcups2 (= 1.7.2-0ubuntu1.2) but 1.7.2-0ubuntu1.3 is to be installed
        Depends: libcupscgi1 (>= 1.4.2) but it is not going to be installed
        Depends: libcupsmime1 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsppdc1 (>= 1.4.0) but it is not going to be installed
        Depends: cups-core-drivers (>= 1.7.2-0ubuntu1.2)
        Depends: cups-daemon (>= 1.7.2-0ubuntu1.2)
        Depends: cups-ppdc
        Depends: cups-filters (>= 1.0.24-3~) but it is not going to be installed
        Recommends: cups-filters (>= 1.0.42) but it is not going to be installed or
                    foomatic-filters (>= 4.0)
        Recommends: printer-driver-gutenprint but it is not going to be installed
        Recommends: cups-filters (>= 1.0.36) but it is not going to be installed or
                    ghostscript-cups (>= 9.02~)
E: Unable to correct problems, you have held broken packages. 

I think that the outcome is the same...perhaps you can find something different from the differnt posts but to me they seem identical.


> **schragge said:**
> **Lastly, let's figure out what packages are still broken:**
```
dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p'
``` 

> | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
||/ Name                                                        Version       
+++-===========================================================-==============
rc  anjuta-common                                               2:3.10.2-0ubun
rc  guile-2.0-libs                                              2.0.9+1-1ubunt
rc  libanjuta-3-0                                               2:3.10.2-0ubun
rc  libcairo-script-interpreter2:amd64                          1.13.0~2014020
rc  libcdr-0.0-0                                                0.0.15-1ubuntu
rc  libcups2:i386                                               1.7.2-0ubuntu1
rc  libfsplib0                                                  0.11-2        
rc  libgdl-3-5:amd64                                            3.8.1-2ubuntu1
rc  libgladeui-2-6                                              3.16.1-0ubuntu
rc  libgpod4:amd64                                              0.8.3-4ubuntu3
rc  libgssapi-krb5-2:i386                                       1.12+dfsg-2ubu
rc  libharfbuzz-gobject0:amd64                                  0.9.27-1ubuntu
rc  libk5crypto3:i386                                           1.12+dfsg-2ubu
rc  libkeyutils1:i386                                           1.5.6-1       
rc  libkrb5-3:i386                                              1.12+dfsg-2ubu
rc  libkrb5support0:i386                                        1.12+dfsg-2ubu
rc  libmikmod2:amd64                                            3.1.16-1      
rc  libmspub-0.0-0                                              0.0.6-1ubuntu2
rc  libopenvg1-mesa:amd64                                       10.4.0~git2014
rc  liborcus-0.6-0                                              0.5.1-7       
rc  libportmidi0                                                1:200-0ubuntu3
rc  libsdl-mixer1.2:amd64                                       1.2.12-10     
rc  libsdl-ttf2.0-0:amd64                                       2.0.11-3      
rc  libsmpeg0:amd64                                             0.4.5+cvs20030
rc  libtimezonemap1                                             0.4.1         
rc  libtorrent-rasterbar7                                       0.16.13-1ubunt
rc  libtre5:amd64                                               0.8.0-3ubuntu1
rc  libvisio-0.0-0                                              0.0.31-1ubuntu
rc  nvidia-libopencl1-304                                       304.125-0ubunt
rc  python3-gi-cairo                                            3.12.0-1ubuntu
rc  xbmc                                                        3:13.2-1~ppa1~




> **schragge said:**
> **Yes, it can sometimes be very frustrating.**
VERY...VERY frustrating! Thanks for your support!

---

### Post by schragge on 2014-12-25
Hmm, packages that were allowed for autoremoval are no problem, they stay intact anyway until explicitly removed with *apt-get autoremove*, but we absolutely do not want *lprng* to be installed as it will force removal of *cups-client* and many other packages with it.

Let's try it this way
```
sudo apt-get install {libcups2,cups-{bsd,client}}=1.7.2-0ubuntu1.2 lprng-
```
This should downgrade libcups2 and eventually also cups-bsd and cups-client, but prevent installation of lprng.

---

