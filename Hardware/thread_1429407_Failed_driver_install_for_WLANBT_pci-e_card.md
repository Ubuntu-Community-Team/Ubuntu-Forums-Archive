---
title: "Failed driver install for WLAN/BT pci-e card"
date: 2010-03-14
forum: Hardware
---

### Post by simbeb on 2010-03-14
I haven't been able to use my Ubuntu NBR 9.10 install for several months because I upgraded my wifi pci-e card to a wifi/bluetooth card and there was no driver for it. Now I found the driver there:

[http://3dsp.com.cn/web_html/download.html](http://3dsp.com.cn/web_html/download.html)

It is the one under #4 for Ubuntu 9.10 32-bit.

When I try to run the driver, I get the following:

```
fred@Netbook:~$ cd Desktop
fred@Netbook:~/Desktop$ sudo bash Install_3DSP.sh
[sudo] 
password for fred: 
 *
 * Checking user...[ Ok ]
 
* Verifying kernel...[ Ok ]
 * 
Checking files...[ Ok ]
 
* Installing modules...[ Ok ]
 
* Creating boot script...[ Ok ]
 
* Installing utilities...[ Ok ]
 
* Installing 3dsp-wifi-radar...[ Ok ]
 
* Loading modules...insmod: error inserting '/usr/local/3DSP/pci/3dspbt.ko': -1 Operation not permitted

insmod: error inserting '/usr/local/3DSP/pci/3dspwlan.ko': -1 Operation not permitted

mknod: missing operand after `0'
Try `mknod --help' for more information.
Installation completed. Exit.

Please restart your computer to use 3DSP card.
Startup 3DSP card throuth Applications->Accessories->3DSP WB.

Thanks for using 3DSP card. Have a good day!
fred@Netbook:~/Desktop$ 
```
Then the bluetooth utility cannot start and the wifi utility does not find the wifi card ('no valid device found')

I am a bit desperate . Does anyone see what I am doing wrong? (I am quite a newbie to Linux)

Cheers

---

### Post by simbeb on 2010-03-20
I really expected someone in the community to see what is wrong with this driver install. Never mind, will try elsewhere :(

---

### Post by daddyd on 2010-03-21
try to run sudo su first then run the script. I dinked with the same prob for a while.

---

### Post by simbeb on 2010-03-24
> **daddyd said:**
> try to run sudo su first then run the script. I dinked with the same prob for a while.
 
 
Thanks, will try that. but I'm not holding my breath :)

---

### Post by alxgomz on 2010-05-26
Hello I had the very same problem and finally realised i was trying to install the PCI vbersion of the driver when I had the USB one.

here is the link i used:
[ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Ubuntu/BlueW-2310U_2.3.3_100303_Ubuntu9.10_withhotkey.tar.gz](ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Ubuntu/BlueW-2310U_2.3.3_100303_Ubuntu9.10_withhotkey.tar.gz)

Good luck

---

### Post by alxgomz on 2010-05-29
3DSP also released the source code of both kernel modulesftp://3dsp_lpkt_pci:fw1qa8@3dsp.com.cn (for USB only... PCI doesn't have source available... unless i mistaken) and applications, so now we're not stuck with the kernel 2.6.31-14 anymore.
Compilation works flawlessly when requirements mets (see INSTALL)!

source code at [ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Open%20Source%20Code/]("ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Open%20Source%20Code/")

---

