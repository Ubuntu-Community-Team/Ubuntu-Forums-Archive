---
title: "Having problem installing driver for Radeon Mobile x1270"
date: 2010-03-22
forum: Hardware
---

### Post by The Flying Penguin on 2010-03-22
I bought myself a MSI Wind U210 laptop several months ago and have installed Ubuntu 9.10 on it. It runs great except for my graphics card. Compiz works great but sometimes really fast video is choppy even below 480p. Since it runs great in XP I figured this must be because of my graphics driver in Ubuntu.

My graphics card is a Radeon Mobile X1270.

Here is my xorg.conf file:
> Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2646 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
Now I am not an expert but that does not look like my card is properly installed. I should see some info on it right? 

I downloaded Envyng to try and install the ATI driver. It shows a candidate version of "8.660-0ubuntu4" but when I try to install it I get this:

>  Downloading the packages...
dpkg: status database area is locked by another process
dpkg-exec: Running dpkg

Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 303, in mainMenu
    a.driverMenu('fglrx')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 164, in install
    self.cache.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 318, in commit
    raise SystemError("installArchives() failed")
SystemError: installArchives() failed
I went to ATI's website to manually download a driver but they refer me to my laptop manufacturer's website. Of course, MSI doesn't have a Linux driver.

I'm not really sure how to proceed. I looked through the package manager for ATI and Radeon drivers but I'm not really sure which ones to install and several are already installed.

Any help would be greatly appreciated.

---

### Post by The Flying Penguin on 2010-03-22
Ok, I did a little more fooling around. I followed the instructions from [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) for group 1 as I have the RS690. That changed nothing.

I installed Catalyst Control Center and it says there is no ATI driver installed or it is not functioning. Entering aticonfig in the terminal gives me the message "No supported adapters detected".

Isn't 10.04 supposed to support my card right out of the box?

---

### Post by Yellow Pasque on 2010-03-22
The open-source radeon driver is pre-installed. The proprietary fglrx/Catalyst driver no longer supports this chip (ATI has considered it 'legacy' for about a year now). If you tried the latest drivers from xorg-edgers, that is the best you can do.

BTW, CCC and aticonfig are tools of fglrx, which is why they don't work for you. Uninstall CCC.

---

### Post by The Flying Penguin on 2010-03-23
After installing the latest drivers from xorg-edgers I am no longer able to enable compiz and video playback is very now choppy now. 

Is there something I can do to fix this? Would you recommend going back to the open source driver that came pre-installed or should I use the last supported proprietary driver?

---

### Post by The Flying Penguin on 2010-03-24
Well, did a little more research and according to this post [http://http://www.phoronix.com/forums/showthread.php?t=18218]("http://http//www.phoronix.com/forums/showthread.php?t=18218") the ATI 9.3 driver will no longer work under 9.10? Is this true? Are my only options to use the open source driver that is installed by default or the bleeding-edge drivers?

Did the 9.3 ATI driver provide full x1270 support in previous Ubuntu releases? If my goal here is to get my card working fully, would installing a previous Ubuntu version and the 9.3 driver solve my problem? I just want to be able to playback my videos smoothly and perhaps even a little 3D gaming on the side.

Perhaps I have done something wrong here. Do I need to edit the xorg.conf to make Ubuntu use the bleeding-edge driver? [http://http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers]("http://http//wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers") says to add the line "radeonhd" but I don't have a radeon hd, I have a x1270.

I'd really appreciate any input here. I've put in a lot of time getting this far and I just don't quite want to give up yet.

---

### Post by Yellow Pasque on 2010-03-25
> the ATI 9.3 driver will no longer work under 9.10? Is this true?
Yes.
> Did the 9.3 ATI driver provide full x1270 support in previous Ubuntu releases? If my goal here is to get my card working fully, would installing a previous Ubuntu version and the 9.3 driver solve my problem?
Yes and probably. The problem is that you'd have to go back to Hardy/8.04. I guess you could use Intrepid/8.10, but Hardy has more software available and Intrepid is about to go EOL in terms of support/updates. One other possibility is using Jaunty/9.04 and downgrading the Xserver to get the proprietary drivers installed.

---

### Post by waynefoutz on 2010-04-19
This card and ATI catalyst 9.3 will only work with intrepid or earlier. The new Lucid beta runs pretty good, however. 2d and Compiz work flawlessly, but 3d there are some glitches. SupertuxKart does not display properly, neither does Google earth.Also running windows games under WINE is a problem.  90% of the Linux-native 3d games in the repositories work fine. The default open source drivers in the Lucid beta aren't anywhere as good as Hardy with the Catalyst driver, but compared to what they were in Jaunty, they've come a long way. 

I resorted to installing an old Windows XP partition on my drive for when I want to do any gaming. 

Another option you could go with a laptop with this chipset is to install Debian Lenny and 9.3 Catalyst. Lenny still has the older version of xserver

---

### Post by Saint Nick on 2010-07-26
I went to Intrepid/8.10 which allowed for my X1270.  However, I'm currently having problems with Doom 3 but I'm not sure if it is related.

---

### Post by Saint Nick on 2010-07-28
The doom3 issue was not graphics related by screen resolution related.  I had to start the game in window mode and had no further problems.

---

### Post by The Flying Penguin on 2010-07-31
Whoah, I guess I never followed up on this. Since it has been brought back to life with this last post I figured I'd update.

What was the solution? I sold the laptop (after barely six months of ownership) and bought a new one that had a graphics card with full Linux 3d support. I bought an Asus UL30VT with an Intel 4500MHD and Nvidia G210M hybrid graphics. The hybrid graphics aren't supported but the G210M is with full 3d support thanks to a proprietary driver from Nvidia.

---

### Post by Saint Nick on 2010-07-31
You just had to go to an older version of Ubuntu 8.10/8.3.  I went to 8.10 and was able to install the appropriate driver for the X1270.

---

### Post by The Flying Penguin on 2010-08-01
> **Saint Nick said:**
> You just had to go to an older version of Ubuntu 8.10/8.3.  I went to 8.10 and was able to install the appropriate driver for the X1270.

Well, yeah. I could have done that but I wanted to run the latest and greatest version of Ubuntu. My excitement had been building for the release of 10.04 and there was no way I wasn't going to run it ;)

And btw, 8.10 is no longer supported. I would go to 8.04 since it's still supported until April of 2011.

---

