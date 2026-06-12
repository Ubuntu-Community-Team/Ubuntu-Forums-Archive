---
title: "AMD FirePro Workstation FGLRX not working"
date: 2015-09-20
forum: Hardware
---

### Post by nickyforiasha on 2015-09-20
I recently bought an AMD FirePro 3D v9800 and I am unable to get fglrx to work. The latest version of the workstation driver is 14.502, and installing it through "generate distro package" boots Ubuntu in low graphics mode, completely unable to start Unity. Installing the driver on xorg gives me an error in the end. Checking fglrx-install.log, it says please install all necessary packages, and before proceeding I installed them through apt-get. Next time I get the error after the installation, and the log file tells me to install necessary packages but doesn't list anything.


In the end, both install methods fail. The one method that works is through "Additional Drivers" on the Ubuntu Update/PPA manager. Installing it that way works, however instead of installing the workstation driver 14.502, it seems to install the radeon driver 15.20 (in both "fglrx" and "fglrx-updates". Desktop is stable, but launching any application that uses OpenGL shows serious screen artifacts, making it impossible to even read text on the screen. OpenCL also freezes and crashes when being used by an application.

I have done this on Ubuntu 15.04, and after about 10 driver reinstalls, Unity broke and I downgraded and installed 14.04. I unfortunately lost a very lucky and stable installation of 15.04, but getting the card to work is more important. I tried multiple configurations and ways to install the driver on 14.04LTS including apt-get and dpkg, but it never works. I reinstalled 14.04 about 8 times in the last week trying to get this to work, I'm afraid I am wearing out my SSD.

I need help in getting the official amd.com driver to work. Any suggestions and especially answers are appreciated. Thanks in advance!

---

### Post by wildmanne39 on 2015-09-20
Please> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
Do not cross post, or post the same thing in multiple locations.
Thanks

---

### Post by howefield on 2015-09-21
Thread moved to the "*Hardware*" forum, probably a better fit for your question than "*Ubuntu Phone and Tablet*"

---

### Post by Yellow Pasque on 2015-09-21
> I tried multiple configurations and ways to install the driver on 14.04LTS including apt-get and dpkg, but it never works
Be more specific.  Does it install at all? If it doesn't, give the output of apt or the fglrx-install.log. If it does install, but doesn't boot/work, try to get the /var/log/Xorg.0.log file (or see /var/log/Xorg.0.log.old if you have to reboot into a different configuration after the failed boot).

> I have done this on Ubuntu 15.04
Ubuntu 15.04 (or more specifically, Xserver version 1.17) is not supported by the Catalyst Pro 14.502 driver.

---

### Post by nickyforiasha on 2015-09-22
> **Temüjin said:**
> Be more specific.  Does it install at all? If it  doesn't, give the output of apt or the fglrx-install.log. If it does  install, but doesn't boot/work, try to get the /var/log/Xorg.0.log file  (or see /var/log/Xorg.0.log.old if you have to reboot into a different  configuration after the failed boot).


Ubuntu 15.04 (or more specifically, Xserver version 1.17) is not supported by the Catalyst Pro 14.502 driver.


yes it installs, all methods install. It just doesnt work. I  know amd like to make drivers on older xorgs which always pissed me off.  For that I tried rolling back to 14.04 and also debian jesse (which has  xorg 16 or 15 dont remember). Also how do you know? The radeon driver  page on [amd.com]("http://amd.com") has a installer notes section that says this, but the  workstation driver doesnt seem to have this kind of file. Have you tried  the driver 14.502 and approve that it works?(just wondering). Anyways,  heres /usr/share/ati/fglrx-install.log when installing on "xorg 6.9 or later":

NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Supported adapter detected.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.

Creating symlink /var/lib/dkms/fglrx/14.502.1040/source ->
                 /usr/src/fglrx-14.502.1040

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/14.502.1040/build; sh make.sh --nohints --uname_r=3.19.0-28-generic --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-14.502.1040 with DKMS
[Error] Kernel Module : Removing fglrx-14.502.1040 from DKMS

------------------------------
Deleting module version: 14.502.1040
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs


When attempting to install through generate distro package, it closes and the log file says i need to install rpmbuild. It gives different instructions on how to do it in suse, and redhat even thought im on ubuntu (deb). it used to always work in radeon. I can force the installation and it generates packages and i just install them through dpkg. When all 4 (fglrx, fglrx-core, fglrx-amdcccle, and fglrx-dev) are installed, the computer boots and there is no gui. I can remove amdcccle, and fglrx leaving fglrx-core and it works through low-graphic mode on a small resolution,. This is the only piece of the driver that seems to work, when installed through generate distro package, and leaving only fglrx-core installed, but of course that isnt enough for everyday use.

Please ask more questions or suggest something, i want to cooperate. i need to fix this problem.

---

### Post by Yellow Pasque on 2015-09-23
> Have you tried the driver 14.502 and approve that it works?
No, but this person has, and also points to helpful patches to fix the build error (including one to solve the issue where the installer thinks you are running an RPM distro):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1450089/comments/11](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1450089/comments/11)

Just to be sure, you did not install Ubuntu 14.04.3, correct? That has Xserver 1.17 in it..

---

