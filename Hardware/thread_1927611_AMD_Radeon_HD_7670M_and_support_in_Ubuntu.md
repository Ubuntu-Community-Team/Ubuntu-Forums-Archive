---
title: "AMD Radeon HD 7670M and support in Ubuntu?"
date: 2012-02-18
forum: Hardware
---

### Post by ITCompozer on 2012-02-18
Hi There,

I want to buy a Notebook with AMD Radeon HD 7670M.

Is it supported by Ubuntu?

I can't find drivers on AMD/ATI website for Linux and Windows.

Notebook model:
Acer AS7750G

---

### Post by Yellow Pasque on 2012-02-18
Open-source ati driver does not support the 7000-series, and support for the 7970 just appeared in Catalyst 12-1, so my guess is that the 7670M is not supported at the moment.

---

### Post by mgt2000 on 2012-03-17
AMD Radeon HD 7xxx series are not supported in Linux until now and even the latest version of Catalyst 12.2 doesn't support these video cards.
The open-source software doesn't support this cards too.

---

### Post by bcarlowise on 2012-03-19
I would try the latest driver from AMD just to see if it will work:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Use the instruction here for uninstalling what you currently have installed and installing the AMD driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by sunveer on 2012-06-22
> **bcarlowise said:**
> I would try the latest driver from AMD just to see if it will work:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Use the instruction here for uninstalling what you currently have installed and installing the AMD driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)


Does it work now?

---

### Post by zSeries on 2012-06-22
I have been running running Catalyst 12.4 on 10.04 LTS with Radeon HD 7700 for weeks. I havent had any problems at all.

---

