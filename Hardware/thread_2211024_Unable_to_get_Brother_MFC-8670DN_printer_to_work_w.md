---
title: "Unable to get Brother MFC-8670DN printer to work with Ubuntu 13.04"
date: 2014-03-13
forum: Hardware
---

### Post by markwco on 2014-03-13
I currently am running Ubuntu 13.04.  I plan to update to the new LTS release once that is released.  I'm not sure if that would make a difference with the below issue that I have:

I have a Brother MFC-8670DN printer.  It is connected to a Mac desktop via USB but I'm also using the ethernet port to connect it to the Wired/WiFi router.  For that reason I'm able to print to it from the network.  I've used it with a Chromebook via Google Cloud Print, with a Mac laptop, and even an iPad and iPhone via various printing apps.  For some reason I can't get it to work with Ubuntu.

When I did the add printer I selected the printer directly on the network and added it.  It asked for various options and I selected 1 input tray since that's all I have and also no Ramdisk since I don't have any additional options in the printer.  It gave me the option of two drivers, the BR-Script3 and a Postscript. It recommended BR-Script3 and I don't believe this is a Postscript either so I selected BR-Script3.  It gave the option to print a test page. I did that and it quickly printed.

Since then I've tried printing other items such as a website from Chromium.  When I select to print after that the yellow status light on the printer will begin flashing and will continue flashing.  For example I had a 7 page website and after 2 mins or so the first page printed and then in a few more mins the 2nd page, etc.  It ends up just printing a page every few mins so that a 7 page document takes about a half hour to print.  If I view the print queue it will say "Waiting for printer to finish".  I'm just not sure what's hanging it up.  The printouts come out fine.  The issue is the extremely slow print speed.

Even though this isn't a Postscript printer I tried that option and it didn't work.  I also tried networking via the Mac desktop and then to the printer since it listed that as another option to connect.  I ran into the same type of problems with it taking a few minutes to print each page.

I'm obviously selecting the Brother MFC-8670DN driver so I would assume that would work.  Is there another driver or option I should select?  

Thank you in advance for your help.

Mark

---

### Post by kurt18947 on 2014-03-14
I have two Brother MFDs, 7820 & 6490CW.  When I selected Brscript on the 7820N, the first page would print pretty quickly but subsequent pages would be at a rate of a couple pages a minute.  I was able to find in the repository a CUPS driver and installed that.  I was able to select that CUPS driver and speed increased to what I expected, around 20 pages/minute.  The MFC-6490 uses a CUPS driver from the get-go.  I use Brother's installer script, I'm not sure if that matters or not.

---

### Post by gifford on 2014-03-14
I would suggest installing the printer as a networked one as per the instructions on the Brother site. It seems that the problem is fairly well documented regarding the BR-Script3. See this link:[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother/MFC-7820N](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother/MFC-7820N)

Go to this site and follow the instructions for installing your printer: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by pdc on 2014-03-14
and if you go here

[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

you get to download a Brother installer; that should install both the correct printer driver; and scanner driver; 

thanks to supermandodi for this link

---

### Post by markwco on 2014-03-14
Thank you. I installed the CUPS driver and it's working fine now.

---

