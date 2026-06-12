---
title: "Installing any OS other than Vista on HP DV6000"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by hellmet on 2007-10-25
My friend has a new DV6000 HP laptop. I tried installing Ubuntu. It installed, but then failed at GRUB installation. Tried twice with live cd, and once with Alternate. When I try to install XP , ( we hated Vista, so we wanted to install XP, and then remove Vista). the installer says there was no hard drive that it could detect at all.

Any clues whats happening here? He'd really appreciate any help.

---

### Post by humeston on 2007-10-27
That can happen if XP or Vista doesnt recognize the ext3 formatting created by ubuntu, download the gparted iso on another computer, and burn it.  then boot into it, and reformat it into NTFS.  I have the same computer, and the booting can be buggy, or stall if you do not hit F6 at the live CD start up screen, and type

> noapic nolapic

---

### Post by #Reistlehr- on 2007-10-27
Sounds like either the Vista discs are missing the whole SATA drivers, or write protection for the MBR is enabled in BIOS.

---

### Post by hellmet on 2007-10-27
The problem just isn't with the ubuntu drive. It just can't seem to recoginise the entire HDD. And,, ubuntu can't write to MBR, but Vista could. I'm guessing HP has designed some kind of a lock on the hard drive, but I never heard of such a thing before.

---

### Post by Cyber-J on 2007-10-27
> **hellmet said:**
> The problem just isn't with the ubuntu drive. It just can't seem to recoginise the entire HDD. And,, ubuntu can't write to MBR, but Vista could. I'm guessing HP has designed some kind of a lock on the hard drive, but I never heard of such a thing before.

I seriously DOUBT that. I've had XP and several Linux flavors along side the Vista Install on my DV6305. I've even had a larger hard drive in the notebook for a few months before I eventually moved the drive to an external case and reinstalled the factory drive. There is nothing that I've run into that would say that HP locks out certain operating systems from being installed on their hard drives. It sounds like to be the drive has become corrupted or could be dead itself. Does the drive show up at all in Ubuntu's partitioning software or any partitioner? Can you see the drive but not the partitions? If the drive shows up but the partitions don't, it could be something like a corrupt partition table. If the drive itself doesn't show up at all, it could be bad hard drive or something else. I'm not sure what you are meaning by "It just can't seem to recognize the entire HDD"?

---

### Post by renim on 2007-10-27
> **hellmet said:**
> The problem just isn't with the ubuntu drive. It just can't seem to recoginise the entire HDD. And,, ubuntu can't write to MBR, but Vista could. I'm guessing HP has designed some kind of a lock on the hard drive, but I never heard of such a thing before.

Is this the Intel or the AMD version?? If it is the Intel version then you are missing the SATA drivers. The AMD version even though uses a SATA HD doesn't seem to have this issue. The default XP disc doesn't recognise the SATA controllers or the drive and hence gives you no hdd found error. In order to install XP, you will have to either slipstream the Intel ICH7M or 8M chipset drivers whichever version the dv6000 uses on to your XP disc or disable native SATA support in the BIOS and then install XP or use an external floppy to load the drivers during XP installation.

As for as Grub issues - no idea!

---

### Post by hellmet on 2007-10-28
> **renim said:**
> Is this the Intel or the AMD version?? If it is the Intel version then you are missing the SATA drivers. The AMD version even though uses a SATA HD doesn't seem to have this issue. The default XP disc doesn't recognise the SATA controllers or the drive and hence gives you no hdd found error. In order to install XP, you will have to either slipstream the Intel ICH7M or 8M chipset drivers whichever version the dv6000 uses on to your XP disc or disable native SATA support in the BIOS and then install XP or use an external floppy to load the drivers during XP installation.

As for as Grub issues - no idea!
That fixed it mate. XP seems to be able to see the HDD now. But, installing grub always fails. It says Fatal Error, Grub couldn't be installed. When I try to manually grub-install, it cannot find a boot device or whatever. Ubuntu can see and install to the partitions though.

---

