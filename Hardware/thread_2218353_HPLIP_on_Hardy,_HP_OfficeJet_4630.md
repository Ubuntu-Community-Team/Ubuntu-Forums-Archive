---
title: "HPLIP on Hardy, HP OfficeJet 4630"
date: 2014-04-20
forum: Hardware
---

### Post by x1a4 on 2014-04-20
Hello:


I need to get the **HP OfficeJet 4630** all-in-one printer to work on Xubuntu Hardy.  I downloaded HPLIP 3.14.4 but the installer requires dependencies not available in the Hardy repos.  Is there a way to perhaps get an older version of HPLIP which supports this printer?  Or perhaps some way to install the dependencies without breaking Hardy?  The dependencies needed are:  libusb-1.0.0-dev, libcupsimage2-dev, libsnmp-dev, snmp-mibs-downloader, avahi-utils, libdbus-1-dev, libsane-dev, sane-utils, gtk2-engines-pixbuf, xsane.  

Thank you kindly for any help.

---

### Post by mörgæs on 2014-04-20
Hardy is out of support and has been that for many years. I recommend a fresh install of a supported version.

---

### Post by x1a4 on 2014-04-20
Thank you for your reply.  Unfortunatelly installing anything newer than Hardy is not an option on this box.  I would like to, but I can't.  So, is there any way to get the OfficeJet 4630 to work on Hardy, or am I stuck with my old printer?

---

### Post by mörgæs on 2014-04-20
> **x1a4 said:**
> Unfortunatelly installing anything newer than Hardy is not an option on this box.

Why? Please post a complete hardware description.

---

### Post by tgalati4 on 2014-04-21
Open a browser:  [http://localhost:631](http://localhost:631)

Try installing your printer.  If the exact printer driver is not found, then select one that looks close.

---

### Post by x1a4 on 2014-04-21
> **mörgæs said:**
> Why? Please post a complete hardware description.

It's nothing to do with hardware.  There are features in Hardy that I need but no new OS has.  For example, I can configure my virtual terminals to have 4 TTYs and 3 log-in screens on boot.  Another reason I don't want to upgrade the OS is that some users of this computer are not computer savvy.  Things are configured the way they like it, the way is has been for years, and they don't want to change.  

As for the specs it's a 32-bit desktop with an AMD Sempron 2400+ processor, 2GB of RAM, 500GB of storage, nVidia GeForce 6200 video and Creative SoundBlaster Live! sound card.

---

### Post by x1a4 on 2014-04-21
> **tgalati4 said:**
> Open a browser:  [http://localhost:631](http://localhost:631)

Try installing your printer.  If the exact printer driver is not found, then select one that looks close.

Already tried that.  Didn't work.  Thanks though.

---

### Post by Yellow Pasque on 2014-04-21
>  Is there a way to perhaps get an older version of HPLIP which supports this printer?
The oldest version you can use with that printer is 3.13.9, which isn't very old and probably has the same requirements.

---

### Post by mastablasta on 2014-04-22
> **x1a4 said:**
> For example, I can configure my virtual terminals to have 4 TTYs 


use terminator ?

> 
and 3 log-in screens on boot. 


i am not sure what this means or why this would be good.

i would give latest Xubuntu 14.04 a try. at least a live session.

---

### Post by mörgæs on 2014-04-22
> **x1a4 said:**
> Things are configured the way they like it, the way is has been for years, and they don't want to change.  

- but maybe they want an updated system which is safe from attack. Are they aware that there's no security in an obsolete version of Buntu?

---

### Post by tgalati4 on 2014-04-22
I'm running 12.10 and it has version 3.12 of hplip:

tgalati4@Mint14-Extensa ~ $ apt-cache policy hplip
hplip:
  Installed: 3.12.6-3ubuntu4.3
  Candidate: 3.12.6-3ubuntu4.3
  Version table:
 *** 3.12.6-3ubuntu4.3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.12.6-3ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

You may be able to manually install the driver for that printer, but *hplip* is needed to get access to some network/workgroup functions.

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

[http://hplipopensource.com/hplip-web/models/officejet/officejet_4630_series.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_4630_series.html)

---

### Post by mörgæs on 2014-04-22
12.10 is either very close to or already out of support.

---

