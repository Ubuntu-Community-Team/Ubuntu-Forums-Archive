---
title: "ubuntu graphics card problem"
date: 2012-09-14
forum: Hardware
---

### Post by snowlizard31 on 2012-09-14
Hey , I have ubuntu installed on my iMac model 8,1 and it randomly goes to sleep, sometimes when it gets out of sleep mode the screen goes light blue but you can still see the desktop apps and everything and it doesn't go back to normal untill I restart my computer. So my question is, is this because my graphics card isn't supperted. Is my graphics card even supported.

iMac 8,1
 graphics card ATI Radeon HD 2600 PRO
processor Intel Core 2 Dou 2.80GHz

---

### Post by Epodx64 on 2012-09-15
I might be wrong but i -dont- think that model of Ati card is supported anymore.

---

### Post by typhoon_tip on 2012-09-15
Your card is officially supported by AMD Legacy structure.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

Just download the file, unzip and follow the instructions here to install the driver manually:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I suppose you are using Ubuntu 12.04, correct ?

And please, follow letter by letter ALL instructions there (you may have to change the name of executable downloaded, because this page refer to _current_ driver, which is different than _legacy_, but instructions works in exactly the same way !!).

I just installed this driver on my computer the other day. Works perfectly !

---

