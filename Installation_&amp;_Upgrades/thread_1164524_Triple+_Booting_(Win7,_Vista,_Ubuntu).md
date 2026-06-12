---
title: "Triple+ Booting (Win7, Vista, Ubuntu)"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by fredyboy10 on 2009-05-19
I have installed three OSes Win Vista, Win 7 (RC 7100), and Ubuntu 9.04. I am using the GRUB bootloader instead of the Microsoft bootmgr. After installing all three OSes and restoring GRUB I noticed there was only one Windows option, choosing this option leads to the Windows bootmgr and gives me a choice between Win7 and Vista. I don't want to make two choices when starting, Also I am using the savedfault option in GRUB but that doesn't let me differentiate between Win 7 and Vista.

I then modified menu.lst to add the Win7 partition. This doesn't work out of the box becuase bootmgr is on the Vista partition. Copying the boot folder and bootmgr restores the ability to boot from the Win7 partition from GRUB. Now when I pick Win7 from GRUB I get win7 (set as default). I pick Vista from GRUB I get the choice between Win7 and Vista (win7 default). Using bcdedit in Vista I am able to make Vista the default and set timeout from 30 to 3. Restarting to Win7 and trying to do the same thing but with Win7 defualt I notice that bcdedit reports the same as it did in Vista (Vista now default with 3s timeout), but when I booted from the Win7 partition in GRUB and bootmgr had Win7 as default with 30s timeout. 

This is most likely an issue with the Windows BCD, but I think you people (yes you) will have more experince with multi-booting. Since the bootmgr is not quite correct the hibernation file always fails when choosing Win7 from GRUB, but choosing Vista from GRUB then Win7 from bootmgr will resume the hibernation file correctly.

Any ideas? I most likely need to correct where bootmgr thinks the BCD file lives.

Thanks

---

### Post by mmesantos1 on 2009-05-19
> **fredyboy10 said:**
> I have installed three OSes Win Vista, Win 7 (RC 7100), and Ubuntu 9.04. I am using the GRUB bootloader instead of the Microsoft bootmgr. After installing all three OSes and restoring GRUB I noticed there was only one Windows option, choosing this option leads to the Windows bootmgr and gives me a choice between Win7 and Vista. I don't want to make two choices when starting, Also I am using the savedfault option in GRUB but that doesn't let me differentiate between Win 7 and Vista.

I then modified menu.lst to add the Win7 partition. This doesn't work out of the box becuase bootmgr is on the Vista partition. Copying the boot folder and bootmgr restores the ability to boot from the Win7 partition from GRUB. Now when I pick Win7 from GRUB I get win7 (set as default). I pick Vista from GRUB I get the choice between Win7 and Vista (win7 default). Using bcdedit in Vista I am able to make Vista the default and set timeout from 30 to 3. Restarting to Win7 and trying to do the same thing but with Win7 defualt I notice that bcdedit reports the same as it did in Vista (Vista now default with 3s timeout), but when I booted from the Win7 partition in GRUB and bootmgr had Win7 as default with 30s timeout. 

This is most likely an issue with the Windows BCD, but I think you people (yes you) will have more experince with multi-booting. Since the bootmgr is not quite correct the hibernation file always fails when choosing Win7 from GRUB, but choosing Vista from GRUB then Win7 from bootmgr will resume the hibernation file correctly.

Any ideas? I most likely need to correct where bootmgr thinks the BCD file lives.

Thanks

Hey There, 
I set up the same triple boot. You have to edit your original bootloader for Vista since it will still have Vista and Win 7. This is assuming Vista was the first OS installed on your HDD. Ubuntu still marks Win 7 as Vista even if it is the only Win OS on your HDD. Your only issue is Vista and Win 7 use the same location for boot. No way around this issue.

---

### Post by Mark Phelps on 2009-05-20
Ran into a similar problem.  Discovered that the two OSs (Vista and Seven) are both using the SAME BCD; thus, whenever I change it through BCDEdit or EasyBCD in one OS, when I boot to the other OS, the same changes are there.

Since I need both for the time being, don't really want to go hacking around inside the BCD and break something.

If you figure out a way to change one BCD but not the other, please let us know.

---

### Post by krang on 2009-05-20
> **Mark Phelps said:**
> 
If you figure out a way to change one BCD but not the other, please let us know.

Yes, please.

I am at the same problem. I have Win 7 and Vista on an external drive (eSATA) and the laptop main OS (came with the laptop) in normal drive. I want to replace the Vista on integrated drive with Ubuntu since I'm using linux mostly for my work.

Since you reportet these problems, I assume there is no chance for me yet. :(

---

### Post by fredyboy10 on 2009-05-20
I copied the BCD files to the Win7 partition and get the 30 sec timeout with win7 as default from bootmgr, but this must be different than the BCD because once Win7 starts bcdedit displays the Vista BCD as others have confirmed.  
I will try to export the Vista BCD and see if I can somehow convince Win7 to use its own BCD file.

---

### Post by fredyboy10 on 2009-05-20
Editing the new Win7 BCD was easier than I thought. Using bcdedit just add the flag "/store C:\Boot\BCD"
 For example
```
bcdedit /store C:\Boot\BCD /set timeout 10
```
This will change the entries in C:\Boot\BCD instead of the System BCD. THis is great I can control which is defualt and timeout and such.

Now the problem, Windows 7 still think the Vista BCD file is the one being used,  this is just annoying for editing the file but survivable. The problem comes up when hibernating. During the resume process the BCD has to understand there is a resume file and deal with it accordingly. The new Win7 BCD does not resume the file, it instead deletes in and boots normally. If I restart with the Vista BCD instead the hibernate resume for Win7 works. I am assuming this has to do with Windows writing something to the bcd or in hiberfile.sys and it still thinks it is using the Vista BCD.

Anyone have any ideas?

---

