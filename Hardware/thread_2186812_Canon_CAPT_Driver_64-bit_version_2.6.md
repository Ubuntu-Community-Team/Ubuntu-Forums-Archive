---
title: "Canon CAPT Driver 64-bit version 2.6"
date: 2013-11-09
forum: Hardware
---

### Post by zKhtdyX on 2013-11-09
Hi,

there are numerous threads out there concerning canon capt printer driver issues. Especially getting printers working on 64-bit systems seemed to be very tricky in the past with that driver due to canon did offer only 32-bit *.deb-packages yet.

But version 2.6 released in July this year contains pre-compiled 64-bit deb packages for the first time!
[http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)

So I followed the installation instructions:
(for canon lbp3300 on ubuntu 12.04 64bit)

```

sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon

#Registered the printer:
sudo /usr/sbin/lpadmin -p LBP3300 -m CNCUPSLBP3300CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E                      
# Registered the printer with ccpd daemon.
sudo /usr/sbin/ccpdadmin -p LBP3300 -o /dev/usb/lp1
#Started ccpd daemon:
sudo /etc/init.d/ccpd start
#checked ccpd status
sudo /etc/init.d/ccpd status
-> /usr/sbin/ccpd: 4244 4240


```

But the printer does not print anything.

When I check "captstatusui -P LBP3300" it says "Check the DevicePath of /etc/ccpd.conf" but the device path of "/dev/usb/lp1" is the correct one.

Did get anyone managed a printer working the the new 64bit driver?
Maybe someone can help me to get this printer working.

---

### Post by heir4c on 2013-11-09
Why you use all that terminal-stuff if it is a .deb file?
To install the driver you download the .deb file. Go to the Download folder and rightclick on the tar.gz file and choose 'Unpack' (or something like that. I have a Dutch version of Ubuntu).
Than you see a folder with the name: Linux_CAPT_PrinterDriver_V260_uk_EN
Doubleclick on that. Doubleclick on the 64-bit_Driver folder.
Doubleclick on Debian folder.
Now you see 2 .deb packages: cndrvcups-capt_2.60-1_amd64.deb and: cndrvcups-common_2.60-1_amd64.deb
Doubleclick FIRST on the second .deb file cndrvcups-common-2.60-1-amd64.deb to install.
Then do the same with the first .deb file.
Normally UbuntuSoftwareCenter will used to install the .deb files. I install always gdebi to install .deb files. If you will use that too than you install this with the command:
```
sudo apt-get install gdebi
```
When you install now the .deb files you rightclick on the file and choose: "Open with:" and than choose "GDebi PackageInstaller"
It's easy and if there is a problem than you get a message/error.

After install the packages go to SystemSettings and the PrinterManager.

---

### Post by zKhtdyX on 2013-11-12
hi heir4c,

for this strange driver you have to ignore the printer settings in system settings or any automatically added printer.
Here is a documentation: [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

A more detailed one (French): [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

---

