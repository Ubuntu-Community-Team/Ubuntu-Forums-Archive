---
title: "Working Driver Ati Radeon Mobility HD 5650?"
date: 2010-11-20
forum: Hardware
---

### Post by KutViZ on 2010-11-20
I installed the proprietary fglrx driver and amdccc (or what is it) from synaptic, everything works fine but when i run catalyst control center it says my graphic card is ATI Mobility Radeon HD 4200 Series. So i guess that the driver not supports the 5xxx series so far. I searched the internet but so far I couldn't find any solution. 

And there is a proof that i really have 5650:
Terminal:
> 
gepzsir@gepzsir-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)


I also typed fglrxinfo, and a question came up that the OpenGL version is too old:
> 
gepzsir@gepzsir-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 1.4 (3.3.10237 Compatibility Profile Context)
How should I fix this?

---

### Post by alanmoore78 on 2010-11-20
Have you tried disabling the on-board (HD4200) graphics in the BIOS?

---

### Post by KutViZ on 2010-11-20
Can't see any option to do that in BIOS... 

I assumed that the driver is too old, but don't know how to update it correctly.

To make some things correct, i'm using a laptop...

---

### Post by glaildo on 2010-12-23
Hello, I am with the trouble, ubuntu detect only ati 4200 instead of ati 5650.
I am almost crazy... I tried many things, but nothing!!!

---

### Post by v4mpiro on 2012-01-27
Same here, even with the new 12.1 Catalyst drivers. I also tried using aticonfig to set up all the adapters but it doesn't work.

---

### Post by Mark Phelps on 2012-01-27
This thread is about problems when you have TWO ATI video cards installed, one is being used by default, and you can't use the other one.

If you other folks do NOT have that problem, please go start your own threads -- as trying to solve DIFFERENT problems in the same thread makes the situation too confusing.

That said, this sounds like it may be solvable using the switchable (hybrid) graphics solutions -- read below:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by v4mpiro on 2012-01-27
I know, that's why i asked for help in this thread. I also have two ati cards, and I can use only one of them. The link YOU suggested is not useful, we are trying to use the CATALYST drivers, the open source drivers have bad power management and overheat the notebook. Thanks anyway for the suggestion.

---

### Post by devil_ua on 2012-03-19
> **KutViZ said:**
> Can't see any option to do that in BIOS... 

I assumed that the driver is too old, but don't know how to update it correctly.

To make some things correct, i'm using a laptop...

did you solved problem? i have same issue, besides when i'm using fglrx system is too slower. So i decided to use open source drivers and vgaswitcheroo for some time while developers are not solved this problem

---

### Post by bcarlowise on 2012-03-19
If your system truly has the HD 5650 then the proprietary ATI drivers should show that. Are you sure you are using the proprietary drivers from AMD or are you using the open source drivers that Ubuntu detects and allows you to install via the "Additional Drivers"?

My suggestion is this....go to the AMD site here and download the correct driver package for your system:

[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

Then follow the instructions contained in the following link to completely uninstall what you currently have installed and then install the AMD proprietary drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

If you follow the instructions you will have the right AMD proprietary drivers and you will get the full performance benefit of your ATI graphics. I am willing to bet that after you do that the AMD Catalyst Control Center app will report the correct graphics.

---

### Post by devil_ua on 2012-03-19
> **bcarlowise said:**
> If your system truly has the HD 5650 then the proprietary ATI drivers should show that. Are you sure you are using the proprietary drivers from AMD or are you using the open source drivers that Ubuntu detects and allows you to install via the "Additional Drivers"?

My suggestion is this....go to the AMD site here and download the correct driver package for your system:

[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

Then follow the instructions contained in the following link to completely uninstall what you currently have installed and then install the AMD proprietary drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

If you follow the instructions you will have the right AMD proprietary drivers and you will get the full performance benefit of your ATI graphics. I am willing to bet that after you do that the AMD Catalyst Control Center app will report the correct graphics.

i'm tried this instructions several times but all the same, system uses integrated ati 4200 and can't switch to 5650

P.S

```
sk@Pavilion:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series] (rev ff)

```

ubuntu has detected both video cards when i've  installed Catalyst 11.12  but its performance is too much slower

---

### Post by v4mpiro on 2012-03-20
I spent many days trying to configure the Catalyst but there's no way to let it use the 5650. We must wait for the upcoming 12.3 drivers, hoping they will solve the problem.

---

