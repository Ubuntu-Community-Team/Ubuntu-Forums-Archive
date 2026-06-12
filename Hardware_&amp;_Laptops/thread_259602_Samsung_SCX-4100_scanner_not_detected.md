---
title: "Samsung SCX-4100 scanner not detected"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by jomacfang on 2006-09-17
My Samsung SCX-4100 multifunction printer/scanner was working fine scanner and printer under Dapper (after a little Googling). Just upgraded to LTS 6.06 and now just the printer works. Sane can't find the scanner. I tried reinstalling the driver package "samsung-scx4100-drivers_1.0.165-1_i386.deb" and tried to change the permissions of /dev/usb/lp0 which worked before. Now, /dev/usb seems to have been removed so I repermissioned /dev/lp0. No go. Any sugesstions?

---

### Post by Sef on 2006-09-18
[Click here,]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-scx4100") it will take to the SCX 4100 page of LinuxPrinting.

---

### Post by radtek on 2007-02-01
After downloading the linux pacage from samsung it really was a simple setup once I opened the **install.sh** file with gedit and changed the:

```
#! /bin/sh
``` 

with

```
#! /bin/bash
```

I did this as well to the check_installation.sh, set_variables.sh, and uninstall.sh. I figured the installer would access them... probably isn't really necessary.

However, the install worked fine-- just manually place the driver if you have to before completing the installation.

[B]Scanner didn't work but I got it to by following this:
[/B]
Make sure you download the SANE libs through synaptic if you haven't already.

Add 2 lines like this to the end of /etc/udev/rules.d/45-libsane.rules before the LABEL="libsane_rules_end" line (based on output of sane-find-scanner) so that people in the "scanner" group and not only root can use the scanner. (You'll have to reboot after doing this.):

```

sudo gedit /etc/udev/rules.d/45-libsane.rules
``` 


```
# Samsung|SCX-4100 
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3413", MODE="664", GROUP="scanner"
```

Restart udev:


```
sudo /etc/init.d/udev restart
```

Create a symlink that is required to for Xsane to be able to see the scanner (You'll need to do this every reboot ):

```

sudo mkdir /dev/usb 
sudo ln -sfn /dev/usblp0 /dev/usb/lp0
```

Scanning using "xsane" and OpenOffice.org (Insert -> Picture -> Scan -> Request) should now work.

**Now- how to configure so I don't have to redo the code every time I reboot?**

Well I did this after some research:

```
sudo gedit /etc/group
```

Which returned in gedit to which I added xsane:

```
root:x:0:root,radtek
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:radtek,root
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,radtek,root
fax:x:21:root
voice:x:22:
cdrom:x:24:haldaemon,radtek,root
floppy:x:25:haldaemon,radtek,root
tape:x:26:root
sudo:x:27:
audio:x:29:radtek
dip:x:30:radtek,root
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:radtek
sasl:x:45:
plugdev:x:46:haldaemon,radtek,root
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:radtek
haldaemon:x:110:
scanner:x:111:cupsys,hplip,radtek,root,[COLOR="DarkRed"]xsane[/COLOR] (I added xsane)
slocate:x:112:
gdm:x:113:
radtek:x:1000:root,radtek
admin:x:114:radtek,root
ntp:x:115:
saned:x:116:
mythtv:x:117:radtek
mysql:x:118:
```

[COLOR="Black"]Now even when I reboot I have xsane able to access the scanner![/COLOR]

---

### Post by nashjc on 2007-04-04
I've followed your suggestions and the /bin/sh -> /bin/bash did get the installer to fire. Thanks. 

Now I cannot seem to get the scanner detected properly. Printer prints test page fine, so I think that the print side is OK.

I found

sane-find-scanner

DID find the scanner, both on a Compaq Presario 1540 (Dapper 6.06) and on an Acer 5050 (Edgy 6.10). But 

scanimage -L 

says "no scanners identified". 

Anyone have suggestions?

I'll also post on another thread on this subject. Apologies for that, but this material seems scattered about.

JN

---

