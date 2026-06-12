---
title: "Brother HL3140CW printer"
date: 2016-03-07
forum: Hardware
---

### Post by Panawe on 2016-03-07
Just bought this colour laser printer off eBay without first checking for compatibility with Ubuntu. 

Is anyone aware of any problems with this printer in Ubuntu?

TIA

---

### Post by howefield on 2016-03-07
Shouldn't be a problem, there are Linux drivers for this printer on the Brother website if it isn't already recognised out of the box.

---

### Post by SeijiSensei on 2016-03-07
Great choice.  I have a 3170CW and used the printer driver utility at Brother's website the first time I installed it.  Now I just point a browser to [http://localhost:631/](http://localhost:631/) and use the CUPS management page.  If you connect the printer directly on the network with an Ethernet cable and give it a static IP address, CUPS will discover it automatically.  I'm using the 3070 driver because I didn't see one for the 3170, but it works just fine.  I don't see a driver for the 3140 in CUPS list on my Kubuntu 14.04 system, but I'd be surprised if the 3070 driver wouldn't do the job.  If you have problems, try the [driver installer utility]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl3140cw_us_eu&os=128&dlid=dlf006893_000&flang=4&type3=625") instead of CUPS.

It looks like that printer has a firmware upgrade which you should probably apply.

I can also print to it from my Android phone with Brother's [app]("https://play.google.com/store/apps/details?id=com.brother.mfc.brprint&hl=en").  I don't have wifi printing enabled; the phone gets an address from my wifi router and can see the printer that way.

---

### Post by Panawe on 2016-03-09
Thanks for advice. Couldn't make any headway using the Brother Linux tool but seem to have installed it using the CUPS method. Having said that I haven't been able to print yet, seems to send data to printer but printer stays asleep.

---

### Post by Panawe on 2016-03-10
Have got this working now but I thought my experience might be useful to others.

Used the CUPS menu which appeared to install the printer but I couldn't get it to work. It appeared in the Printers screen as installed and default but I, with my minimal Ubuntu skills, couldn't get it to communicate properly with my computer.

Went to the Brother site and negotiated my way through the menus and downloaded their driver installer. Herein lies the problem I found - I unzipped the file and went through the instructions until I met:

>   Step5. Run the tool:
   **Command: bash linux-brprinter-installer-*.*.*-* Brother machine name **
   Step6. The driver installation will start. Follow the installation screen directions.

The expression "Brother machine name" - whatever I put in wasn't recognised. The reason, I discovered after finding a video on Youtube, was that I was writing, in Terminal, things like "Brother HL-3140CW" and variations on that theme instead of simply keying in the model "hl3140cw" which worked like a dream.

Hope this is of some use to others.

---

