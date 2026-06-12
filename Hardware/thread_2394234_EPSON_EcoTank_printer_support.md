---
title: "EPSON EcoTank printer support"
date: 2018-06-14
forum: Hardware
---

### Post by soundgeek on 2018-06-14
Do Epson EcoTank printers like the ET-4500 work with Ubuntu?

---

### Post by soundgeek on 2018-06-14
I followed Epson links which told me that the ET-4500 is only supported in MacOS & Windows, but the I found this which looks promising: [http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

---

### Post by kurt18947 on 2018-06-15
Indeed it does. I haven't run an Epson printer on Linux so no personal experience. I do wonder about the "big ink tank" printers though. I wonder if the printhead durability and resistance to clogging is going to be in line with the ink capacity. Having a huge relatively inexpensive supply of ink isn't going to help if the printhead is misbehaving, for example after not having printed for a moth or more. If the ink delivery system is reliable those printers seem like they'll be economical long term.

---

### Post by soundgeek on 2018-06-17
[**[COLOR=#000000]Thanks kurt18947. I wonder about how it will go with the print heads, but we'll see. The disk that comes with it does not have Linux drivers, so I will try the link to drivers that I found. I don't know how to install them, but I'll see if I can figure it out. Epson don't make it so easy for Ubuntu.[/COLOR]**]("https://ubuntuforums.org/member.php?u=1447222")

---

### Post by kurt18947 on 2018-06-20
> **soundgeek said:**
> [**[COLOR=#000000]Thanks kurt18947. I wonder about how it will go with the print heads, but we'll see. The disk that comes with it does not have Linux drivers, so I will try the link to drivers that I found. I don't know how to install them, but I'll see if I can figure it out. Epson don't make it so easy for Ubuntu.[/COLOR]**]("https://ubuntuforums.org/member.php?u=1447222")  It's probably just as well that disks don't come with Linux drivers, the linux drivers on disks are oftentimes hopelesssly out of date. Please keep us apprised of your progress and problems. I think there was recent period of time when Epson MFD installs were problematic after being good for a long period of time.

---

### Post by soundgeek on 2018-06-21
I followed the instructions that went with the downloads. I installed **lsb** via **sudo** in a terminal window - I don't know what this does or whether it helped. I have a 64 bit processor, so I installed **epson-inkjet-printer-escpr_1.6.21-1lsb3.2_amd64.deb** using Ubuntu Software Centre and then **epson-printer-utility_1.0.2-1lsb3.2_amd64.deb**.

I set up the printer with a fixed IP address & plugged it into the LAN. In **System Settings/Printers** I selected **Add** and had it search for **Network Printers**. It discovered the printer with two identifiers under Network Printers. I guessed **Epson ET-4500 I(IP network printer via DNS-SD)** and this seems to work fine. 

I've tried this on 14.04.1 and 16.04.1 and both PCs could use the printer on the network.

I haven't tried installing the scanner drivers yet.

---

### Post by soundgeek on 2018-06-21
> **kurt18947 said:**
> ... Epson MFD installs were problematic....

What is MFD? I'm guessing not minimum fatal dose? ;)

---

### Post by soundgeek on 2018-06-21
I've since found this [tutorial]("https://tutorialforlinux.com/2016/06/19/epson-et-4500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/") for ET-4500 installation which is similar, but a bit different to the process I have followed.

---

### Post by maglin2 on 2018-06-21
I have an Epson printer and I just install printer-driver-escpr from the ubuntu repository. It's probably well out of date, but it's always got my xp-425 working.

If I want the scanner to work too I always have to download the drivers from epson though.

---

### Post by kurt18947 on 2018-06-23
> **soundgeek said:**
> What is MFD? I'm guessing not minimum fatal dose? ;)

Multi Function Device, e.g. printer/copier/scanner/fax. Re scanner install, I don't know about Epson but Brother had an issue with scanner install in 18.04 after working flawlessly in at least 14.04 & 16.04. The problem was copying some files to the wrong location, similar to what Brother had with the printer installer previously. If you run into a "scanner not found" situation let me know and I'll post a link to the Brother fix. There's no guarantee the Brother fix will work with Epson but it'd be a place to start.

---

