---
title: "How to install Epson ET-3700"
date: 2019-11-26
forum: Hardware
---

### Post by mblossom on 2019-11-26
I am running Ubuntu 18.04.1 on a  PC with Intel Core2 Duo.

Trying to install an Epson ET-3700.

System searches for but is unable to find correct driver.

Epson lists drivers to download for Ubuntu here:

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=101986&DSCCHK=f880793699494616468653a80e2575418d70ea49](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=101986&DSCCHK=f880793699494616468653a80e2575418d70ea49)

... with the following options:

[TABLE="align: center"]
[TR]
[TD="align: left"]epson-inkjet-printer-escpr2_1.1.2-1lsb3.2_i386.deb[/TD]
[TD]1.86 MB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: left"]epson-inkjet-printer-escpr2-1.1.2-1lsb3.2.x86_64.rpm[/TD]
[TD]1.66 MB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: left"]epson-inkjet-printer-escpr2_1.1.2-1lsb3.2_amd64.deb[/TD]
[TD]1.86 MB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: left"]epson-inkjet-printer-escpr2-1.1.2-1lsb3.2.src.rpm

[TABLE="align: center"]
[TR]
[TD="align: left"]epson-inkjet-printer-escpr2-1.1.2-1lsb3.2.i486.rpm[/TD]
[TD]1.66 MB[/TD]
[TD][/TD]
[/TR]
[/TABLE]
[/TD]
[TD]2.45 MB[/TD]
[TD][/TD]
[/TR]
[/TABLE]
[TABLE="align: center"]
[TR]
[TD="bgcolor: #CCCCCC, colspan: 3, align: left"]Information[/TD]
[/TR]
[TR]
[TD="colspan: 3, align: left"][Notice]
In order to install these drivers, you need to install LSB package (version 3.2 or later) beforehand.

Ubuntu:
# apt-get install lsb

Fedora: 
# yum install lsb

OpenSUSE:
# yast --install lsb[/TD]
[/TR]
[/TABLE]
     
   
    [TABLE="align: center"]
[TR]
[TD="align: left"][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]



... but I have no idea how to proceed.

Many thanks,

~Mark

---

### Post by mörgæs on 2019-11-27
Hi, welcome to the fora.

Please run the three commands 
```
sudo apt update
sudo apt dist-upgrade
sudo apt install lsb
```
one at a time and post the output in CODE tags.

---

### Post by brian_p on 2019-11-28
You do not need any vendor drivers to print with the ET-3700. Put the printer on the network and execute ```
driverless
``` to get a URI and substitute in ```
lpadmin -p et3700 -v URI -E - m everywhere
```

Test printing with ```
lp -d et3700 /etc/nsswitch.conf
```

All-in-all, a five minute task.

---

### Post by brian_p on 2019-12-01
The OP receives two quality responses and then doesn't respond. What a waste of everyone's time and effort!

---

