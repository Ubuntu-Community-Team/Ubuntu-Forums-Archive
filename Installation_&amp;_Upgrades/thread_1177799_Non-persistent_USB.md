---
title: "Non-persistent USB"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by rannday on 2009-06-03
I have had this issue since day on with creating USB start-up drives.

I do not know what to do to make it persistent. I have re-formated and recreated dozens of pen-drives and also external HDDs, yet I have not been able to make it persistent (which I hope means that it saves all my settings/files/updates/applications). 

I recently created a 10 gigabyte partition on an external hard drive of mine and put Ubuntu on there. I allowed it to use all of the extra space to save settings/files/updates/applications. I tested it out, changed some preferences, updated, yet after a restart, all was lost.

I'm flabbergasted here. Please help. Thank you.

-rann

---

### Post by Mighty_Joe on 2009-06-04
So what *exactly *have you tried?  You haven't given us much information to diagnose your problem.
There are several options to set up a persistent USB drive:
The Ubuntu LiveCD has a USB Live CD Creator.  I haven't had much luck with it, probably due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544"), but if you stick with a 2Gb or smaller persistent partition, you should be fine.
[UNetBootin]("http://unetbootin.sourceforge.net/") is another option.  It will take the ISO of pretty much any distribution and make a persistent Live CD type install on a flash drive.
There are a couple ways to set up a persistent flash drive by hand at [pendrivelinux]("http://www.pendrivelinux.com/").
You can also just install Ubuntu directly to the drive.  I used the instructions [here]("http://beastie.cs.ua.edu/cs150/configuration.html") to configure Ubuntu so it (hopefully) doesn't wear out the flash drive.

---

