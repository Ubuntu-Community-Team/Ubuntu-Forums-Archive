---
title: "Brother DCP-135c Scanner only running under root"
date: 2015-01-11
forum: Hardware
---

### Post by marexel on 2015-01-11
[FONT=century gothic]Hello,

I am running Kubuntu 14.04 64bit and a Brother DCP-135c, printer works fine, the scanner too, but only under root. Another Scanner whatsoever is working fine (Medion MD6228, see below). I have already [posted]("http://forum.ubuntuusers.de/topic/dcp-135c-scannen-wiki-nicht-korrekt/") in a german forum but the reply wasn't helpful. I have already tried everything I found in forums and google, but nothing fixed the problem. So, here is some information:
 ```
marexel@flea:~$ dmesg
[ 1319.307358] usblp 2-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01CE
[ 1319.307400] usbcore: registered new interface driver usblp
[ 1320.110251] scsi 7:0:0:0: Direct-Access     Brother  DCP-135C         1.00 PQ: 0 ANSI: 2
[ 1320.113362] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 1320.191247] sd 7:0:0:0: [sdd] Attached SCSI removable disk
```
```
marexel@flea:~$ lsusb
Bus 002 Device 003: ID 04f9:01ce Brother Industries, Ltd DCP-135C

```
```
marexel@flea:~/.sane$ ls -la
insgesamt 332
drwx------  3 marexel marexel   4096 Mai 25  2014 .
drwxr-x--x 58 marexel marexel   4096 Jan 11 11:21 ..
-rw-------  1 marexel marexel 326950 Dez 14 17:44 medion-md5345-model.cal
drwx------  3 marexel marexel   4096 Dez  8 18:15 xsane

```
```
marexel@flea:~/.sane/xsane$ ls -la
insgesamt 36
drwx------ 3 marexel marexel 4096 Dez  8 18:15 .
drwx------ 3 marexel marexel 4096 Mai 25  2014 ..
drwx------ 2 marexel marexel 4096 Mai 25  2014 batch-lists
-rw------- 1 marexel marexel 1622 Jan  5 18:50 Brother:DCP-135C.drc
-rw------- 1 marexel marexel 1801 Dez 14 17:44 Medion:MD5345_MD6228_MD6471.drc
-rw------- 1 marexel marexel 4253 Jan  5 18:50 xsane.mdf
-rw------- 1 marexel marexel 5207 Jan  8 17:17 xsane.rc
```
According to the german [Wiki]("http://wiki.ubuntuusers.de/Brother/Scanner") an a [HowTo]("http://forum.ubuntuusers.de/topic/dcp-135c-fehlermeldung-brcupsconfpt1-crashed/#post-6329662") I edited /etc/lib/udev/rules.d/40-libsane.rules to ```
# Brother DCP-135c
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01ce", ENV{libsane_matched}="yes"

# The following rule will disable USB autosuspend for the device

```
But
```
marexel@flea:~/.sane/xsane$ sudo ldconfig
/sbin/ldconfig.real: /usr/lib/libbrcolm2.so.1 is not a symbolic link
/sbin/ldconfig.real: /usr/lib/libbrscandec2.so.1 is not a symbolic link
```
```
marexel@flea:~/.sane/xsane$ sudo vim /etc/sane.d/brother.conf

```[/FONT]```
[FONT=century gothic]# Brother USB
# For libusb support for unknown scanners use the following command
# usb <vendor ID> <product ID>
usb 04f901e9[/FONT]
```[FONT=century gothic]```
marexel@flea:~/.sane/xsane$ sudo vim /etc/sane.d/dll.conf
...
brother2
```[/FONT][FONT=century gothic]

It seems to be a rights-problem, which can be found a lot in forums, but I can't find a clue that helps me with my problem...
Can anyone help?
Thanks, kr,

marexel[/FONT]

---

### Post by plucky on 2015-01-11
Have you installed **sane-utils**?

```
sudo apt-get install sane-utils
``` 

Then reboot.

If that doesn't work then try running from a terminal ```
sudo chmod a+w /dev/bus/usb/002/003
``` should allow you to open simple-scan as a user.

Good Luck

---

### Post by marexel on 2015-01-14
Thanks for your hint, but I didn't need it.
Somehow the scanner works now. I didn't change anything - but an muon automatic-update...?
So, unfortunately I cannot give any advice...
Thanks for your help, kind regards,

marexel

---

