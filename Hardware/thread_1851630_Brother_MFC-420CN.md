---
title: "Brother MFC-420CN"
date: 2011-09-28
forum: Hardware
---

### Post by Twinturbo120 on 2011-09-28
Where to begin..The drivers for the particular printer aren't displayed on ubuntu's list so I go to the brother website to download them. I download the lpr driver and install it. I go back to the list and it still doesn't appear there. I try 4 different "generic" drivers and those don't seem to work. 

In the menu where it says to pick driver there is an option for a PPD file. But the website of the printer doesn't have any PPD file =/ Any help would be greatly appreciated!

---

### Post by kurt18947 on 2011-09-28
I can't help with a .ppd file because I don't have that model.  You installed the lpd driver, did you also install the CUPS driver?  I install both. I'm under the impression - correct or not - that Ubuntu uses the CUPS driver but you have to install the LPR driver before you can install the CUPS driver.  I assume you also looked at the "pre-required" steps. The LinuxPrinting web site has been down for the past week or so.  That might be why the foomatic database is not available though I'm not sure the two are related.  Not all Brother printers have non-Brother source drivers available.  Synaptic has Brother print drivers listed but aside from the Brother Laser CUPS driver I haven't tried them.

---

### Post by Twinturbo120 on 2011-09-28
> **kurt18947 said:**
> I can't help with a .ppd file because I don't have that model.  You installed the lpd driver, did you also install the CUPS driver?  I install both. I'm under the impression - correct or not - that Ubuntu uses the CUPS driver but you have to install the LPR driver before you can install the CUPS driver.  I assume you also looked at the "pre-required" steps. The LinuxPrinting web site has been down for the past week or so.  That might be why the foomatic database is not available though I'm not sure the two are related.  Not all Brother printers have non-Brother source drivers available.  Synaptic has Brother print drivers listed but aside from the Brother Laser CUPS driver I haven't tried them.

I tried to install the CUPS driver with the software manager but every time I do, the little tab that says "install" still says install even after I installed it. If that makes sense >.> So I have a feeling the CUPS driver isn't installed at all.

---

### Post by kurt18947 on 2011-09-29
> **Twinturbo120 said:**
> I tried to install the CUPS driver with the software manager but every time I do, the little tab that says "install" still says install even after I installed it. If that makes sense >.> So I have a feeling the CUPS driver isn't installed at all.
I wonder if software center is being .......difficult.  You could try installing from the command line as shown in the instructions on Brother's drivers download package.  I've downloaded & installed the Gdebi installer which seems to me a little less fussy than the software center.  Are you running a 32 bit or 64 bit install?  I assume 32 bit because you didn't get an error message about wrong architecture but Brother's drivers *must* be installed from the command line on 64 bit systems.

---

### Post by rewyllys on 2011-09-29
Twinturbo, I suggest trying the Brother printer driver installation script that I discuss in this thread:
[http://ubuntuforums.org/showthread.php?t=1850454&highlight=brother+printer+install+script](http://ubuntuforums.org/showthread.php?t=1850454&highlight=brother+printer+install+script)

---

### Post by Twinturbo120 on 2011-09-30
> **rewyllys said:**
> Twinturbo, I suggest trying the Brother printer driver installation script that I discuss in this thread:
[http://ubuntuforums.org/showthread.php?t=1850454&highlight=brother+printer+install+script](http://ubuntuforums.org/showthread.php?t=1850454&highlight=brother+printer+install+script)

I'll give it a try, thanks bud.

---

