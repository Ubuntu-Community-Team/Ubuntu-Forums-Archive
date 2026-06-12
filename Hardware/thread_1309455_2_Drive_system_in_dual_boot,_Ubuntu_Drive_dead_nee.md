---
title: "2 Drive system in dual boot, Ubuntu Drive dead need to replace"
date: 2009-11-01
forum: Hardware
---

### Post by wanderingarticfox on 2009-11-01
I thought I was having trouble upgrading my 9.04 to 9.10 but it was the death throws of an Ultra ATA 100 HDD that happens to have my 9.04 on it. The kernnel did upgrade but it has an imminate drive failure warning. I am back to using XP :(:(  I can access my 'boot from' selector in post which has an option to enter 'terminal'; and I am having to enter into the GRUB list to boot to Windows. I am ordering a replacement drive and need to know if I should enter something in the terminal access in the POST when I hook up the new drive  OR should I just boot with CD [yes I have ISO burned for 9.10] and will GRUB pick up and run with things and allow for a new set-up?  I know this is old tech but I am still saving for a new build and need to keep this one alive for another 5-6 months. Thanks for any help.:):):)

---

### Post by wanderingarticfox on 2009-11-02
I have an old 2001 Compaq that I popped in an old [read  recycled] 30GB Hdd into. I thought I was having trouble with the upgrade from 9.04 to 9.10 but it turns out the drive was dying. I now am awaiting a new Ultra ATA 100 drive but I am having trouble with GRUB when I pull the failed drive out. The origional [40GB] drive has XP Home on it and the dead one has my Ubuntu on it; however I do remember having to use 'Super Grub' back in the installation. I cannot remember which drive was not mouting.  Does anyone, please, have some tips on how I get around this error 25 from GRUB when trying to boot just the 40GB drive?? and with the bad one pulled? I've gone into BIOS and dropped the dead drive but it must have GRUB on one of it's chips because I cannot get to the GRUB Menu to boot windows with out the dead drive hooked up.  I know this is Ubuntu Forums but I also know that GRUB is the bootloader we all use in Ubuntu. I so desprately want to rid myself of Windows:(:confused:](*,)](*,)

---

### Post by cariboo on 2009-11-02
Use you XP install CD to fix the mbr on the drive. Boot from the XP install CD and select R for the recovery console. Once in the Recovery console run FIXMBR and FIXBOOT.

---

### Post by coffeecat on 2009-11-02
And if you don't have a Windows XP install disc (you won't if all you have is a manufacturer's recovery disc), then you can use your SuperGrubDisc to reinstall the Windows MBR. The menus on the SuperGrubDisc are not exactly a model of clarity, but there are two entries for Windows. One simply boots into Windows without repairing the mbr; the other repairs the MBR and then boots into Windows so that the next time you restart Windows you can boot up without using the SuperGrub disc.

In fact SuperGrub is better for repairing the mbr. It takes ages to get into the repair console with the XP disc. It takes seconds with SGD.

---

### Post by wanderingarticfox on 2009-11-03
First I want to thank cariboo907 and coffeecat for responding. I researched things some more and I used SGD to do the repair/remake of the boot strap/boot order. I am now booting to Windows XP in my primary HDD and the secondary HDD [failed drive] is physically removed. This solves the imediate issue I have confronted and prep's  me for the instal of the new HDD which I will use to reinstal Ubuntu 9.10 so I can proceed to rid myself of Microsoft.  Super GRUB Disc rock's and Ubuntu ROCKS SOLID so for those that have an older system pay heed; there is a solution and MS ain't it >>>Ubuntu ROCKS & 9.10 is a 'pretty' view; I can not wait toget beyound the desktop!!!!!!!!!!!):P):P

---

