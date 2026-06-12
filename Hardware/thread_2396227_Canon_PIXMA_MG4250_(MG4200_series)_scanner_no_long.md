---
title: "Canon PIXMA MG4250 (MG4200 series) scanner no longer working."
date: 2018-07-12
forum: Hardware
---

### Post by makem2 on 2018-07-12
This scanner and printer were working with xubuntu 16.04 but after a reinstall of the same version due to some non-related corruption, it no longer works. My /home partition was retained during the re-install. The unit is networked and works from two windows machines and an S8 phone.

XSANE is installed. libsane1.0.26 is installed(via: [COLOR=#111111][FONT=Consolas]ppa:rolfbensch/sane-git)

The scanner is fully supported by SANE ([/FONT][/COLOR]http://www.sane-project.org/sane-mfgs.html#Z-CANON). There is a canon entry in /etc/sane.d/dll.conf

It is not mentioned in HardwareSupportComponentsScannersCanon but it did work. I am wondering if I need to compile from source this time.

I am not in any hurry at the moment as scans can be carried out from another machine, (I hate to let windows take over!) and as I intend to update to xubuntu 18 LTS later this month, perhaps I should wait and see if that fixes it.

I have uninstalled ufw temporarily.[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
```
makem@ssdTOSH:~$ scanimage -L
device `pixma:MG4200_192.168.2.24' is a CANON Canon PIXMA MG4200 multi-function peripheral
makem@ssdTOSH:~$ scanimage -T
scanimage: open of device pixma:MG4200_192.168.2.24 failed: Invalid argument
makem@ssdTOSH:~$ 
 
```

Printer properties: Canon MG4200 series - CUPS+Gutenprint v5.2.11

[COLOR=#222222][FONT=Verdana]Simple Scan: Failed to scanner. No scanners available.[/FONT]

[FONT=Verdana]XSANE: Failed to open device 'pixma:MG4200_192.168.2.24:Invalid argument.[/FONT]

[FONT=Verdana]Troubleshooting suggestions appreciated please, or to wait or not to wait for upgrade?

**EDIT**: [/FONT][/COLOR]saned.conf access list contains: 192.168.2.1/29

It also states: # NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and# /etc/services must also be properly configured to start

Both /etc/inetd.conf and /etc/xinetd.conf are not configured.

[B]I have installed the Gimp image processing program and from that I can scan!

[/B]Using the path: File/Create/Scangear MP.... menu option I am able to scan via WiFi.

If I use the path File/Create/Xsane menu option I get the '[FONT=Verdana]Invalid argument' error.

It is a pain to have to install a program to enable scanning.[/FONT]

---

### Post by RangerK on 2018-12-08
I also use xubuntu, but 18.04.  My Canon Pixma e414 can print, but not scan.

Interestingly, I see the scanner with I run

` sudo sane-find-scanner

but not when I run

` sane-find-scanner

I get permission errors.

How do you scan via Gimp?  I don't have a scangear menu option.

---

