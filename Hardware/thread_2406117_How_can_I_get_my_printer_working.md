---
title: "How can I get my printer working?"
date: 2018-11-15
forum: Hardware
---

### Post by sofasurfer on 2018-11-15
I have Ubuntu 16.04, and a HP printer Model #3850, but it is not showing up on the ADD Printer spot, when I get into that part.  We've had problems with it previously, because of software glitches - through trial and error, I found how to fix it a couple of times.  I assume that the software is all screwed up in it.  I need to know how to delete and install the printer software, so that the printer will be recognized by the computer.

---

### Post by Autodave on 2018-11-15
How is this connected: wifi, internet, USB, LAN, etc?

---

### Post by sword3 on 2018-11-15
Autodave is correct, we need to know how it is connected. In the past, I have been able to choose a printer model close to the one I might have and get it to work, or even by choosing Generic Printer if you have that option.

---

### Post by oldfred on 2018-11-15
The new 18.04 supports driverless printing.

But with older installs best to use the HPlip software directly from HP, the version in Ubuntu's repository is often older.
And then configuring wireless printing is a lot easier as you can use computer rather than the couple of buttons & tiny screen on HP printers.

[https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)

---

### Post by sofasurfer on 2018-11-16
Printer is connected with USB. It has wifi capability but we do not use wifi.
Printer installation has always been the most difficult thing for my. I am not familiar with HPlip. I am aware of CUPS but never learned to manually set it up. 
I assume I need to remove everything on my system that has to do with printers (since I have really spent a lot of time installing and removing stuff with no results)  and then reinstall the printer driver which I assume is HPlip. Am I correct on that? 
So I am asking for guidance and direction. Ready, set, go!

---

### Post by SeijiSensei on 2018-11-16
Install hplip with "sudo apt install hplip".  It may be there already.

Open a browser and point it to [http://localhost:631/](http://localhost:631/).  Choose Administration, then Add Printers.  Enter your username and password when prompted.  Select the HPLIP option and follow the remaining steps.

---

### Post by sofasurfer on 2018-11-16
I installed HPlip. 
I went to local:631.
Under PRINTER I chose "local printer:  HP Printer (HPLIP) ".
When I hit continue I go to ADD PRINTER and I am asked to enter something into the CONNECTION box. "hp" is already in the box but I don't know what its asking for. 

This is all fine if you can help me get this going but I want to say that previously my printer would show up in the printer control panel and a click of the button would install it....as far as I remember.

Soooo, whats my next step?
Thank you.

---

### Post by SeijiSensei on 2018-11-17
Sorry, my experience with HPLIP is limited to network printers. 

Another option is to use the "hp-setup" command.  Try "hp-setup -i -a". See [http://manpages.ubuntu.com/manpages/bionic/man1/hp-setup.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/hp-setup.1.html).

> One USB printer attached, automatic:
$ hp-setup -i -a

---

### Post by sofasurfer on 2018-11-17
Thamks. I got it working

---

