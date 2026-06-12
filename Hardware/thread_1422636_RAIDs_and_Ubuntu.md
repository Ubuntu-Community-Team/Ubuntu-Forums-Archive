---
title: "RAIDs and Ubuntu"
date: 2010-03-05
forum: Hardware
---

### Post by Twinflower on 2010-03-05
I recently tried converting to Linux, and installed Ubuntu 9.10 a few hours ago.
Everything looks fine and promising except two issues:
 

a) I have a hardware-raid (aka "FakeRAID/DriverRAID") consisting of 2x500GB SATA-disks, but they are not recognized by ubuntu.
They are connected to a gigabyte raid controller which I think is a Silicon Image-chip. The motherboard is a Gigabyte P35-DQ6
When i visited my gigabyte's website, they had no drivers for linux, only refering to third party vendors.


b) I also have a windows software raid consisting of 2x1000GB SATA-disks which is not recognized.
This raid was made in Windows 7 in the disk manager-tool.
(Those are connected to a intel-controller which is raid-disabled because of driver issues with windows (blue screen).


As I was uncertain about the software-raid would work in Ubuntu, I really expected the HW-raid to work right out of the box as I' under the impression that Ubuntu tries to get users over from Windows.
 

Ubuntu (and windows 7) is installed on a fifth disk, a 160gb "standalone".
 


Please advice



below is a screenshot from the ubuntu disk tool;
[IMG]http://s2.postimage.org/pGcD9-f3ced4cc43fd3b3fcc6136098dbdcdc0.png[/IMG]

---

### Post by solar george on 2010-03-06
There is some information here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

But it really seems that the only reason to use fake raid is because you need both win and linux to be able to access the array, otherwise stick with a pure software raid.

---

### Post by Twinflower on 2010-03-08
thanks for your reply solar george.
I've read through the wiki you linked to, but it all seems pretty confusing to a first timer.

Is it really that complicated to get ubuntu to see my fake/software-raids as one disk?

Remember, i dont have to install to a raid as I have a standalone disk with both windows and ubuntu on it

---

### Post by solar george on 2010-03-08
Do you *really* need to use the fake raid system rather than the linux sw raid?

---

