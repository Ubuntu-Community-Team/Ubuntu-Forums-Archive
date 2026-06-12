---
title: "Cannot install Brother HL-2230"
date: 2014-03-16
forum: Hardware
---

### Post by Anthony_Day on 2014-03-16
I am having trouble installing my Brother HL-2230. I have installed the CUPSWRAPPER and LPR Drivers using the Brother Linux installation tool. It is connected via USB.  the Device URI: usb:/dev/usb/lp0 When I use the command tail -f /var/log/syslog I do not register any log activity plugging the printer in. I am out of ideas...

---

### Post by pdc on 2014-03-17
I guess if we check the brother drivers are installed:

> [COLOR="#FF0000"]dpkg -l | grep Brother[/COLOR]

and the printer is connected .............directly........or via a USB hub......and the port works fine by checking with another device? 

what does 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] give with the printer seemingly plugged in and turned on

---

### Post by Anthony_Day on 2014-03-20
ub-1@ub1-Dell-DV051:~$ dpkg -l | grep Brother
ii  cupswrapperhl2230                          2.0.4-2                                 Brother HL2230 CUPS wrapper driver
ii  hl2230lpr                                  2.1.0-1                                 Brother HL-2230 LPR driver
ii  printer-driver-ptouch                      1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

The USB port works, I have tried other devices to test it.

ub-1@ub1-Dell-DV051:~$ /usr/sbin/lpinfo -v
network https
network lpd
network smb
network http
network ipps
network ipp14
network ipp
network beh
network socket
direct hp
direct hpfax

---

### Post by gifford on 2014-03-20
If you are referring to the installation tool found here:[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625)
Your printer is not listed as a compatible model.
I would suggest going to the Brother site and following their instructions for installation of the cupswrapper and lpr drivers. It requires use of the command line but is always reliable.
Here is the link if you do not have it already.[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by Anthony_Day on 2014-03-20
I have already tried to manually install the printer cuppswrapper driver and lpr drivers.

---

### Post by pdc on 2014-03-20
when I do **NOT** have my Canon printer (usb-connection) turned on (but joined by usb and in sleep mode) I get

> $ /usr/sbin/lpinfo -v
network lpd
network ipps
network smb
network ipp14
network socket
network http
network https
direct ccp
network beh
network ipp
[COLOR="#0000FF"]direct parallel:/dev/lp0[/COLOR]


I notice you get

> $ /usr/sbin/lpinfo -v
network https
network lpd
network smb
network http
network ipps
network ipp14
network ipp
network beh
network socket
direct hp
direct hpfax 

..........so maybe you just didn't include it, but I would like to see dev/usb/lp0 mentioned 

when I turn the printer on, I get ........as well as the above

> direct cnijusb:/dev/usb/lp0
direct ccp
network ipp
network smb
direct usb://Canon/MG3100%20series?serial=402E18&interface=1


........so I am still wondering if your computer is seeing the printer 

another couple of commands from here 

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

(if you could copy and paste them, and then copy/paste back the results please)

> [COLOR="#FF0000"]ls -l /dev/usb/lp* /dev/bus/usb/*/*[/COLOR]

and 

> [COLOR="#FF0000"]sudo usb_printerid /dev/usb/lp0[/COLOR] 

_______________________________________--

cursory examination of here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2230](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2230) would suggest your printer drivers as installed are fine

---

