---
title: "Can't install OSS sound driver"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by RoboRob on 2005-04-12
Hi,
Just starting out with linux.
Installed a dual boot WinXP/Ubuntu 5.04 but in ubuntu I have no sound.
In past distro's I tried (Mandrake,Redhat) I had the same problem but managed to install the OSS driver.

I'm having problems installing the OSS sound drivers in ubuntu. My sound card is a Terratec Aureon 7.1 Universe.

Did a lspci :
0000:00:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy2 4PT/HT] PCI Multi-Channel Audio Controller (rev 01)

When installing the OSS sound driver I get an error:

roborob@master-pc:~/tmp$** sudo ./oss-install**
One or more applications are currently using sound:
        10702   /usr/lib/mozilla-firefox/firefox-bin
OK to close them (Y/N) ? y
Sending termination signals
Sending kill signals
Checking for any previously installed sound drivers...
*** Sound driver is already running - trying to unload it ***


You appear to have the the kernel level sound driver installed as a loadable
module. Unload it by executing rmmod sound and try installing OSS/Linux again.

If this error repeats again you probably have the sound driver being loaded
automagically by the kerneld daemon. In this case you should log out from the
X Windows session, then press <ctl><alt><F1> and log in on the Linux console
as root and then install OSS again.

Am I allowed to do these changes automatically for you (Y/N) ? y
Trying to disable the conflicting sound driver

roborob@master-pc:~/tmp$ **rmmod sound**
ERROR: Module sound does not exist in /proc/modules

Anyone using the Terratec Aureon 7.1 Universe with ubuntu?

---

