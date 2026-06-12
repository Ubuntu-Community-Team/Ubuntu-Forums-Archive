---
title: "Boot hangs for 5 seconds"
date: 2009-11-08
forum: Hardware
---

### Post by frojnd on 2009-11-08
Hello there. 

When I boot Ubuntu 9.10 clean install on acer aspire 5410 It hangs for about 5 seconds. I've checked the dmesg and found this:

pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001

Which I belive it's responsble for all this.

I've red the forum and found that if you in bios disable boot plug and play it fixes the problem. Problem is that in my motherboard there is no such option pap. Any help would be appreciated.

---

### Post by frojnd on 2009-11-20
I just find out, that flashing the bios might help solved this prolbem. There is however one problem. I have no idea how to do this on a linux. I did a little research first. I found that the my current bios version is V1.15 on my Acer Aspire 5410. But if I go to a official page: [http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360](http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360) Notebook -> Aspire -> Aspire 5410, even the picture shows it's ok. Then I select Bios and I see a bunch of versions there. And if I sort it by date I see that my bios was published on 2009/06/02 and the newest version is 1.31

However this is for WINDOWS. How can I flash bios on Linux. And any instructions or mini howto would be more than appriciated.

---

### Post by Bunnybugs on 2009-11-20
> **frojnd said:**
> Hello there. 

When I boot Ubuntu 9.10 clean install on acer aspire 5410 It hangs for about 5 seconds. I've checked the dmesg and found this:

pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001

Which I belive it's responsble for all this.

I've red the forum and found that if you in bios disable boot plug and play it fixes the problem. Problem is that in my motherboard there is no such option pap. Any help would be appreciated.

Well, I know that it's possible to update your BIOS from windows.... how to do that in GNU/Linux, and specially, Ubuntu... I don't know:S

Sorry mate

---

