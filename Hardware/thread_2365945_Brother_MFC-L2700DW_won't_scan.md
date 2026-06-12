---
title: "Brother MFC-L2700DW won't scan"
date: 2017-07-12
forum: Hardware
---

### Post by cackerso on 2017-07-12
I am running Kubuntu 16.04 with all the updates.  The Brother is on a home network.  It's a print, copy, scan printer.  I installed the most recent drivers from the Brother site.  It all seemed to go OK and the print part works fine.  I installed "Simple Scan" and when I run it I get the error message:  "Failed to Scan   Unable to connect to Scanner". Simple Scan does list the printer when I look under "Change Scanners". Looking at posts here I installed sane and xsane.  When I try the Xsane scanner I get a similar result.  The error is: "Failed to open device 'brother4:net1;dev0.' Invalid argument".

The used the command  "dpkg -l | grep Brother"  in a terminal and got:

```


ii  brother-udev-rule-type1                         1.0.0-1                                    all          Brother udev rule type 1
ii  brscan-skey                                     0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                         0.4.4-1                                    amd64        Brother Scanner Driver
ii  mfcl2700dwcupswrapper:i386                      3.2.0-1                                    i386         Brother MFC-L2700DW CUPS wrapper driver
ii  mfcl2700dwlpr:i386                              3.2.0-1                                    i386         Brother MFC-L2700DW LPR driver
ii  printer-driver-brlaser                          3-5~ubuntu1                                amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                           1.4-1                                      amd64        printer driver Brother P-touch label printers


```             

There are a lot of other posts about getting a scanner to work but I am not that facile in Linux and I don't want to just continue randomly trying solutions that may or may not be applicable.  I did have an HP printer installed previously and although I did delete it using the printer tool in KDE, HPLIP is still installed.  I have no idea if that makes any difference.        

I looked at these search suggested three links, maybe one of the solutions will work but I'd like some feedback first.  The first thread seems to be the most relevant.

    [https://ubuntuforums.org/showthread.php?t=2098408&highlight=Brother+MFC-L2700DW+won%27t+scan](https://ubuntuforums.org/showthread.php?t=2098408&highlight=Brother+MFC-L2700DW+won%27t+scan)
   [https://ubuntuforums.org/showthread.php?t=2251170&highlight=Brother+MFC-L2700DW+won%27t+scan](https://ubuntuforums.org/showthread.php?t=2251170&highlight=Brother+MFC-L2700DW+won%27t+scan)
   [https://ubuntuforums.org/showthread.php?t=2262935&highlight=Brother+MFC-L2700DW+won%27t+scan](https://ubuntuforums.org/showthread.php?t=2262935&highlight=Brother+MFC-L2700DW+won%27t+scan)

---

### Post by gifford on 2017-07-12
Try this in the terminal: brsaneconfig4 -q to see if you have the correct ip address listed for the scanner.

---

### Post by kurt18947 on 2017-07-12
The suggestion by gifford seems like a good place to start. After installing the Brother scanner driver, you must 'tell' the scanning software the I.P. address to use. I find it makes life simple to assign a static I.P. address to the printer/scanner. 

The Udev fix only applies on non-sudo users on machines on a USB connection I believe. The telling sign there is that the sudo user can scan, other users cannot. I find Brother network installs simpler than local/USB, you may just have to type that one line in a terminal.

---

### Post by cackerso on 2017-07-13
The output of "brsaneconfig4 -q" is:  

Devices on network
  0 MFC-L2700DW         "MFC-L2700DW"       I:192.168.0.103

If I check the IP address of the printer manually it shows:  192.168.000.101

So assume I need to change the IP address for the scanner in a file somewhere, unless there is some other way to do it in a terminal.

---

### Post by gifford on 2017-07-13
For me, using Ubuntu 14.04, the settings location is usr/local/brother/sane and the file is brsanenetdevice4.cfg, if it is the same for you, just change the address to be as for your printer.

---

### Post by cackerso on 2017-07-14
Thanks, that worked.  Except the file was in /opt/brother/scanner/

One last question.  When I run Simple Scan I get an error message from HPLIP which I had previously installed for an HP printer. It was replaced by the current Brother printer.  Can I safely purge HPLIP without screwing up the Brother installation?  I've already deleted the HP printer set up.

---

### Post by gifford on 2017-07-14
I think that would be fine and should not hurt the Brother installation. Glad you resolved the scanner issue.

---

