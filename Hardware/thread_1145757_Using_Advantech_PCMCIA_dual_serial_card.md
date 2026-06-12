---
title: "Using Advantech PCMCIA dual serial card"
date: 2009-05-01
forum: Hardware
---

### Post by kenbotransy on 2009-05-01
I've been using a 2.4 kernel distribution on a Thinkpad A31 for a few years to run a B12 robotic platform.   The software talks to the robot over a PCMCIA card made by Advantech (the COMpad 32 2 port).   Using the pcmcia_cs package, I was able to set up the correct entries in the /etc/pcmcia/config file.   It looked like: 

card "Advantech COMpad-32/85B-2"
  version "ADVANTECH", "COMpad-32/85B-2"
  cis "cis/COMpad2.dat"
  bind "serial_cs"


Then, I installed Ubuntu 8.04 on the laptop which moved to a 2.6 kernel.   It also went from the pcmcia_cs system to the more integrated pcmcia_core.  However, the default setup simply sees the COMpad as a parallel port :-(   After some research, I added the card entry to the /etc/pcmcia/config.opts file.   I also grabbed the pcmcia_cs package and moved the cis/COMpad2.dat file to /lib/firmware/COMpad2.cis

But, no luck with the card---ubuntu still sees it as a parallel card (the default).   I cannot get it to recognize it as the correct serial.    

I did a search with lsmod and saw no serial_cs module.   I did an insmod on the serial_cs in the /lib/modules/... directory.   No luck.  

I am not sure if the card entry line should still contain the cis line.  If so, 
should it read 
   cis "COMpad2.cis"   
or still contain the cis/ ? 

If anyone has any experience with the dual port serial PCMCIA card or a related entity, 
I'd appreciate any advice.    Or, what else can I look at for debugging help? 

thanks, 
kenny

---

### Post by kenbotransy on 2009-05-05
Still no luck with the card.   Regardless of what I try, the card
refuses to bind to serial_cs.   Is there any way to manually force this 
after the PCMCIA system has loaded it as a parallel card? 

kenny

---

