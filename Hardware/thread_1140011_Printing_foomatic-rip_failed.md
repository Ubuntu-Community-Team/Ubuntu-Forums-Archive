---
title: "Printing: foomatic-rip failed"
date: 2009-04-27
forum: Hardware
---

### Post by VCoolio on 2009-04-27
I'm trying to print with a perfectly avarage hp laserjet, but no luck. It says: /usr/lib/cups/filter/foomatic-rip failed. I googled it, found truckloads of printing problems with Jaunty which makes me really sad, also found this error but no (understandable) solution. 
- I did reinstall everything with foomatic in it
- I did change the file /etc/papersize to a4 (I read someones remark that it should not be letter, but foomatics site says it should, so I reset it to letter as it did not make any difference)
- I did a reboot
Hope you have some ideas on this. I've attached a very long .txt-file that was kindly created by troubleshoot (I had to zip it because the size exceeded this forums max .txt size). Maybe you know what to do with it.

---

### Post by VCoolio on 2009-04-27
SOLVED: used the driver [here]("http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-LaserJet_6P&show=0") instead of the one that was automatically used when adding printer. Hurray !! Jaunty still rocks afaic :guitar:

---

### Post by triplemaya on 2009-05-07
I solved it a different way, posted here in case it helps anyone.

I too have an aged laserjet, a 5L, and I couldn't find any way to try a different driver. The system installed the hplip driver by default, and I could not change this. I went through the loop of trying to install a different driver, or change the URI in the printer configuration, but it kept going back to the hplip driver. But I was sure that the URI was not the same as previously (I don't have a record of that but it looked unfamiliar and it didn't mention 'parallel'.) 
Fortunately I still had the previous install, 8.10 which worked fine, on another hdd, so I fired it up again. In that install the URI was 
```
parallel:/dev/lp0
```
 so I just pasted that into the URI in the new install, and once again tried to change the driver. This time I got to chose the 'standard', ie I presume older, driver, called 
```
HP LaserJet 5L Foomatic/ljet4 (recommended)
```
 from the list of HP printer drivers, and it worked perfectly after that.
I am not recommending any of this, or saying others should have parallel:/dev/lp0 as their URI ( obviously my printer is aged and connected to the parallel port) but hopefully the info will be of use to someone.

---

### Post by tobjai on 2010-10-26
Unfortunately theses "solves" don't work for people with different printers. Isn't there a way to just fix whatever is wrong with this foomatic-rip thing?

---

### Post by war.ace on 2011-02-11
I have an HP laserjet P1505 and I'm getting this error with the foomatic-rip as well. How can I go about fixing that?

---

### Post by jringoot on 2013-02-20
Just a quick note on the papersize: this really depends on the real physical size of the paper, should be clearly indicated on the paper pack and often there are markers in the paper-tray indicating the papersize.
In Europe traditionally A4 is used (see [http://en.wikipedia.org/wiki/DIN_476](http://en.wikipedia.org/wiki/DIN_476))
In the US they traditionally use more often letter format.

---

### Post by codemaniac on 2013-02-20
Old thread closed.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

