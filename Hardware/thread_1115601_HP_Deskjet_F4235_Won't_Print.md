---
title: "HP Deskjet F4235 Won't Print"
date: 2009-04-04
forum: Hardware
---

### Post by chessnerd on 2009-04-04
Alright, I've tried to print using an HP Deskjet F4235 over a dozen times and here's what happens:

1. I click print
2. It says that it is printing
3. It says that it is done printing
4. Nothing is printed

I've tried reinstalling the driver for the printer several times. I've restarted CUPS several times. I've switched to several other drivers to see if they would work. I reconfigured just about every option under Applications>Settings>Printing. I tried using the install CD (it wasn't compatible with Linux, but I'd tried everything else). Nothing seems to work. It could be that this printer just isn't Linux compatible.

This is not a life or death situation. I have two other computers (a laptop and another desktop) with Windows that I can print from, but I'd like to be able to get this printer to work with Xubuntu.

Any ideas?

---

### Post by 73ckn797 on 2009-04-04
In System/Administration/Printing make sure that you have selected the printer, not fax function (is listed), as the default for printing.

---

### Post by chessnerd on 2009-04-04
The printer is set as the default. I've tried changing just about everything in the printer configuration. I think it might be that it just isn't compatible with Linux.

---

### Post by Mark76 on 2009-04-04
Have you tried downloading a driver from HP themselves?

HP are very good when it comes to Linux support.

---

### Post by chessnerd on 2009-04-04
Well, I tried the install info they gave at this site: [https://answers.launchpad.net/hplip/+question/52234](https://answers.launchpad.net/hplip/+question/52234) and it didn't seem to work. The setup program they gave couldn't detect my printer. Any reason why that might be?

---

### Post by 73ckn797 on 2009-04-04
You could download the HP Linux printer driver here:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) 

Also make sure you have not set the printer to print to file.

I am running Jaunty and the HP driver download is the same version available via Synaptic. 

From their site it states: 
*The current version of the HPLIP solution is version 3.9.2.* ([Release Notes]("http://hplipopensource.com/hplip-web/release_notes.html"))

---

### Post by chessnerd on 2009-04-04
Thank you 73ckn797 and Mark76 for your help. I was able to successfully print a test page just now. :)

---

### Post by 73ckn797 on 2009-04-04
> **chessnerd said:**
> Thank you 73ckn797 and Mark76 for your help. I was able to successfully print a test page just now. :)

What was your solution? It may be a help to someone else browsing the forums for answers. You will have made a contribution to another new users experience.

Glad to have helped and enjoy your Ubuntu experience.

---

### Post by chessnerd on 2009-04-04
Well, maybe it didn't work so well. It seems to have actually made things worse. I installed the program from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and then ran it as an executable (it didn't work as a .run). After it installed and then ran a program to detect my printer I was able to print, all seemed good and right with the world and I printed a couple of documents. My computer started to run slow after that (probably because I had too many windows open) and so I rebooted.

I've rebooted my computer and now am both unable to print and my Applications>Settings>Printing and all other printing applications are gone! I don't understand what happend. To top it all off, the Device Manager for HP that the program installed doesn't work either.

I feel like I've been brought back to square -1. Is there a system restore or something that I could run or is there some command that I could put in that will bring back my applications? At this point, I'd be happy to just be back and square 0.

---

### Post by 73ckn797 on 2009-04-04
Try removing all listed installations of hplip from synaptic and re-installing.

---

### Post by chessnerd on 2009-04-04
That might not be necessary, I seem to have found the solution. I went into Add/Remove Programs to remove the HP program and typed in "printing" and found that the printing program was somehow removed. I reinstalled it and no errors or anything came up. I just printed a page from OpenOffice and there were no problems. I don't know why the HP program would uninstall that, but I'm now able to print again. 
:mad: Sometimes I think that these computers have a mind of their own.

I think I'm going to reboot and see if I can still print after that. If I can't, I'll uninstall the HP programs, otherwise, I'm good to go.

---

### Post by chessnerd on 2009-04-04
Still able to print after reboot. I don't know what the problem was, but it seems fixed now. I guess you just have to reinstall the printing applications after you install the HP thing. This might be a Xubuntu problem rather than an Ubuntu problem because the print manager is different for Xubuntu.

Thanks again for the help. Let's just hope I don't get any more problems. :)

---

### Post by h4141 on 2011-01-19
this HP Deskjet F4235 All-in-One Printer [Drivers]("http://driverswin.com/hp-deskjet-f4235-printer-drivers-for-win/") Download pages. win and linux driver 
good luck

---

### Post by h4141 on 2011-01-19
this HP Deskjet F4235 All-in-One Printer [Drivers]("http://driverswin.com/hp-deskjet-f4235-printer-drivers-for-win/") Download pages. win and linux driver 
good luck

---

### Post by h4141 on 2011-01-19
this HP Deskjet F4235 All-in-One Printer [Drivers]("http://driverswin.com/hp-deskjet-f4235-printer-drivers-for-win/") Download pages. win and linux driver 
good luck

---

### Post by h4141 on 2011-01-19
Bu HP Deskjet F4235 Hepsi-Bir-Arada Yaz&#305;c&#305; [Sürücüler]("http://driverswin.com/hp-deskjet-f4235-printer-drivers-for-win/") Download sayfalar&#305;. kazanmak ve sürücü linux 
iyi &#351;anslar

---

### Post by h4141 on 2011-01-19
Bu HP Deskjet F4235 Hepsi-Bir-Arada Yaz&#305;c&#305; [Sürücüler]("http://driverswin.com/hp-deskjet-f4235-printer-drivers-for-win/") Download sayfalar&#305;. kazanmak ve sürücü linux 
iyi &#351;anslar

---

