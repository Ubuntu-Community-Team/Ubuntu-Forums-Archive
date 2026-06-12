---
title: "Samsung CLX-3175FN wrong colors"
date: 2010-03-07
forum: Hardware
---

### Post by mwildam on 2010-03-07
I bought a Samsung CLX-3175FN multifunctional printer,scanner,fax - and had an issue with colors printed awful. I imagine this also affects Samsung CLX-3175 and other variants available.

When installing the unified driver (from the Samsung site) under Ubuntu 9.10 it writes some information to /etc/modprobe.conf file. This is deprecated - and causes an error on boot (if you disable the nice splash screen you can see it). It only writes one line into this file and so I tried it simply deleting this file - error was gone and everything still works (please don't delete that file if you are unsure - best would be to check existence of that file before installing the unified driver).

Apart from that there is a second issue: Under Ubuntu 9.10 I either did not install any driver as it seemed to be plug & play as the printer was found automatically on the net.

However, the colors were awful and investigating the issue I found out that the plug & play version tried to use the

Samsung CLX-3175 Foomatic/foo2qpdl driver.

When installing the unified driver downloaded from the Samsung site, it installs the following driver:
Samsung CLX-3170 Series (SPL-C)

And this one - the latter - works correctly with the colors. I noticed that the Foomatic one offers different color correction options. I tried a few but none worked - even trying with no color correction at all.

So in short, the SPL-C driver (installed with the unified printer driver) from Samsung works fine and the Foomatic/foo2qpdl does not for the colors.

Hope this helps for everyone experiencing the same issue. I wasted a lot of paper until getting to that solution.

---

### Post by mwildam on 2010-03-07
I have contacted Samsung telling them about the issue and hope they will contact the right persons to get those things right. (I for myself do not know who are the right community members.)

---

### Post by rrinaudo on 2010-04-11
Hi, I just bought a Samsung CLX-3175. I had the same problem, Ubuntu default driver got the colors really wrong, then installing Samsung's unified driver and picking the 3175 got them wrong too. 

As you say selecting the Samsung CLX-3170 Series (SPL-C) is started to work great. 

Thanks a lot, I would have wasted a lot of time till I got this fix.

---

### Post by jb33 on 2010-05-15
Hi!

After downloading and starting the unified driver on Xubuntu 10.04 I get this error message. Can anyone help me what could be wrong?

loadResource: Failed to register resource </home/jb33/Letöltések/cdroot/Linux/i386/qt4apps/install/../../../noarch/install/share/ui/guiinstallui.rcc>
Failed to load widget from <:/forms/WizardTemplate.ui>

---

### Post by LarsSikstrom on 2010-07-24
> **jb33 said:**
> Hi!

After downloading and starting the unified driver on Xubuntu 10.04 I get this error message. Can anyone help me what could be wrong?

loadResource: Failed to register resource </home/jb33/Letöltések/cdroot/Linux/i386/qt4apps/install/../../../noarch/install/share/ui/guiinstallui.rcc>
Failed to load widget from <:/forms/WizardTemplate.ui>
Hello jb33,

I have read the other thread you started and added my bit.

I am still trying to get my CLX-3175FN to work with Ubuntu 10.04 32 bit version.
As you may have read the printer works very well for me with the 64 bit version.

This morning I followed a hint and installed "libqt4-dev", removed and saved all the content of my "Downloaded" map, downloaded again the Samsung unified driver, extracted "cdroot" and ran "cdroot/autorun". The installation failed and I got the same comment as the one you reported above.
I see that you wrote your post a couple of months ago and wonder if you found the solution or have changed to another version of Ubuntu in order to get the printer to work properly? If you have solved the problem I would surely love to know how!

Best regards

Lars

---

### Post by fabien29200 on 2011-02-06
This is a late answer but maybe it could help someone.

I had the error "failed to load widget" from the Unified Driver too.

I googled it and show the post of LarsSikstrom. I remarked that the path contained non ASCII character (also the case in my installation).

I moved the cdroot directory in a path that contained no non-Ascii character and it worked.

Good luck all.

---

### Post by Mudvayne on 2011-03-03
> **fabien29200 said:**
> This is a late answer but maybe it could help someone.

I had the error "failed to load widget" from the Unified Driver too.

I googled it and show the post of LarsSikstrom. I remarked that the path contained non ASCII character (also the case in my installation).

I moved the cdroot directory in a path that contained no non-Ascii character and it worked.

Good luck all.

Care to explain this in English to someone that just switched from windows I have the 3175 and it prints AWFUL in ubuntu 10.10 colors nothing like my wonderful Win7 printed...lol :/ I need this running as I use it for my business. Thx

**Actually with a little reading at the Samsung website when you click on the linux Unified driver beside where you download there is clear Ubuntu install instructions..works great now!! Or see below

[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

   $ sudo cdroot/autorun

4. After install, PPD path is set again.

   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

---

