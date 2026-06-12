---
title: "SATA hard drive not seen in GUI or Terminal"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by diodeman on 2009-06-07
I have just recently converted over from the "dark side" and have spent the past week reading up on everything that I possibly can. Through all my reading I have been unable to figure out how to get my second hard drive to show up. When I installed Kibuntu 9.04 it gave me the option on which attached one of the identical SATA drives attached I wanted to place the operating system. I chose one and installed without any issues figuring that the other SATA drive would be available once Kubuntu was up and running. Sadly to say, it was not and I have not been able to mount or even see it while in either the terminal or the GUI of Kubuntu. I know that the hard drive is still working because bios detects it every time that I turn the computer on. I have tried typing lshw, but that didn't really seem to help isolate my issue. Any thoughts would be greatly appreciated. Oh, not sure if it will make a difference, but it was formatted NTFS prior to Kubuntu install and was opering in a RAID 0 configuration with onboard Intel Matrix controller.

---

### Post by ddrichardson on 2009-06-07
It's not the drive it's the controller:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by diodeman on 2009-06-07
> **ddrichardson said:**
> It's not the drive it's the controller:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)


Do you have to do this in order to just see the second hard drive? I would like to not to have to use a RAID setup and would like to just have the drive for backup purposes. Sorry, still really new. Thanks for the help!

---

### Post by ddrichardson on 2009-06-07
I don't know much about it to be honest, just that there are a lot of articles on Matrix controllers being FakeRAID.

---

### Post by diodeman on 2009-06-08
hmm, still at a loss here. I checked out the link provided, but I'm just curious if the FakeRaid has to be set up even if I do not want to run a RAID setup for my computer. All I want to do is just have the second drive show in the operating system. Not sure if that is possible and it was only a windows thing, or what. Please help!

---

### Post by ddrichardson on 2009-06-09
Sorry I don't know anymore than that and suspect that Windows had dedicated drivers for the controller.

If there is no device being built in /dev/sd* then the controller is not being recognised. If you```
ls /dev/sd*
```and the device isn't there then there is a possibility that a kernel driver is needed for the controller that isn't in the stock kernel or modules but you'd need to do some Googling to find out more or even ask Intel - they're pretty helpful IMHO.

---

### Post by diodeman on 2009-06-12
Thank you for the help. I typed the command into the terminal and it I have 

sda, sda1,sda2,sda5,sdb,sdc, and sdc1. I'm currently running two DVD-R/W Drives, and two hard drives. It looks like it is seeing all of the ATA connections, but I can't seem to access the drives. Thanks again.

---

### Post by ronparent on 2009-06-12
If the drive was setup in windows it is a fakeraid and contains raid metadata on the drive. Even if you have disabled the raid in bios, ubuntu still sees the metadata and doesn't mount it as a normal sata drive. If you no longer want the raid drives in your system you have to disable raid in the raid bios (if you haven't already done so) and erase the metadata. To do that you have to first temporarily install dmraid - **sudo apt-get install dmraid -y** from a terminal. Then you run it to erase the metadata - **sudo dmraid -D**. If you want to rid yourself of dmraid then you - **sudo apt-get purge dmraid**. The drives hould then show up, probably as unpartitioned space on reboot. You will see them by running the partitoner (I'm in windows right now and can't recall the menu sequence for loading gparted in GUI).

---

### Post by diodeman on 2009-06-12
since one of the hard drives from the previous RAID is what I'm running Kubuntu under right now, dmraid should not see that drive as a raid drive and therefore not erase any information it it, correct? Thank you for the help! I'm going to give it a try here soon.

---

### Post by skipit721 on 2009-06-21
ok here i sit looking for a similar answer ,, i just added a new  partition to my menageri,and first loaded vector  ,then replaced it with 9.04 ,, why well vector couldn't access any other drives or partitions outside of root  now i have the same issue with 9.04  i still am running 8.10 no issues ever or with any other distro including puppy ,, i am sorly missing 1.3 terabytes of space this way, but i am jumping in to say no it isn't a raid issue no it isn't a drive isue it is a permision isue changed in the new kernel across multiple platforms .. hardy and intrepid  do not have this issue neither did vector 5.9 new problem to 6.0  and ubuntu 9.04

---

### Post by skipit721 on 2009-06-21
ok if this is the same isue i had it is an easy fix  in xubuntu 9.04  and in gui no less.
click on aplications, go to system  authorizations go down the list to hal and give yourself access reboot and you are there worked for me ,, although i don't know why they changed permisions for hal  in the update ,,

---

### Post by lindsay7 on 2009-06-21
Try opening Gparted and see if that sees the drive.  I just put in a brand new sata hard drive and windows would not see it at all and could not install it or do anything with it. I booted Ubuntu and I still could not see until I looked at it with Gparted. I formated the drive as fat32 just to get it going and then booted back to windows and It was recognized. I was going to restore this drive with Acronis (which was installed on the windows drive to the new drive).

---

### Post by diodeman on 2009-06-22
Thanks guys for all of the advice on trying to get the hard drive up and running. I haven't had a chance to try any of those suggestions yet because school has been extremely busy. As soon as I get a chance, I will post the results to update. Thanks again for the help!

---

