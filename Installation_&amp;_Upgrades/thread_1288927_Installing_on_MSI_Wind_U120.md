---
title: "Installing on MSI Wind U120"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by zahnac on 2009-10-11
I would like to install the Netbook Remix on my MSI u120, but it appears that the u120 is one of the only netbooks in the world that will NOT boot from a USB flash drive. I want to try an install via "Unetbootin" from Windows but I need an ISO image of Remix. All I can find are .IMG versions. 

Is there an ISO version available for download? OR, alternatively, if anyone has install Netbook Remix onto a u120, can they tell me how they did it?

:confused:

---

### Post by rreese6 on 2009-10-12
there is a program called imagewriter you can find in package manager that will put it on the USB for you

---

### Post by zahnac on 2009-10-12
Thank-you, I'm aware of that utility. However, the MSI U120 will NOT boot from a USB Flash drive. Therefore I'm still looking for an ISO image of remix so I can use the Unetbootin utility to attempt the install.

---

### Post by rreese6 on 2009-10-12
I found this info about the U100 Maybe something there might help you.
[http://msiwindpc.net/2008/09/28/how-to-install-the-ubuntu-8041-on-the-msi-wind-u100/]("http://msiwindpc.net/2008/09/28/how-to-install-the-ubuntu-8041-on-the-msi-wind-u100/")

Also this looked interesting:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")
It speaks about using the LiveCD ISO

---

### Post by saleminkb on 2009-10-26
Hi, all

I have an interesting situation.  I installed unr 9.10 rc on my msi u120 with the use of a usb stick.  The installation went fine and everything works except the usb ports.  I know it isn't a hardware problem because I installed over usb.  I thought that usb support was integrated into the kernel.  If anybody can provide some insight it would be appreciated.

---

### Post by francsal on 2009-10-26
> **saleminkb said:**
> Hi, all

I have an interesting situation.  I installed unr 9.10 rc on my msi u120 with the use of a usb stick.  The installation went fine and everything works except the usb ports.  I know it isn't a hardware problem because I installed over usb.  I thought that usb support was integrated into the kernel.  If anybody can provide some insight it would be appreciated.

I regularly boot rom the USB ports on my U120, so, I really don´t think that should be an issue. Sorry for asking a probably dumb question, but are you pressing F11 in the boot process? Also, have you tried with a different USB memory?

As for the USB ports working, on mine they work MOST of the time. I had this problem that sometimes my 3G modem and my memory stick would not be recognized, but that was solved in the RC version. Also, they worked just fine in Jaunty. I did the upgrade to 9.10 because of the 3G modem.

Frank.

EDIT: Regarding your original question, I have two answers. First, I was able to try Kubuntu Netbook Remix, booting from a USB memory stick. It worked just fine, but, I do prefer the traditional Kubuntu desktop. Also, regarding the IMG vrs ISO problem, I used MagicISO to convert from IMG to ISO (Actually, I mounted the IMG using MagicDisc, and then used MagicISO to convert the mounted "CD" to an ISO file. Then, used Unetbootin to make a bootable USB with the ISAO image, and voila, it worked flawessly.

---

### Post by saleminkb on 2009-10-26
There are no problems booting from usb.  The problem is that once I am in ubuntu the usb ports do not work.

---

### Post by paddy2k on 2009-10-27
I am having a similar issue on a  MSI Wind U120 OEM netbook (Targa Traveller 1016)

I have tried to boot, the Kubuntu NBR Alpha 5 , Ubuntu NBR Alpha 5 , Kubuntu Alpha 5, Ubuntu NBU RC, Ubuntu Moblin RC and Kubuntu RC, each with varied results.

Sometimes they boot, other times they don't. The NBR RC, Mobilin Alpha 5 & RC booted first time, but have failed to boot since. The boot screen either fills with text moving so fast I can't ready it or stops loading crypto disks.

When trying the beta I was able to boot using the option APCI=off  but would not like to have to do that. Having logged a [ticket]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/428632") for the issue with the Alpha 5 I was told my USB media was to blame, however I've used 4 different types of media. 

I don't know if the issue only effects the live version or would it happen to a full install hence am wary of upgrading my 9.04 install as it works perfectly.

---

### Post by saleminkb on 2009-10-27
From what I see, alot of people are having issues with Karmic on netbooks after the latest updates.  My usb ports/devices worked when I first installed but stopped working after updates,  I am wondering whether this has to do with the added support for usb 3.0 in the latest kernel.

---

### Post by chernoknizhnik on 2009-10-31
> **saleminkb said:**
> There are no problems booting from usb.  The problem is that once I am in ubuntu the usb ports do not work.

I have MSI Wind 100 Plus same issue-USB not forking and I also can`t activate Bluetooth with Fn+F11.

---

### Post by saleminkb on 2009-11-03
If you can live without your webcam on your msi wind, post #28 at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352) should fix the usb issues. It is a problem with the uvcvideo conflict of ubuntu and the bios, which jams up the webcams usb synch.  This causes errors for the entire usb controller.

---

### Post by paddy2k on 2009-11-10
Disabling the webcam using Fn + F6 at boot up worked perfectly and was able to boot and install Kubuntu 9.10.

The underlying issue still remains but the workaround is ok for now.

---

