---
title: "Epson Expression Home XP-2100 driver for Ubuntu 18.04"
date: 2019-11-13
forum: Hardware
---

### Post by Harix on 2019-11-13
Need to find driver for printer, scanner, copier Epson XP-2100. Anyone?
Thanks

---

### Post by brian_p on 2019-11-13
What is wrong with whatever you have on your Ubuntu system?

---

### Post by mörgæs on 2019-11-14
Please post the output of ```
apt-cache policy printer-driver-escpr
```

---

### Post by Harix on 2019-11-15
```
harix@harix-750:~$ apt-cache policy printer-driver-escpr
printer-driver-escpr:
  Installed: (none)
  Candidate: 1.6.17-2
  Version table:
     1.6.17-2 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
harix@harix-750:~$ 

```

---

### Post by mörgæs on 2019-11-16
As a first attempt I would try to use this driver rather than downloading from Epson or elsewhere: ```
sudo apt install printer-driver-escpr
```

If it fails then a clean install of 19.10 will bring you 1.6.33-1.

---

### Post by Harix on 2019-11-16
sudo apt install printer-driver-escpr
Yes, this worked! Can print with wifi.

```
$ apt-cache policy printer-driver-escpr
printer-driver-escpr:
  Installed: 1.6.17-2
  Candidate: 1.6.17-2
  Version table:
 *** 1.6.17-2 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

but not scan...other driver?

---

### Post by brian_p on 2019-11-16
You will have to look at [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) for a scanner driver.

---

