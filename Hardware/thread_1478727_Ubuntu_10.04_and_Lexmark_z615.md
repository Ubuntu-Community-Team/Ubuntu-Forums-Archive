---
title: "Ubuntu 10.04 and Lexmark z615"
date: 2010-05-10
forum: Hardware
---

### Post by dedal_gr on 2010-05-10
Hi. I have a problem with printer Lexmark z615. I install the driver for z600 series but it not work. With 8.04 all is fine.
I use this dr[http://www.nodevice.com/driver/Z615/get32517.html]("http://www.nodevice.com/driver/Z615/get32517.html")iver.

---

### Post by neandert on 2010-05-10
> **dedal_gr said:**
> Hi. I have a problem with printer Lexmark z615. I install the driver for z600 series but it not work. With 8.04 all is fine.
I use this dr[http://www.nodevice.com/driver/Z615/get32517.html]("http://www.nodevice.com/driver/Z615/get32517.html")iver.

I have exact the same problem, It will be a new printer or back to windows?

---

### Post by anglican on 2010-05-11
> **dedal_gr said:**
> Hi. I have a problem with printer Lexmark z615. I install the driver for z600 series but it not work. With 8.04 all is fine.
I use this dr[http://www.nodevice.com/driver/Z615/get32517.html](http://www.nodevice.com/driver/Z615/get32517.html)iver.
Just a guess, that driver is quite old and requires libstdc++.so.5 which was last seen in the jaunty [repos]("http://packages.ubuntu.com/en/jaunty/libstdc++5"). The jaunty version certainly installed fine in karmic and probably does in lucid... so try installing:

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5) 

If that doesn't work, perhaps you could post the errors from the log file (/var/log/cups/error.log) when you try to print.

H

---

### Post by anglican on 2010-05-17
> **anglican said:**
> Just a guess, that driver is quite old and requires libstdc++.so.5 which was last seen in the jaunty [repos]("http://packages.ubuntu.com/en/jaunty/libstdc++5"). The jaunty version certainly installed fine in karmic and probably does in lucid... so try installing:

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5) 

If that doesn't work, perhaps you could post the errors from the log file (/var/log/cups/error.log) when you try to print.

OK, I finally got around to seeing what happens myself with my Lexmark x1150 (which also uses the z600 driver). In Lucid (and also later Karmic kernels) there is a problem caused by usbfs no-longer being included in the kernel; usbfs was already deprecated and found to cause some problems with udev. Old drivers like z600, however, require it and will silently fail! There is a way to get the printer working, not IMO a terribly good way, but it works. You will need to give the following commands:
```
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
```You can test that the printer driver is correctly installed with the command:
```
/usr/lib/cups/backend/z600
```Which should give output something like:
> direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"Once you've finished printing you might want to undo the above as it may well break other things, so type:
```
sudo umount /proc/bus
```Hope this helps.

H

---

### Post by dedal_gr on 2010-05-19
Hi.
Thanks for your help.
All work.
I just installed libstdc++.so.5

---

### Post by imtiyaz on 2010-05-29
Content of this post became unnecessary due to installation of 'libstdc++5'
I can print now with Z615:D

---

### Post by imtiyaz on 2010-05-29
Anyone interested to download the driver may use any of the following pages -


[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

[http://support.lexmark.com/index?page=content&id=DR4360&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=&searchid=1275025417913](http://support.lexmark.com/index?page=content&id=DR4360&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=&searchid=1275025417913)

You should follow the first instruction at -

[http://ubuntuforums.org/archive/index.php/t-159704.html](http://ubuntuforums.org/archive/index.php/t-159704.html)

---

### Post by imtiyaz on 2010-05-29
Anyone interested to download & install 'libstdc++5' in Ubuntu 10.04 should go to the following page -

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

when you click on any link a dialogue box will appear. You should select "Open with GDebi Package Installer" & click OK. The file will be installed to your Ubuntu 10.04.

Without this file you can not use your Lexmark Z615 printer in Ubuntu 10.04.

The following page may be helpful for you -
[http://mindaict.blogspot.com/2010/01/solved-printing-with-lexmark-in-karmic.html](http://mindaict.blogspot.com/2010/01/solved-printing-with-lexmark-in-karmic.html)

Have printing with Z615 :)

---

### Post by Gsyman on 2010-09-06
Hi
My daughter has a HP Pavilion 2899ea laptop (64bit) and we cannot get her Lexmark Z615 to work on it.

We used this driver:

 [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&amp;do=get&amp;target=lexmark.z600-0.4.deb](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&amp;do=get&amp;target=lexmark.z600-0.4.deb)

Can anyone walk us through what to do? I have almost convinced her to ditch Vista and use Linux!

Thanks

---

### Post by anglican on 2010-09-08
> **Gsyman said:**
> Hi
My daughter has a HP Pavilion 2899ea laptop (64bit) and we cannot get her Lexmark Z615 to work on it.

We used this driver:

 [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&amp;do=get&amp;target=lexmark.z600-0.4.deb](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&amp;do=get&amp;target=lexmark.z600-0.4.deb)

Can anyone walk us through what to do? I have almost convinced her to ditch Vista and use Linux!

Thanks
It should be enough to simply follow the instructions in post #3 and #4 above. Wherever you see a "code:" box it means "Open a terminal and type (or cut and paste) this command in that terminal". If you have any problems with any step just post back here. Provided you get the specified output to the 
/usr/lib/cups/backend/z600 command you should be able to print OK.

H

---

### Post by Gsyman on 2010-09-24
Finally got the printer working by following the instructions in this posting:

[http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html)

Follow the commands in the fist post.

Seems you need both 32 and 64 bit versions of lidstdc running separately to make it function.

my daughter has now moved from Vista to Ubuntu. Another convert!

---

