---
title: "Fails to install &quot;file did not match its source copy&quot;"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by zenlunatics on 2009-08-18
When installing ubuntu or xubuntu, I get the message:

The following file did not match its source copy on the CD/DVD:

/target/lib/modules/2.6.28-11-generic/kernel/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.ko

This error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

I'm given the options to abort skip or retry, if I skip I get the same error message with a different file. 

I don't think its the cd, I've used several differant live cd's many of which I have used to install ubuntu on other computers. I'm going to wait till its cooler where I live ( the temp. of the computer room is probably 90 degrees farenheit or higher, also very humid) and try to do a usb install, if that doesn't work I'm assuming its something with the hard drive which I can't fix. 

Any advice? ( I kind of already deleted windows, and I was installing it on a relatives computer so I kinda really need to fix it)

---

### Post by presence1960 on 2009-08-18
kind of already deleted windows? that is like a woman saying she is kind of pregnant. Either you actually removed windows or you didn't.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you made the CD from?

Did you burn the iso as an image at no more than 4x speed? If you don't have a program which allows you to choose burn speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html").

Did you try "check disk for defects" option when booting the live CD?

---

### Post by zenlunatics on 2009-08-18
I did the md5sum. I thought the fact that I've used this cd before effectively, rules out that its a problem with the cd. Plus I get the same problem with both xubuntu and ubuntu. Am I wrong?

---

### Post by presence1960 on 2009-08-18
> **zenlunatics said:**
> I did the md5sum. I thought the fact that I've used this cd before effectively, rules out that its a problem with the cd. Plus I get the same problem with both xubuntu and ubuntu. Am I wrong?

Is the CD scratched or dirty. Try burning a new one or making a bootable USB if your machine will not read the cd thru the install process, that is if your rig can boot from USB. 

You may also want to look at your optical drive. try cleaning it as suggested in the error.

---

### Post by lisati on 2009-08-18
> **zenlunatics said:**
> I thought the fact that I've used this cd before effectively, rules out that its a problem with the cd. P

edit (misread post): not all CD drives are created equal. A CD which works on one machine sometimes doesn't work on other machines.

---

### Post by presence1960 on 2009-08-18
> **lisati said:**
> edit (misread post): not all CD drives are created equal. A CD which works on one machine sometimes doesn't work on other machines.

+1

reading a data CD and booting a bootable CD are not the same animal. it just may be the drive. You may read data CDs fine but have problems with a bootable CD. If all else fails try a bootable USB provided the machine can boot from USB. Use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB.

---

### Post by zenlunatics on 2009-08-19
So I just tried a usb boot, I used netbootin, And configured the BIOS settings to boot from usb, and all I get is a blank black screen with one small blinking line in the top left hand corner.

Does this mean there is something wrong with the hard  drive?

---

### Post by zenlunatics on 2009-08-19
....oops. I wasn't using the "live" version of the iso. I will repeate the usb boot with a live iso.

---

### Post by zenlunatics on 2009-08-19
Same results with the live iso.

---

