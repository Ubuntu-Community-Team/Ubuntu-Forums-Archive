---
title: "Canon PIXMA MX870"
date: 2012-05-09
forum: Hardware
---

### Post by Welly Wu on 2012-05-09
I have a Canon PIXMA MX870 that I have connected to my Verizon FiOS fiber optic Internet network using a Category 5e cable and 802.11 G WPA2 AES-TKIP PSK. I went into system settings to add my IP address for my Canon PIXMA MX870 printer and I verified it by checking the wired and wireless network settings on my MI424WR router and the Canon multi-function machine itself, but Ubuntu is telling me that there is no printer available at this specific IP address. I am using NAT. I tried this same action earlier this morning and it did find my printer, but I could not print any documents or a test print page. I know that Ubuntu supports my Canon PIXMA MX870 multi-function machine because it is listed under Canon printers.

What is causing this problem?

How do I solve this problem so that I can print documents?

---

### Post by Welly Wu on 2012-05-09
[http://ubuntuforums.org/showthread.php?t=1475336](http://ubuntuforums.org/showthread.php?t=1475336)

I read this thread carefully and I downloaded and installed the Canon printer and scanner drivers from Europe. Then, I went into System Settings -> Printers and I put in the same IP address. It works now. I can print documents and scan documents. This is solved.

---

### Post by ahallubuntu on 2012-05-09
[Posted this right after you found the European drivers on your own - good job!  Still good to connect either wired or wireless but not both.]

First of all, there is no need to connect the printer twice.  Either connect it via the Cat 5e network cable or connect it wirelessly, not both.  Connecting it twice will give it two separate IP addresses on your network and could cause confusion later.

I'm using two Canon printers wirelessly in Ubuntu 10.04 LTS: a Canon MX420 and a Canon MX340.  Both show a device URI like this

cnijnet:/00-1E-8F-F3-3B-61

Where 00-1E-8F-F3-3B-61 is my printer's MAC (hardware) address on the network.  What does yours show for device URI in the printer properties after installed?

The MAC is different for wired and wireless connections, too - that's why if you connect one way or the  other but not both you'll have less confusion over this.

I'm not sure if it makes any difference, but Ubuntu 10.04 did not natively support my printer.  I had to install a driver I found on Canon's European website and that has worked well.

---

