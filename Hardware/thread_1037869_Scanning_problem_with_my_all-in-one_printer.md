---
title: "Scanning problem with my all-in-one printer"
date: 2009-01-12
forum: Hardware
---

### Post by hanbin973 on 2009-01-12
I have a problem with scanning with my all-in-one-printer.

I have no problems with printing. ( I'm using the driver of HP PSC-1350 )

My printer's model is Samsung SCX-1420, also I found out that it is a OEM of HP PSC-1350.

When I run xsane, it saids it can not find the device. How ever, when I run sane-find-scanner in the console, it saids there is a scanner. But dosn't knows the sane supports it or not.



I really needs help. hpjlp and hplip dosn't helps. also samsung driver has no driver of my SCX-1420....

---

### Post by yahs on 2009-01-12
As most samsung all in one printers are similar, I suggest you try these links ([http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)) and ([http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)) from the thread HOWTO Install Samsung Unified Printer Driver by Tweedledee. I have a Samsung scx-4100 and I was able to get everything up and running with these posts.

---

### Post by hanbin973 on 2009-01-14
All of those are the solution I trid. It didn't worked.. oh....

In the next time.. I need to buy a printer from hp...

---

### Post by Peter09 on 2009-01-14
I have the same problem as you exactly - except its on an HP printer

---

### Post by yahs on 2009-01-14
With regard to Samsung SCX-1420. Have you tried using the Samsung unified printer driver? Print set up is fairly easy, but scanning is quite difficult. (I am using Ubuntu Hardy)

I found that I had to add myself to the group lp, the group lpadmin and the group scanner. (I had to create the group lp)

I had to edit the file /etc/init.d/mountdevsubfs.sh.
and remove the comment symbol # from the 4 lines after
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs   -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb.

It also helped by rebooting after these changes.

---

