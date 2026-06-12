---
title: "Canon Imageclass MF8350 Cdn and Canon Pro9000 Mark II Printer Drivers Needed"
date: 2014-11-03
forum: Hardware
---

### Post by Wibbie1 on 2014-11-03
I'm running Ubuntu 14.04 on a 32 bit OS type computer. I'm new to Ubuntu and cannot seem to get my laser printer to work at all. It's a Canon Imageclass MF8350 Cdn. I would like to know what drivers to use, where I can get them, and how to install properly. Any help or suggestions would be wonderful. Please feel free to ask, if more details are needed. I wasn't sure what to provide.

I also have a Canon Pro9000 Mark II inkjet printer that I managed to make print, but the print comes out cut off and very faded with odd lines through the images on the page. I don't think it's necessarily a printer issue, as I just used it a few days ago before my iMac died, but who knows. 

Thanks in advance.

---

### Post by LinuXXuniL on 2014-11-03
Hi.

You can find some info here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters) ;

This is the official product support: [http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/color_imageclass_mf8350cdn#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/color_imageclass_mf8350cdn#DriversAndSoftware) ;

Hope you will find a way.

---

### Post by pdc on 2014-11-07
Hi Wibbie 1

just seen your post

I hope you are still out there; if you subscribe to a thread you start, you can get email updates when a reply has been posted

I think you need the Canon UFR driver; 

I have replied to someone else [http://ubuntuforums.org/showthread.php?t=2251562&p=13162403#post13162403](http://ubuntuforums.org/showthread.php?t=2251562&p=13162403#post13162403) who I think also needs the UFR

if I wait to see that you have seen this, I will then give you detailed instructions;

> /usr/sbin/lpinfo -v  ..........as in the other thread, if you could copy this; paste it into a terminal; copy the results and paste it back here, it will help

_______________

Canon lists your device as bidirectional, so to register the ppd they say the structure of the command is ```
/usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v cnusb:[device file location] -E
```

---

