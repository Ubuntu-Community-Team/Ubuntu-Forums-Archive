---
title: "[SOLVED] HP Printer: IPP request failed with status 1028"
date: 2008-08-10
forum: Hardware
---

### Post by dbbolton on 2008-08-10
I'm using an HP Deskjet D1420. I ran gnome-cups-manager to set it up. The printer was detected automatically, and I selected the deskjet.ppd driver (version 1.3)

When I try to print a test page, nothing happens and I get this output:

```

** (gnome-cups-manager:14179): WARNING **: connect = 'usb://HP/Deskjet%20D1400%20series?serial=TH75L231T304Y5'

** (gnome-cups-manager:14179): WARNING **: IPP request failed with status 1028

```

Any idea what's wrong?

---

### Post by johnlvs2run on 2008-08-10
I don't know the answer, but 2 months after getting a biostar tf8200 motherboard, my HP laserjet 4M plus still won't run, and there are still some issues with the nvidia online video.  

After a number of posts and emails, my feeling is the biostar tf8200 motherboard chip doesn't work well with ubuntu's linux kernel - which is alluded to in biostar's responses.

Biostar obviously doesn't care about this.  In order to get the printer working, and video to work as it should, I might have to look at other distributions.

---

### Post by dbbolton on 2008-08-11
> **johnlvs2run said:**
> I don't know the answer, but 2 months after getting a biostar tf8200 motherboard, my HP laserjet 4M plus still won't run, and there are still some issues with the nvidia online video.  

After a number of posts and emails, my feeling is the biostar tf8200 motherboard chip doesn't work well with ubuntu's linux kernel - which is alluded to in biostar's responses.

Biostar obviously doesn't care about this.  In order to get the printer working, and video to work as it should, I might have to look at other distributions.
I'm using an MSI motherboard. I've heard that they don't have the greatest Linux support, but this computer was free.

Also, I'm using Debian right now, but I figured I was much more likely to get a helpful response here than on the Debian forum. 

I know that this printer worked perfectly with Ubuntu 8.04 and an old ASUS motherboard.

---

### Post by dbbolton on 2008-08-11
When I visit [http://localhost:631/printers](http://localhost:631/printers) I see this message:

```

DeskJet-Series (Default Printer) "No pages found!"
Description: DeskJet-Series
Location:
Printer Driver: HP DeskJet Series, 1.3
Printer State: idle, accepting jobs, published.
Device URI: usb://HP/Deskjet%20D1400%20series?serial=TH75L231T304Y5 

```

---

### Post by dbbolton on 2008-08-12
I checked the OpenPrinting database ( [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1420](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1420) ) and deskjet.ppd is NOT the right driver for this printer. It comes with the foomatic packages, and this particular model is not yet supported. 

All I had to do was install the hpijs package and select the proper version of the hpijs driver ( drv:///hpijs.drv/hp-deskjet_d1400_series-hpijs.ppd ).

---

