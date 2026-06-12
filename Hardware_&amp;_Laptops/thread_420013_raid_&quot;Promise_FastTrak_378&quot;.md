---
title: "raid: &quot;Promise FastTrak 378&quot;"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by matt91 on 2007-04-23
i am soon to be buying 2 400/500GB hard drives for my server which i want to use in a RAID1 array. i have never used raid before. my motherbourd booklet shows drivers installing for windows but nothing about linux. will my "Promise FastTrak 378" work in ubuntu server and do i need drivers?

thanks.

---

### Post by matt91 on 2007-04-23
my motherbourd manual says this is a "hybrid solution". am i right that this needs the software which isnt available?

will i need to use software backup? if so, which method is the best. i currently back up ubuntu(1GB without my data) by tar.gz. i think this is not a good option for larger ammounts of data.

are there any howtos on backup methods?

---

### Post by igloocentral on 2007-05-06
I would NOT recommend using the Promise FastTrak 378 controller that you have. DMRAID claims that it supports Promise FastTrak fakeRAIDs, but it definitely does not work on my Promise FastTrak S150 TX2+. Save yourself a big headache and buy a hardware RAID!

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/112402](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/112402)
[http://www.linuxquestions.org/linux/answers/Hardware/Promise_FastTrack_PDC20378_PATA_or_RAID](http://www.linuxquestions.org/linux/answers/Hardware/Promise_FastTrack_PDC20378_PATA_or_RAID)
[http://www.linuxforums.org/forum/debian-linux-help/12741-problem-installing-promise-fasttrak-s150-sx4-2-4-2-6-7-a.html](http://www.linuxforums.org/forum/debian-linux-help/12741-problem-installing-promise-fasttrak-s150-sx4-2-4-2-6-7-a.html)
[http://humandoing.net/past/2006/3/19/raid_on_linux_ubuntu_510/](http://humandoing.net/past/2006/3/19/raid_on_linux_ubuntu_510/)

---

