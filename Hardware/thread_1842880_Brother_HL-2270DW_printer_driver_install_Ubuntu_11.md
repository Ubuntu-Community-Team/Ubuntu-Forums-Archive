---
title: "Brother HL-2270DW printer driver install: Ubuntu 11.04 64-bit"
date: 2011-09-12
forum: Hardware
---

### Post by txducker on 2011-09-12
Second Addendum: Posts below this one state that the Brother 2170W driver works for the 2270DW printer, however I am not recommending the 2170W driver. I have not used the 2170W driver and do not know if any functionality is lost by using this driver, however several people in the following posts report it working, but other posts say the quality is not as good as the HL-2270W drivers. No one has reported any problems with the HL-2270DW driver which is not the case for the 2170W driver. If you want to use 2270DW driver, then follow the instructions below.

This is a post on how I setup my Brother HL-2270DW printer driver for Ubuntu 11.04 64-bit (update 02/23/2012 this driver works perfectly in Ubuntu 11.10 64 bit). This printer has wifi capabilities and took me hours to get this printer set up properly. I really do appreciate Brother's linux support, however they do not have 64-bit drivers on their website. Trying to install the standard 32-bit drivers resulted in installation errors and the driver .ppd file would not get installed. You have to download a bash script from their website to patch their two driver files before the drivers will install on 64-bit systems. Below I will give links to instructions on the install and links to the patched driver files. Patching driver files might be a challenge to those not comfortable with the command line.

[My more detailed instructions.]("http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html")

[Brother printer instructions.]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html")

Driver download -> [CUPS wrapper Brother HL-2270DW driver/patched Ubuntu 11.04 64-bit version 2.0.4-2]("https://docs.google.com/leaf?id=0BxKNugMxlGF7NzQwYTcyNmYtZWMxNC00MzJlLWEwZGEtM2QyNzgwN2ZhYWZh&hl=en_US")

Driver download -> [Brother HL-2270DW printer driver/patched Ubuntu 11.04 64-bit version 2.1.0-1]("https://docs.google.com/leaf?id=0BxKNugMxlGF7MjQ3ODI4MzEtMGMyYy00ZGVlLThiMjAtZjdiMjZjZjkxOWE3&hl=en_US")

[Ubuntu Thread that helped my install.]("http://ubuntuforums.org/showthread.php?t=1745084")

Good Luck!

---

### Post by kroq-gar78 on 2011-09-14
sweet! this worked perfectly. I just got this printer yesterday or so, and what great timing! Just a day earlier, you posted the instructions!

Thanks!

---

### Post by ozviking on 2012-01-19
> **txducker said:**
> This is a post on how I setup my Brother HL-2270DW printer driver for Ubuntu 11.04 64-bit. This printer has wifi capabilities and took me hours to get this printer set up properly. I really do appreciate Brother's linux support, however they do not have 64-bit drivers on their website. Trying to install the standard 32-bit drivers resulted in installation errors and the driver .ppd file would not get installed. You have to download a bash script from their website to patch their two driver files before the drivers will install on 64-bit systems. Below I will give links to instructions on the install and links to the patched driver files. Patching driver files might be a challenge to those not comfortable with the command line.

[My more detailed instructions.]("http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html")

[Brother printer instructions.]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html")

Driver download -> [CUPS wrapper Brother HL-2270DW driver/patched Ubuntu 11.04 64-bit version 2.0.4-2]("https://docs.google.com/leaf?id=0BxKNugMxlGF7NzQwYTcyNmYtZWMxNC00MzJlLWEwZGEtM2QyNzgwN2ZhYWZh&hl=en_US")

Driver download -> [Brother HL-2270DW printer driver/patched Ubuntu 11.04 64-bit version 2.1.0-1]("https://docs.google.com/leaf?id=0BxKNugMxlGF7MjQ3ODI4MzEtMGMyYy00ZGVlLThiMjAtZjdiMjZjZjkxOWE3&hl=en_US")

[Ubuntu Thread that helped my install.]("http://ubuntuforums.org/showthread.php?t=1745084")

Good Luck!

Hi,
Just use the HL-2170W driver that comes in Ubuntu when adding printer, works perfect.
had the printer up and running in minutes.
Cheers

---

### Post by nerdmanxdx on 2012-01-31
> **ozviking@optusnet.com.au said:**
> Hi,
Just use the HL-2170W driver that comes in Ubuntu when adding printer, works perfect.
had the printer up and running in minutes.
Cheers

Thanks for the tip. Confirming that this works for me on 11.10 with duplexing.

---

### Post by txducker on 2012-02-01
Are you using the 64 bit version of Ubuntu?

---

### Post by xyzzyman on 2012-02-03
2170W 64bit drivers have always worked for me for this printer.

---

### Post by beenny on 2012-02-17
For some reason the 2170DW drivers did not work for me...but this youtube video walks you through the installation well:

[http://www.youtube.com/watch?v=pqpWhnjemLc](http://www.youtube.com/watch?v=pqpWhnjemLc)

Duplexing and all work on 64bit 11.10

---

### Post by pinegreen on 2012-02-23
I've tried both drivers and while the HL-2170W drivers work, the quality is considerably better with the HL-2270DW drivers!!

---

### Post by txducker on 2012-02-24
> **pinegreen said:**
> I've tried both drivers and while the HL-2170W drivers work, the quality is considerably better with the HL-2270DW drivers!!

Thanks pinegreen for letting us know that.  I have not taken the time to test both drivers and test all the features of the printer with both drivers. I can report that I have not had any problems with the printer using the HL-2270W drivers.

Pinegreen, can you explain in more detail what was better for you with the HL-2270W driver? When you said quality is better, are you referring to print quality or stability of the driver software?

---

