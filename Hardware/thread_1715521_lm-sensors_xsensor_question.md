---
title: "lm-sensors xsensor question"
date: 2011-03-27
forum: Hardware
---

### Post by ghostofzuul on 2011-03-27
hi i installed lm-sensors and got it up and running and i'm getting an odd reading. 

for my +12v the reading is 0.00 volts and it says ALARM.

other than that everything seems to be within the thresholds. 

i've read that lm-sensors has to be configured exactly to your motherboard or else doesn't work right? is it possible this is just an error? if it was really 0.00 wouldnt my computer be off? 

thanks.

---

### Post by Hakunka-Matata on 2011-03-27
Yeah, don't worry, I rather doubt you'd be posting if the P/S 12VDC output was zilch.  Jump into BIOS Setup @ boot time and check your hardware data, it'll likely show the same.

---

### Post by ghostofzuul on 2011-03-27
> **Hakunka-Matata said:**
> Yeah, don't worry, I rather doubt you'd be posting if the P/S 12VDC output was zilch.  Jump into BIOS Setup @ boot time and check your hardware data, it'll likely show the same.

stupid intel D845EBG2 mobo doesn't have hardware diagnostics on the verison i'm using and since i have it running linux i can't flash update the bios to the most recent version that allegedly has hardware monitoring... 

i thought of something though... i was having shutdown problems and so when i was cleaning everything to get all the dust etc out i noticed that one of the female connectors on my 4 pin atx12v connector was burnt up... when i pulled it off the male part that's on the mobo seemingly wasn't effected... i had a donor computer lying around so i spliced the 4 pin atx12v from that into my power supply and reconnected and so far so good... no shutdowns and the new 4 pin atx is holding up and hasn't fried itself yet. 

i was wondering if that possibly burned out the +12v sensor and that's why i'm getting a 0 reading from lm-sensor.

---

### Post by Hakunka-Matata on 2011-03-27
I spent my entire working life troubleshooting electronics, mostly Radar.  When you have or have had smoke, all bets are off.  That being said, contemporary motherboards are some of the most resilient electronic devices I've ever worked with, they can take a lickin and keep on tickin.  
You can figure out a way to update the BIOS, I thought flashing BIOS didn't require a drive anyway...............

---

