---
title: "Samsung 2TB hd204ui align sectors"
date: 2011-01-02
forum: Hardware
---

### Post by blazyyo on 2011-01-02
I am trying to align the sectors of my new advanced format drive (Samsung 2TB hd204ui). I am running a dual-boot Ubuntu 10.04 and Win XP both on an older hard drive. I have already upgraded the firmware using the patch from Samsung's website. There are no jumpers in the back of the drive.

I ran gparted and created an NTFS partition, with 1mb preceding (have also tried different values), and the remaining space as the NTFS partition. I unchecked the box for "round to cylinders" (although I also tried it with the box checked).

After formatting, in gparted the information screen says the first sector is 2048, which sounds right. But if I open a terminal and type "sudo fdisk -l" it says that it starts at 1. Is this inconsistent, or is it reading something different?

I tried the Acronis align tool in Win XP, but it reports that my drive is not an Advanced Format Drive, and I don't understand why.

Do I need to repartition differently? Thanks for your help.


Edit: By the way, in my bios the drive setting is at IDE instead of AHCI because that was the only way I could boot into Win XP. I have read about fixes and driver installs to correct this, but would rather leave it as it is if it doesn't affect much. This might be why Acronis thinks it is not an Advanced Format Drive?

---

### Post by cascade9 on 2011-01-03
> **blazyyo said:**
> Edit: By the way, in my bios the drive setting is at IDE instead of AHCI because that was the only way I could boot into Win XP. I have read about fixes and driver installs to correct this, but would rather leave it as it is if it doesn't affect much. This might be why Acronis thinks it is not an Advanced Format Drive?

Could well be. BTW, IDE mode does have a performance hit. 

You could always just change to AHCI in BIOS, setup the drive, then change back to IDE mode.

---

### Post by blazyyo on 2011-01-04
> **cascade9 said:**
> 
You could always just change to AHCI in BIOS, setup the drive, then change back to IDE mode.

Changed to AHCI mode, booted Ubuntu, formatted in gparted, and have the same results. I cannot boot to Windows in AHCI mode unless I install drivers, and I rarely use the Win partition so I would rather not spend time setting it up for Windows.

Is my hard drive aligned properly, or is there a better method I can use in Ubuntu? I'm not sure why fdisk says it starts at 1. Please help a newbie. Thanks.

---

### Post by cascade9 on 2011-01-05
WD has an alignment tool that is on a bootable CD. I dont know if Samsung does the same, but if they do that should solve it. (you could boot in AHCI mode to check the alignment)

You might be able to use the WD tool if Samsung doesnt have one.

---

### Post by blazyyo on 2011-01-07
I didn't repartition again. I ran "fdisk -lu" and it shows it starts at 2048. So I guess gparted did it right the first time. User error, sorry and thanks.

---

