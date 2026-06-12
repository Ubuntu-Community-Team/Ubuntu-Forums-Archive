---
title: "Driver Radeon HD 4200"
date: 2015-10-30
forum: Hardware
---

### Post by nipponicshell on 2015-10-30
I'm trying to install the driver, even already follow some tutorials I found on the internet, when you install and restart the notebook ... I can not access the system, the login screen appears for entering the password, put the password and back again to the login screen, I tried putting out the Xauthority and creating a new user, even by downloading the driver from the AMD website itself.

 steps

 1 - under the driver for the AMD website, run the amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run file appears the options, you need to start speaking the fglrx driver, if I install before and I try to run later, says that the driver is old and asks to uninstall.

 2 - the central programs it installs but says that there was an error starting the Catalyst Control, there is no graphics driver installed AMD or is not working properly.

Ubuntu 14.04.3 LTS x86

---

### Post by QIII on 2015-10-30
Hello!

AMD no longer provides Linux support for adapters prior to the HD 5000 series.

Your card is not supported by AMD.  You will need to continue using the default open source Radeon driver that was installed with Ubuntu.

---

### Post by Bashing-om on 2015-10-30
nipponicshell; Regrets, but:

Ninja'd by QIII; 
I do add :
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.++ uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. Terminal command -> X -version to determine the x-server version.

Open source driver for your card is the only recommendation .

[INDENT]sad but that is the way it is
[/INDENT]

---

