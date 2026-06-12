---
title: "Raid Help"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by pacco on 2009-08-29
ok i have an hp ellite m9500f, and the bios is set to ahci instead of raid because i switched it in the bios
i download ubuntu 64 bit altranat cd and want to setup my raid hard drive,i also have a 500gb media drive as well that i would like to use with my 750GB hard drive,now when it detects hard disks it says SERIAL ATA RAID detected would you want to activate these devices and i select yes,but it only sees my 500gb media drive.

I tried to enable "dmraid true" on the boot paramaters,but nothing seems to work.

Any help would be appericiated

:)

---

### Post by ronparent on 2009-08-31
I am unclear on what you want to do. If you want to clear the raid completly, you will have to use dmraid to erase the raid meta data on the 500Gb drive (ie **sudo dmraid -**E). Once this is done it is a normal SATA and dmraid is no longer needed. If you want to retain the existing raid and all of its data, that is another story.

---

### Post by pacco on 2009-08-31
sorry i should have been more specific,i want to use both hard drives as one big hard drive.

How would i do this?
Excuse my manners,thank you for the quick reply

---

### Post by ronparent on 2009-08-31
Depending on how your MB is equipped, that can be accomplished with a spanning raid or posibly with a stripped raid if your MB raid bios permits either. I presume based on your desire for one big hard drive that you don't intend to dual boot with windows. That would also leave you the option of implementing your intents with a software raid. In either event you need to purge the fake raid meta data on the 500Gb drive to insure that it doesn't interfere with what you want. That would, of course, wipe the drive of all readable data. To do that you need to use dmraid on the alternate cd to discover and purge the meta data on the 500Gb drive, preferably without the 750Gb drive installed and with bios configured for normal SATA without raid. The command given above (ie **sudo dmraid -E**) would erase the meta data. 

The next step depends on whether you want a software raid or fakeraid (so called despite the fact that it uses the MB bios to define the raid set). For the software raid see: **[http://ubuntuforums.org/](http://ubuntuforums.org/)**

For fakeraid see: **[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)**

Keep in mind that setting up a raid on a non-symetrical (not equal) set of drives will be challenging even for an experienced ubuntu user and require you to learn things very few user know anything about or can help you with. I myself have not attempted anything quite this ambitious. It is doable if you follow the guides (and quite a learning experience). Post here if you need more help, but, don't expect step-by-step instructions other than the references I gave you. Good luck and have fun.

---

### Post by pacco on 2009-09-01
thank you for the reply, i gave up on the raid and went with encrypted lvm, now im using the 500GB drive for /srv mount point.

I'm trying to setup my server,i'm pretty good with the lvm setups.

Thanks For The Help

---

