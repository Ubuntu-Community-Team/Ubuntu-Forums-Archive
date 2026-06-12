---
title: "Network scanning on HP C6210 all-in-one"
date: 2008-05-04
forum: Hardware
---

### Post by gtmaneki on 2008-05-04
Hi, all.  I have a HP C6210 all-in-one printer/scanner attached to the network at IP address X.Y.2.6.  My Kubuntu 8.04 system at IP X.Y.2.4 can print (thanks to HPLIP 2.8.4) and I can scan using the web interface, but I can't seem to get programs like Kooka and XSane working -- they give me errors saying they can't find the divice, or the device is busy.  Can anyone help me resolve this?

From what I've read, I need to use sane.d  to get things running.

Here's how things are configured:

/etc/services has the line
```
sane-port       6566/tcp        sane saned      # SANE network scanner daemon
```

/etc/inetd.conf has the line
```
sane-port stream tcp nowait saned.saned /usr/sbin/saned saned

```
and I have installed the inetutils-inetd package

/etc/sane.d/saned.conf has the line
```
X.Y.2.4 #IP of my computer
```

/etc/sane.d/dll.conf has the net backend uncommented and the hpaio backend added

/etc/sane.d/net.conf has the line
```
X.Y.2.6 #IP address of printer
```

Running "scanimage -L" gives me the result
```
device `hpaio:/net/Photosmart_C6200_series?ip=X.Y.2.6' is a Hewlett-Packard Photosmart_C6200_series all-in-one
```

Running "scanimage >image.pnm" gives me the result
```
open of device hpaio:/net/Photosmart_C6200_series?ip=X.Y.2.6 failed: Device busy
```

Just a few additional details 
[list]
[*]I have had this problem on both Kubuntu 7.10 and 8.04.  
[*]Also, while I typically have guarddog running on my computer, I get this error whether or not I have guarddog enabled or disabled.
[*] When I was installing HPLIP (downloaded from the sourceforge page), it gave me an error that it couldn't download the libsane-dev package, although I already had it installed on my computer.
[/list]

I hope you all can offer some suggestions.  I'm stuck.

---

