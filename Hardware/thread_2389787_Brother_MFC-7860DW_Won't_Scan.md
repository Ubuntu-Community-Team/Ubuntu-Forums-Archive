---
title: "Brother MFC-7860DW Won't Scan"
date: 2018-04-21
forum: Hardware
---

### Post by kamrynborden on 2018-04-21
My Dad is gave the OK to switch his computer over to Linux, however the only drawback is our multi-functioning printer+multi-pages-scanner+fax won't scan in Linux, regardless by USB or network and it never did; it only worked on Windows.
I'm sure he won't go for purchasing another printer-scanner. Is there a way to make it work? Has anyone had any success? What printer = multi-page scanners have you had success with?

Update: I somehow got it to the computer to recognise the scanner, when I try to scan, it says it can't start scan.

---

### Post by kurt18947 on 2018-04-22
What version of Ubuntu are you using? USB or network connection? Can you scan as a SUDO user? Brother support for Linux is pretty good. They do offer email support via their web site. There's no phone support for Linux. I currently have 2 Brother machines, multi-function inkjet & color laser and both work as expected.  If you're not aware of these pages, they can be useful. A fair amount of information is not relevant in modern Ubuntu such as the pre-install stuff but there's still good information there.
```
[http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)
```

---

### Post by him610 on 2018-04-22
I also own a Brother MFC machine. If your scanner function is not working, you are probably missing a couple scanner files from Brother.
You can determine if you have the necessary Brother software/drivers installed by running this command from a terminal, >  dpkg -l |grep Brother
Your output should resemble this... (note lines 3 and 4 of the response)
```

$ dpkg -l |grep Brother
ii  brmfcfaxcups:i386                             1.0.0-2                                                 i386         Brother MFC/FAX fax share function driver
ii  brmfcfaxlpd:i386                              1.0.0-2                                                  i386         Brother MFC-FAX LPD driver
ii  brscan-skey                                   0.2.4-1                                                  amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                       0.4.4-3                                                  amd64        Brother Scanner Driver
ii  cupswrappermfc7360n:i386                      2.0.4-2                                                  i386         Brother MFC7360N CUPS wrapper driver
ii  mfc7360nlpr:i386                              2.1.0-1                                                  i386         Brother MFC-7360N LPR driver
ii  printer-driver-brlaser                        3-5~ubuntu1                                              amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                         1.4-1                                                    amd64        printer driver Brother P-touch label printers

```

---

### Post by pedro_rodriguez2 on 2018-04-23
I also tried all the latest Linux drivers from Epson to get the scanner in my printer scanner going. Drove me crazy! The following worked for me:

Do this:

1. look here: [https://askubuntu.com/questions/5473...n-ubuntu-14-04]("https://askubuntu.com/questions/547364/canoscan-lide-120-on-ubuntu-14-04")
2. sudo add-apt-repository ppa:rolfbensch/sane-git 
3. sudo apt update
4. sudo apt -y install sane libsane libsane-common sane-utils libsane-extras

You may have to repeat 4. Some parts don't install the first time. Also, you may get a system problem error report on boot. 

BUT, my Epson L350 printer scanner works now, and my Canon 120 LiDE

I only bought the Canon because I could not get the Epson L350 printer  scanner to work! After getting the Canon to work with new repository  files, the Epson worked too!

I think it loads new things in /etc/sane.d/dll.d but I am not an expert!

I am very glad I found this info! Good Luck! Let me know if it works!

---

