---
title: "Ubuntu not detecting hardware RAID-0"
date: 2011-04-03
forum: Hardware
---

### Post by neelanshujain on 2011-04-03
Hi ,

I am trying to install Ubuntu on my computer having HDDs in RAID-0. But the Raid array is not being detected. All the drives are shown individually.

Current Configuration of my system is :

CPU : Intel Core i5-750
Motherboard : [P7P55D]("http://www.asus.com/product.aspx?P_ID=RBA8CzWoopUlYRFZ")
RAM : 4 GB
Graphics : ATI 5770
HDD : 500GB*3 in RAID-0 + 2.0 TB

I had setup the RAID from BIOS menu and then installed Windows-7 which automatically detected the RAID array. Now i am trying to install Ubuntu as the second operating system but it is not detecting RAID array! I am not an absolute beginner to ubuntu but still don't know a lot of terminal commands. I have been using Ubuntu for about an year and the previous installations were on the HDD in IDE mode or AHCI mode. 

Please tell me if there is a way to install it on the array setup by BIOS. The drivers disk of the motherboard have RAID drivers for RedHat and OpenSUSE. If there is a way to use those drivers please tell me how to use those drivers.

Thanks in advance.

---

### Post by ronparent on 2011-04-04
You don't say what release you are using. A common problem with both 10.04 and 10.10 is that they require installation of kpartx to a live session to see raid partitions. You can then continue a normal install from that same session.

---

### Post by neelanshujain on 2011-04-04
I am trying to install 10.10 32bit edition.

I have tried to boot from live cd, then in Terminal I wrote "sudo apt-get install kpartx". Then terminal installed it and then again I tried to install ubuntu, but still it is not recognizing the Raid partitions

---

### Post by wbloos on 2011-04-04
> **neelanshujain said:**
> 
I have tried to boot from live cd, then in Terminal I wrote "sudo apt-get install kpartx". Then terminal installed it and then again I tried to install ubuntu, but still it is not recognizing the Raid partitions

You didn't reboot before installing, did you?
I mean, did you install that package and then install ubuntu from that same live session?
Just to make sure..

---

### Post by neelanshujain on 2011-04-04
Ya , I didn't reboot. I tried to install from the same live session.
I told ya , I've been using it for an year so I am not a complete newbie.

---

### Post by ronparent on 2011-04-04
neelanshujain - From the live cd check by **'ls /dev/mapper'**. If /dev/mapper is essentially emmpty then test **'sudo dmraid -ay'**. This last command should reveal the raid partitions if they are to be found and populate /dev/mapper. Let us know what you find.

---

