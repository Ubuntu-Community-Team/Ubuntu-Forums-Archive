---
title: "Broke my computer trying to overwrite Windows"
date: 2020-02-15
forum: Hardware
---

### Post by sevensixtwo on 2020-02-15
Hi. I made a thumb drive of Ubuntu 18 and tried to install it on my computer.  When prompted, I said to go ahead and overwrite windows instead of first making a separate partition for dual boot.  The installation failed.  After that, my computer didn't work at all.  I tried to do the windows factory reset holding alt+f10 on startup, but that failed.  Now I can use the thumb drive to "try Ubuntu" and that is how I am making this post.  When I try to install Ubuntu from the Ubuntu trial OS, it only sees the USB drive and not my HDD.  Even in gparted, Ubuntu cannot see my HDD, I think because it is not formatted for linux.  

However, I messed up my bios in the course of all of this.  I can boot from the Ubuntu USB for some reason, but in the BIOS it does not have an option to boot from USB.  I have a DBAN USB (program that wipes drives) that I want to use to wipe my drive to see if that will make it show up in gparted, but I can only boot from this Ubuntu USB for some reason, and none of my other bootable USB sticks work.  It was something about trying to overwrite windows from this Ubuntu USB that makes my computer see this USB as a boot option, but none of my other bootable USBs work.

This is what I'd like to do: turn off secure boot in my BIOS, or else turn off UEFI and turn on legacy mode instead, and then I will be able to boot into DBAN and wipe the HDD to get rid of the windows formatting.  However, when I used the Ubuntu USB to overwrite windows, it messed up the BIOS and I absolutely cannot turn off secure boot, and it it won't let me boot from USB in secure boot mode (except this Ubuntu USB for some reason.)

This would also work: if there is some way that I can make gparted see the drive when I'm "tying Ubuntu" from the USB, then that should work too.  Is there some way I can make it see the drive?  Thanks!

**_SUMMARY:_**
Tried to overwrite windows from Ubuntu USB.  Installation failed. 
Fried my BIOS, can't disable secure boot so I can't boot from any USB besides the Ubuntu USB.
gparted doesn't see my HDD
can't boot from other USB with drive formatting tool.
I want to install Ubuntu, but it fails because it can't detect my HDD, and the fried BIOS is making hard for me to format the HDD for linux.

---

### Post by yancek on 2020-02-15
The most common reason for a Linux installer not seeing windows partitions on windows 8/10 is because if was left in a hibernated state (default on windows).  No Linux OS will mount a hibernated system due to the likelihood of damaging the system.  Don't know how you can turn that off if you can't boot windows, maybe from the BIOS firmware?  What exactly failed in your attempt to install Ubuntu?  Did you get any error messages?

You haven't indicated the manufacturer of the computer.  If you do that, someone here familiar with it may have a suggestion on how you can deal with the problem accessing the BIOS.

---

### Post by bcschmerker on 2020-02-15
> **sevensixtwo said:**
> Hi. I made a thumb drive of Ubuntu 18 and tried to install it on my computer.  When prompted, I said to go ahead and overwrite windows instead of first making a separate partition for dual boot.  The installation failed.  After that, my computer didn't work at all.  I tried to do the windows factory reset holding alt+f10 on startup, but that failed.  Now I can use the thumb drive to "try Ubuntu" and that is how I am making this post.  When I try to install Ubuntu from the Ubuntu trial OS, it only sees the USB drive and not my HDD.  Even in gparted, Ubuntu cannot see my HDD, I think because it is not formatted for linux.  

However, I messed up my bios in the course of all of this.  I can boot from the Ubuntu USB for some reason, but in the BIOS it does not have an option to boot from USB.  I have a DBAN USB (program that wipes drives) that I want to use to wipe my drive to see if that will make it show up in gparted, but I can only boot from this Ubuntu USB for some reason, and none of my other bootable USB sticks work.  It was something about trying to overwrite windows from this Ubuntu USB that makes my computer see this USB as a boot option, but none of my other bootable USBs work.

This is what I'd like to do: turn off secure boot in my BIOS, or else turn off UEFI and turn on legacy mode instead, and then I will be able to boot into DBAN and wipe the HDD to get rid of the windows formatting.  However, when I used the Ubuntu USB to overwrite windows, it messed up the BIOS and I absolutely cannot turn off secure boot, and it it won't let me boot from USB in secure boot mode (except this Ubuntu USB for some reason.)

This would also work: if there is some way that I can make gparted see the drive when I'm "tying Ubuntu" from the USB, then that should work too.  Is there some way I can make it see the drive?  Thanks!

**_SUMMARY:_**
Tried to overwrite windows from Ubuntu USB.  Installation failed. 
Fried my BIOS, can't disable secure boot so I can't boot from any USB besides the Ubuntu USB.
gparted doesn't see my HDD
can't boot from other USB with drive formatting tool.
I want to install Ubuntu, but it fails because it can't detect my HDD, and the fried BIOS is making hard for me to format the HDD for linux.
:-(  **Sorry I can't help you much, but SecureBoot is irreducibly complicated for cause.**  The firmwares for SecureBoot-certified hardwares and the shim-process software for bootloading use ECDSA-SHA256 keys issued by Microsoft Corporation.  Unfortunately, the vast majority of vendors of prebuilt SecureBoot systems for Microsoft® Windows® 10.0.18362.1 and later give the end user no access to settings in the BIOS/CMOS.

---

### Post by sevensixtwo on 2020-02-15
If the problem is the encrypted firmware for the hardware, then if I get a new HDD that should be fine then, right?  If I put a new HDD in there, then gparted ought to be able to see it.  Do you agree? Thanks.

---

### Post by sevensixtwo on 2020-02-15
> **yancek said:**
> The most common reason for a Linux installer not seeing windows partitions on windows 8/10 is because if was left in a hibernated state (default on windows).  No Linux OS will mount a hibernated system due to the likelihood of damaging the system.  Don't know how you can turn that off if you can't boot windows, maybe from the BIOS firmware?  What exactly failed in your attempt to install Ubuntu?  Did you get any error messages?

You haven't indicated the manufacturer of the computer.  If you do that, someone here familiar with it may have a suggestion on how you can deal with the problem accessing the BIOS.

The problem when I tried to install Ubuntu 18 on my Acer Aspire E5 was that the computer just turned off.  No error message.  Same thing still happens from the USB stick.  If I select "try Ubuntu" then it loads into the OS, but if I try to "install ubuntu" from the USB's boot menu, then the computer will just turn off after a few seconds.

---

### Post by yancek on 2020-02-15
Newer Acer computers with windows 10 installed require that a user access the BIOS firmware and create a supervisor password and then enable trust before another operating system can be installed.  Might do an online search for your specific Acer on exactly how to do this.

---

