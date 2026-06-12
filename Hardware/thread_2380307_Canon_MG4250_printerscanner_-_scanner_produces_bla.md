---
title: "Canon MG4250 printer/scanner - scanner produces blank file"
date: 2017-12-15
forum: Hardware
---

### Post by makem2 on 2017-12-15
This machine is being used via wifi and used to scan with default installed software for xubuntu.

It now longer scans but the printer works. The installed 'simple scan'cannot find the scanner. I have tried xsane but that seems to work only with usb connected scanners.

I installed the driver from here:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100470302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470302.html)

This finds the printer using the terminal 'scangearmp' command. The selection page comes up allowing choices and then to scan. The machines makes one click and then does nothing although both it and the software say 'scanning'. The resulting file is empty.

---

### Post by sccman on 2017-12-15
Have you been able to scan with other computers? If you have, that can help tell us if it's a problem with your machine or if it's with the scanner itself.

---

### Post by makem2 on 2017-12-15
I have access tomorrow to a windows 10 machine. Thanks for that suggestion.

scangearmp2-3.00-1-deb.tar.gz appeared to be an update to the other driver so I installed that. It could not find the scanner but the first driver now produces a usable file. The preview is not available as it is still blank so cannot be adjusted until after the file is produced. At least I can scan now though.

I will see what windows makes of the scanner later and come back.

---

### Post by makem2 on 2017-12-16
The scanner scans correctly using a windows 10 machine.

---

### Post by pdc on 2017-12-16
so using the driver that Canon provides; does not help Simple-Scan "see" the scanner; as I understand it, they are quite separate; Canon provide a programme called ScanGearMP to run the scanners in its devices; and the link you gave is the correct version to download; 

scangearmp2 is a separate driver; for more recent devices;

I wondered if you had ".......upgraded......." to 17.10 .......... I ask as there have been quite a few reports of devices no longer working after the grade process. The next release will be 18.04 and it is to be LTS; so the goals should be stability; 

___________

the good folks at SANE; the open-source support for scanning; believe the MG4200 devices are completely supported; 

If you google on how to do a bug report in Ubuntu, you could report your problems as a bug; ( and don't install the scangearmp2 as that is NOT the correct programme ..)

---

### Post by makem2 on 2017-12-16
> **pdc said:**
> so using the driver that Canon provides; does not help Simple-Scan "see" the scanner; as I understand it, they are quite separate; Canon provide a programme called ScanGearMP to run the scanners in its devices; and the link you gave is the correct version to download; 

scangearmp2 is a separate driver; for more recent devices;

I wondered if you had ".......upgraded......." to 17.10 .......... I ask as there have been quite a few reports of devices no longer working after the grade process. The next release will be 18.04 and it is to be LTS; so the goals should be stability; 

___________

the good folks at SANE; the open-source support for scanning; believe the MG4200 devices are completely supported; 

If you google on how to do a bug report in Ubuntu, you could report your problems as a bug; ( and don't install the scangearmp2 as that is NOT the correct programme ..)

```

makem@ssdTOSH:~$ lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
makem@ssdTOSH:~$

```

I tried 17.10 and had so many problems I reinstalled 16.04 using my saved /home.

I will uninstall scangearmp2 and see if I can still scan. But in any case, being able to use the Windows machine is enough as I do very few scans.

I think I will wait for the new release as I don't fancy installing SANE again.

---

