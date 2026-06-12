---
title: "Radeon 7850 2 GB drivers?"
date: 2014-05-16
forum: Hardware
---

### Post by maazmahmood on 2014-05-16
Installed xUbuntu 14.10 on my computer with Radeon 7850 2 GB GPU. And was wondering to stick with open source drivers OR download drivers from amd.com? 

Which brings me to a few more questions:
1) I was looking at this link, and it says that the closed source is faster in somethings (3D) but doesn't support older chip sets (not my problem fortunately). So is that 3D as in 3D gaming? Or 3D as in 3D models and such? 
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

2) When I open up additional drivers in the settings menu I see parentheses with open and proprietary drivers, does that mean if I download the drivers from amd website I can freely switch between open source and the ones that I download from the website? 

3) What's the difference between the proprietary drivers online and the ones on that menu screen? 


Thanks in advance


**Update** Ok well I went ahead and downloaded/installed the driver from the website. Now I had to do some tweaking, and got frustrated and hit the proprietary driver again this was after the website version was installed so I'm not sure if it overrode the other or not how do I check exactly?

---

### Post by Mark Phelps on 2014-05-17
Answers to your questions:
1) That is 3D as in Gaming.
2) I've not actually tried it, but I do not believe that you can easily switch between driver versions.
3) The ones offered through additional drivers have already been packaged as .deb files, and if you install those, they will automatically get updated when you update kernel versions.  The ones offered through the AMD site have to be installed using their script, although they do have the option to build packages from them.  But, every time you do a kernel update, you have to reinstall the drivers because they are kernel-version-specific and do not automatically update.  The ones from the AMD site, however, tend to be newer than the ones through Additional Drivers.

---

### Post by maazmahmood on 2014-05-17
how do you build a package from them? Sorry new to all this

---

### Post by maazmahmood on 2014-05-17
I've been reading this link , and it says to install a list of packages, now some of these packages have dependencies, so instead going on a scavenger hunt can I just download the main package, like for gimp-help-en I just download gimp overall? Will installing gimp install all those packages? And if downloading overall does count some of those software I already, like I think I have gimp already so to check to make sure i have gimp-help-en is there a command to help me find that?



[http://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst14-4LINReleaseNotes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst14-4LINReleaseNotes.aspx)

---

### Post by Yellow Pasque on 2014-05-17
> **maazmahmood said:**
> I was looking at this link, and it says that the closed source is faster in somethings (3D). So is that 3D as in 3D gaming? Or 3D as in 3D models and such?
Both.

> When I open up additional drivers in the settings menu I see parentheses with open and proprietary drivers, does that mean if I download the drivers from amd website I can freely switch between open source and the ones that I download from the website?
Probably not without rebooting.

> What's the difference between the proprietary drivers online and the ones on that menu screen? 
The drivers in Trusty repo are slightly older (based on Catalyst 14-3 beta).


> Ok well I went ahead and downloaded/installed the driver from the website. Now I had to do some tweaking, and got frustrated and hit the proprietary driver again this was after the website version was installed so I'm not sure if it overrode the other or not how do I check exactly?

So you're installing different versions over each other without uninstalling first (and you probably didn't package the website version)?  Sigh...
You're lucky X still starts.
To properly install website version, see: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)
(and make sure you remove any installed version first!)

---

### Post by maazmahmood on 2014-05-17
Hahah, i broke it :D, no worries, I was able to uninstall it and just went with the driver from additional drivers

---

### Post by Mark Phelps on 2014-05-17
When you RUN the AMD installer ( the .run file) downloaded from the AMD website, it puts up a window and one of the options is to build packages.  When you select that, it will build the packages needed.  After that, all you need to do is reinstall the packages after each kernel upate.

---

### Post by Yellow Pasque on 2014-05-17
> **Mark Phelps said:**
> When you RUN the AMD installer ( the .run file) downloaded from the AMD website, it puts up a window and one of the options is to build packages.  When you select that, it will build the packages needed.  After that, all you need to do is reinstall the packages after each kernel upate.

If you have dkms installed, you don't need to manually reinstall for new kernels. [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)

---

