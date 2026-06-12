---
title: "problems with motherboard/hard drive(s)"
date: 2009-07-10
forum: Hardware
---

### Post by ffxigotenks on 2009-07-10
I've been using linux for almost a year and a half and ubuntu since about november, I recently formatted and reinstalled 8.10 again and over the last couple of days my computer will run fine for a couple hours, maybe more, then the root partition becomes read only and the entire thing locks up so hard the only thing that allows me to reboot past the motherboards drive detection during the POST is to unplug and replug the power supply, only to have it happen again.. I have a SATA hard drive which may be partially to blame, it has failed S.M.A.R.T. tests due to bad sectors, but I'm having trouble belieiving this since it just happened to occur during a failed install of 9.04. it freezes a fsck every time it reaches 1846/22xx during a forced system check and when I run 8.10 off a USB stick to run a manual "fsck -yc /dev/sda3" it starts out fine, then after about two or three hours it starts to cycle between freeze the system temporarially, then resume normally for a minute or two, after leaving it alone for 10 hours and having it complete the check and start writing the bad sector list, it freezes and doesn't recover... I know this is a long post and would appreciate any help I can get

---

### Post by amadeus266 on 2009-07-10
It may very well be that you have a bad disk but it didn't show up until the failed installation (may have been the cause of it in fact). I would recommend a new hard drive.

---

### Post by ffxigotenks on 2009-07-10
thanks for the quick reply, I forgot to add that I have a PATA drive that I decided to try and use instead and kept it attached when I switched back to the SATA. the drive just vanished both when it was running ubuntu and when it was a secondary data drive and the only thing that would bring it back was a power cycling. yet my /home drive has never had a problem throughout this ordeal

---

### Post by ffxigotenks on 2009-07-13
ok, new symptom... I came back to my computer frozen and power cycled the tower, and all I get on the POST is the name of the motherboard and the CPU info, it freezes before the RAM test and nothing allows it to pass it until I unplugged it overnight and powered it up again... I'm now stuck between the RAM and the motherboard being a cause of it.

---

### Post by doas777 on 2009-07-13
If it won't get through the ram check, I'd try replacing the RAM first (since it's the cheaper component) or if you have another PC that will seat the ram, test it there.

---

### Post by ffxigotenks on 2009-07-13
> **doas777 said:**
> If it won't get through the ram check, I'd try replacing the RAM first (since it's the cheaper component) or if you have another PC that will seat the ram, test it there.

ok, would failed RAM eventually work after a night of not receiving power? I have 2 1GB sticks in there and am having a hard time believing that both would fail, but I'm not sure that if one were failing that it would just freeze the system

---

### Post by doas777 on 2009-07-13
> **ffxigotenks said:**
> ok, would failed RAM eventually work after a night of not receiving power? I have 2 1GB sticks in there and am having a hard time believing that both would fail, but I'm not sure that if one were failing that it would just freeze the system

no, not unless a reboot would work equally well. 

does your BIOS see all the ram? i had symptoms like that on a laptop, after upgrading the ram. HP gave me so little control in the BIOS that I had to get a winflash from support to tell it that it should have 2GB.

yes a bad block on a single stick of ram could lead to freezes and crashes.

I'm leaning toward a bad mobo personally, but checking the ram first is a logical troubleshooting step, as it is cheaper and less of a pain.

---

### Post by ffxigotenks on 2009-07-13
> **doas777 said:**
> no, not unless a reboot would work equally well. 

does your BIOS see all the ram? i had symptoms like that on a laptop, after upgrading the ram. HP gave me so little control in the BIOS that I had to get a winflash from support to tell it that it should have 2GB.

yes a bad block on a single stick of ram could lead to freezes and crashes.

I'm leaning toward a bad mobo personally, but checking the ram first is a logical troubleshooting step, as it is cheaper and less of a pain.

when it finally started up this morning it told me "2048MB OK" which is correct, I think I'm gonna try putting my RAM into a friend's system and see if that works, and if it does, then I'll replace the mobo

---

