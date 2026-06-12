---
title: "Upgrade killed my PC"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by beach_defender on 2009-08-30
Hi,
I thought that I published this question earlier today, but I must have killed the window before submitting.

Anyway, I recently did a silly thing and hit the 'upgrade' button in synaptic to upgrade from 8.10 to 9.04

It didn't go well.

I had some errors and during the reboot I get the following output before everything hangs - that is no windows, nothing 

* Running DKMS auto installation service for kernel-2.6.28-11-generic 
* nvidia(180.44)...

I have done a bit of research, searching etc but the only references I found relate to loading drivers using the hardware manager GUI, 

I can get to the single user(root) prompt and know that I am using an Intel Quad Core (Q6600 ?) chipset and an nVidia Geforce 7100/6310i graphics card.

I tried to install some utilities and was told by apt-get to issue:

dpkg --configure --a

It goes through a number of things and then comes up with the following:

Adding Module to DKMS build system
driver version = 180.44
doing initial module build

--
and then it hangs. 

Alol ideas gratefully accepted.

---

### Post by stlsaint on 2009-08-31
what are you upgrading from-to! and how long does it stay at the building stage...i mean have you given it ample time to go all the way thru? 
also see [here]("http://ubuntuforums.org/showthread.php?t=1036788") for possible help!

---

### Post by beach_defender on 2009-09-03
Hi, sorry I took a while to get back, I am getting over a small peice of spinal surgery.

I was upgrading from 8.10 to 9.0.4 using synaptic.

The build/reboot stops at the point that it tries to load the nvidia-180-kernel-source package.

OR, at reboot when DKMS tries to load it (nvidia-180.44).

I have managed to get a low res GUI up after booting into single mode and trying to manually load the drivers on one occasion.

IS there a method of loading the nvidia drivers from the command line, in single user mode?

I downloaded a driver package from nvidia but when I tried to run it, it got to 83% compiled and then stalled ( I left it for about 4 hours).

I do not want to have to re-install Ubuntu over on the existing disk in a new partition as the installer seems to think make sense.  I would like to be able to fix the current situation.

As I said, this happened because I took the advice from Synaptic to upgrade.

The most learning todate is to never do that again.  I think the upgrade options need much more work.

---

### Post by fateinabox on 2009-09-03
I had a similiar problem to yours in nature, do you by chance have an Intel onboard video ?? if so then you might find this thread interesting and helpful [http://ubuntuforums.org/showthread.php?t=1256691]("http://ubuntuforums.org/showthread.php?t=1256691")

---

### Post by beach_defender on 2009-09-06
Hi,
I tried that and initially I got a message saying that I should issue a 'dpkg --autoconfigure -a' but that hangs when trying to install the nvidia drivers.


I then removed all of the nvidia packages (apt-get remove nvidiaXXX).

I then re-issued the dpkg command and got no errors.

I then rebooted and got a low res screen, so at least I get to use the machine.

So then I thought 'Install the nvidia drivers through the hardware drivers system app' - this fails miserably telling me that there is a fatal error in the some background process and I should report the bug using bug jockey (or whatever its real name is).

I was selecting the recommended driver - 180.

I then tried to use the 173 driver but it just falls over.

This is an extremely frustrating thing.  Can we please ensure in future that the OS doesn't suggest an upgrade (I only did this because I figured it was safe as I the OS suggest the upgrade)?

This issue has caused me to lose the use of a workstation for over a month.

It seems I have to start from scratch again.

Can anyone suggest a PCI or PCI/Express (I have both) card that will work without proprietary drivers?

BTW, I started the hardware drivers app before starting this post and it is still looking for drivers.  This process is not good and anyway I can see.

Stay well
Barry

---

