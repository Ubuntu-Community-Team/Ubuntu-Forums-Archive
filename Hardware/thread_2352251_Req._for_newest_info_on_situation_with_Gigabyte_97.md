---
title: "Req. for newest info on situation with Gigabyte 970 model boards"
date: 2017-02-10
forum: Hardware
---

### Post by nannerpuss on 2017-02-10
I am one of the unfortunate Gigabyte 970 chipset motherboard owners who have to settle for having no USB 3.0 BUT get onboard networking, OR get USB 3.0 and lose the onboard NIC. There was a janky workaround that I still use, whereby you enable IOMMU and get to keep most features of your mainboard, but lose the ability to have USB 3.0 ports function at full speed and sometimes your USB 2.0 ports on the back decide to stop working. Then a very helpful Ubuntu user came up with a solution involving entering UEFI, plugging in keyboard and mouse and flash drive, booting and editing grub to use the "iommu=soft" flag at run time, then rebooting to disable IOMMU and retain all functionality. It's worth noting that this is/was specifically related to Ubuntu and 64bit distros, but I believe other flavors (Xubuntu for sure) had it. The most recent update or post I can find on this issue is from about one year ago, so I'm curious if:

A) Was there a automagical fix put out (kernel update, firmware, etc) that fixed this problem permanently and I just missed it? Gigabyte's site, especially for main boards, is Windows-centric and beyond sparse one-line notes on firmware updates I can find no mention of this bug being killed. I love Gigabyte but as a permanent linux person now, this is my last board from them or anyone else who doesn't specially state support for linux. 

B) Is anyone else still receiving the AMD-Vi freakout spam during boot, despite applying this "iommu=soft" workaround or another? 

C) If the original user with the fix happens to read this, just know you made the world a better place by doing Gigabyte's job for them and it was appreciated. (ozcyto was the name I believe, but don't wanna get in trouble for using someone's name in a thread)

---

### Post by Yellow Pasque on 2017-02-11
I'm not normally one to throw money at problems, but wouldn't it be easier to get a cheap PCI-e network adapter card?

---

