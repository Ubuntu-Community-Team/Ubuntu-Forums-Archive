---
title: "AMD 780G onboard Raid Support"
date: 2009-09-04
forum: Hardware
---

### Post by jznomoney on 2009-09-04
Does anyone know if there will ever be support for amd motherboard raid.  I have a board based on the 780g chipset with a sb700 chip.  I have raid0 enabled with the bios.  I cant seem to get ubuntu to find my raid set with dmraid.  Has anyone got this to work.  I have windows installed on my raid set.

---

### Post by jznomoney on 2009-09-05
no one has any idea?

---

### Post by ronparent on 2009-09-07
Yes, the support is with a program called dmraid. Do not try to partition of install ubuntu to a raid drive without using dmraid! To do so would wreck all data on the raid0 especially. See this site if your intent is to install ubuntu to a raid0 array: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

As you can guess the community refers to your motherboard raid as a 'fakeraid'. Be sure to study the install carefully because the whole enterprise has a lot of peril. Post here if you need more info.

---

### Post by AWeapons on 2011-09-15
J-Mizz..(laughing)..this forum is OLD as hell..but if this CAN help out..(or if you're still living)..LOL..i'll be glad to help..now!!?? 1) most of the Gateway AMD bioses are locked..so you'll have to unlock it so you can go to raid..(i have the Gateway GM5688E..so i d/l'd a slic'd bios version 7B3G1P04 & my raid is working..ok..here we go..1) this is for raid with a Windows Vista diskl..1st..before you do anything..d/l the most recent RAID drivers from AMD & save them either on 1) a USB thumb driver..(it does NOT have to be bootable)..2) a CD..or 3) a floppy drive..(again..neither of these have to be bootable)..ok..reboot your PC after you've d/l'd your raid drivers & hit F2 for your BIOS..go to Advanced Configurations..& choose RAID..press F10 & shut down PC..now install your HDD's..(remember..your HDD's HAVE to be IDENTICAL IN EVERY WAY..model no#, size, brand, etc)..put the HDD's on the 2 bottom slots on the left side..(that's master & slave)..turn on your PC..and you'll soon see the RAID option..press Ctrl+F when it give you the option to do so..once in the blue screen..select 2 for defining your array..select raid 0 (or whichever your choose)..select 64k..(it's better with data..128k is better if you're using your PC for video)..leave Gigabyte boundary on..& leave fast build on..assign both drivers..hit Ctrl+Y twice..& then hit escape twice..then press Y to reboot..now put in your Vista disk..hit the space bar to boot from cd/dvd..let the Vista prompt come up..and choose INSTALL NOW..once there..load your raid drivers you'd d/l'd earlier..you'll then see your HDD's..it'll show up as one big driver..(almost twice the size of one of the drivers)..from there..install your Vista on the raid..you're done..now the 2nd option..(which was MY option)..LOL..i wanted to use the actual Gateway Restore disk..(sighing)..so here we go..LOL..ok..you'll need 2 other things..1) an extra HDD..& 2) any cloning software..(i used HD Clone 4..it's free)..LOL..1st..put in your master HDD on the top left port..(this will be your master drive & the drive in which you're going put in Windows..then put in your other 2 HDD's..set the 2 identical drives on the bottom 2 ports on your left side..(my mobo has 6 ports..so this is how i set it up)..ok..turn on your PC..& hit F2 to go into your BIOS..once there..go to advanced configurations..& in sata mode..select AHCI..(AMD's earlier drivers are the same with AHCI & RAID)..F10 to reboot..put in your Factory restore disk..(or hit F8 the go to your recovery partition)..install windows..from there..you're going to install the most recent RAID drivers in Device Manager..(these are the drivers you d/l'd in the beginning)..reboot..then go into your bios & switch sata mode to RAID..shut down..take out your PM (primary master) drive..turn back on your PC..hit Ctrl+F on raid option prompt..select option 2..go the your raid array setup..raid 0 (or whichever)..gigabyte boundary on..fastbuild on..& 64k..(or whichever)..assign your HDD's..CTRL+Y twice..escape twice..& Y..shut down..put back in your PM drive in the top left slot..turn PC back on..go into Windows..& then go into computer disk management..you'll see that your raid array is unallocated & uninitialized..(your raid array will be one big HDD)..so initialize it..label it..& format it..then you're going to clone the drive..from the OS drive..(that'll be the smaller driver)..to the raid drive..(that'll be the bigger drive)..after that..shut down PC..remove the top left drive..(the OS drive)..then start your PC..& you'll go right into Windows..(smile)..you'll be in raid..& you're done..(laughing)..i'm actually writing you from this same PC..do NOT buy Acronis & all of these other programs that are CLEARLY a waste of money & time..(i've dumped over 300 dollars in this PC because i wanted to raid using the Gateway Restore Disks)..so no hacks are needed..just follow this..& you'll be good..Peace..& God bless..

---

