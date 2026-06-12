---
title: "Brother DCP 130C Printer Will Not Print."
date: 2008-10-18
forum: Hardware
---

### Post by rags01 on 2008-10-18
Hey, I'm new to the forums and Ubuntu and I thought i'd ask the experts.

My Brother DCP 130C Printer+Scanner (All In One) will not print. I have installed the Drivers for the Printer in Linux but when I try to print it says on my printers display "receiving data" but it then returns to the regular screen. Also in the printer configuration area it says my "Make & Model" is something completely different to what it is! I looked through the make and model list but my printer is not listed.

I am using the latest Ubuntu (8.04)

Help? :(

---

### Post by TopEnder on 2008-10-19
Rags01,
If you search for your printer by name (DCP_130C) in Synaptic Package Manager and install the drivers** but before doing this un-install what you have previously installed to do with your printer/scanner**. I uninstalled all drivers (printers & scanner, dis-connect both power & USB cable, installed drivers, powered down re-connected cables powered up and the printer worked. The Scanner functions was a bit of a problem but by used the post Poll: HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!  (Multi-page thread 1 2 3 ... Last Page) BoardDWorld  (a lot of posts but worth the read) and using the Brother site I have the Scanner working by it's Control Panel or program like "Xsane Image Scanner".  If you search the Forumn for either Brother Printer of Brother Scanner you will find a lot of post that could be of help with your printer problem.
Hope you get it working any problems then you can Private Message me or another entry to your post. I have a few rough notes/points on the installation of the scanner that may help you and if so I'l post them on the forum. TopEnder

---

### Post by rags01 on 2008-10-19
How do I uninstall Drivers?

---

### Post by rags01 on 2008-10-19
Oh Okay I used thee package manager to uninstall the drivers now do I use it again to install them?

---

### Post by rags01 on 2008-10-19
Okay So How to I get back the drivers in the Synaptic Package Manager (Re-Install THem)

---

### Post by ardvark71 on 2008-10-20
> **rags01 said:**
> Hey, I'm new to the forums and Ubuntu and I thought i'd ask the experts.

My Brother DCP 130C Printer+Scanner (All In One) will not print. I have installed the Drivers for the Printer in Linux but when I try to print it says on my printers display "receiving data" but it then returns to the regular screen. Also in the printer configuration area it says my "Make & Model" is something completely different to what it is! I looked through the make and model list but my printer is not listed.

I am using the latest Ubuntu (8.04)

Help? :(

Hi...

The printer's listing in the OpenPrinting database may have something to do with this...

[http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-130C](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-130C)

However, the brother driver listed on that page may work with your printer...

[http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C](http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C)

I would try the CUPS driver first. Also, if you choose the rpm package, you will also need to download and install the "Alien" package from Synaptic. You may very well need to use the terminal (and know some linux command line language) to install this driver. :( If you need help in doing this, please post back and someone should be able to help you.

If this turns out to be impossible or to much of a headache to deal with you can go back to the OpenPrinting database to see what printers are completely compatible with Linux or you can post a question on this forum asking what others use for printers and how well they work with Ubuntu. :)

[http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro](http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro)

Hope this helps... :)

Best Regards...

---

