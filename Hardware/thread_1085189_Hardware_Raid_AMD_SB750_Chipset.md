---
title: "Hardware Raid AMD SB750 Chipset"
date: 2009-03-02
forum: Hardware
---

### Post by SBFree on 2009-03-02
Hi:
I'm making a new build and would like to use Hardware RAID. The MB has an AMD SB750 chipset and comes with a chipset driver file called:
ati-driver-installer-8-7-x86.x86-64.run . when I boot the live CD it sees the 2 drives in the Raid array as seperate drive. Before I do the install and make some destructive move to the other installs on the drives I had the following questions:
Does it seem expected that the Live CD (8.04 64 bit) will not see the Hardware raid array as one drive?
How would I go about using the driver install file?
Thanks,
Scott

---

### Post by hotweiss on 2009-03-02
> **SBFree said:**
> Hi:
I'm making a new build and would like to use Hardware RAID. The MB has an AMD SB750 chipset and comes with a chipset driver file called:
ati-driver-installer-8-7-x86.x86-64.run . when I boot the live CD it sees the 2 drives in the Raid array as seperate drive. Before I do the install and make some destructive move to the other installs on the drives I had the following questions:
Does it seem expected that the Live CD (8.04 64 bit) will not see the Hardware raid array as one drive?
How would I go about using the driver install file?
Thanks,
Scott

You have to use the alternate CD to get RAID support. One of the first options that you will have with the alternate CD is RAID support.

---

### Post by SBFree on 2009-03-03
Thanks.
The link for the alternate 8.04 version:
[http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-alternate-amd64.iso]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-alternate-amd64.iso")
is disconnected.
Do you think 7.10 is the latest version for the alternate CD?
Thanks again,
Scott

---

### Post by SBFree on 2009-03-03
Thanks.

---

### Post by hotweiss on 2009-03-03
You can download the Ubuntu 8.10 alternate CD here:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by SBFree on 2009-03-04
Thanks for directing me to the right download area. The file I have from the Motherboard manufacturer is called: ati-driver-installer-8-7-x86.x86_64.run . Do you know if using the Alternate CD will just ask for such a file or should I anticipate having to do something else with it first?
Thanks,
Scott

---

### Post by hotweiss on 2009-03-04
> **SBFree said:**
> Thanks for directing me to the right download area. The file I have from the Motherboard manufacturer is called: ati-driver-installer-8-7-x86.x86_64.run . Do you know if using the Alternate CD will just ask for such a file or should I anticipate having to do something else with it first?
Thanks,
Scott

That file looks like a video card driver for the 64 bit version of Ubuntu. I would first use the alternate CD to install Ubuntu and then I would work from there. When you first boot up the alternate CD you will be given a few options at the beginning including the option to turn on SATA RAID. Once you have installed Ubuntu, click on the restricted driver icon and install your ATI video card driver. If you have any more problems, message back here.

---

### Post by SBFree on 2009-03-05
Thanks for the heads up on what to look for. I can't get to this install for a few days but appreciate knowing what to expect.
Scott

---

