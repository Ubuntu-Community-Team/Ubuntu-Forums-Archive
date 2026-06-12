---
title: "Windows XP Profession Install"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Mainman407 on 2009-03-05
Yes:
Hopefully there is someone out there who can hopefully assist me with a problem I am experiencing with a new install of Windows XP Professional.

About a week or so ago I purchased a new 500G hard drive and installed it in my system. I then created a 1GB partition to install my Windows XP Pro onto. The Windows installation went exactly as it should. However, when I went to install additional software onto the remaining 498GB partition, my software install would always select the 1GB Windows XP partition. I simply could not access the larger partition.

So, I elected to delete this 1GB partition and split the 500GB drive into two 250GB drives, and then install Windows XP Pro onto the first 250GB partition. 

Well, when I began my new installation of Windows Setup,everything was fine up until the screen which asked if I wished to install Windows onto the selected drive. I pressed ENTER, then I pressed D to delete the 1GB drive partition, and created two 250GB partitions. 

After completing a full format of the C partition, Windows Setup began loading the necessary file required for Windows. After Windows completed loading these files, I was told that Windows would reboot in 15 seconds. I was not told that I wasn't suppose to press any key to boot from the CD when this message appeared on the screen. So, I pressed a key. I later learned this was a no-no. Now my computer will not recognize the hard drive.

I attempted to split the second 250GB partition into two 125GB partitions in order to install Windows onto a one of the 125GB (active) partitions, then I could delete the other two created partitions and migrate this 125GB partition when prompted in the Window Setup environment.

Well, the second Windows Setup install went like clockwork. All stages installed as they should have. Then, when Windows Setup rebooted, I DID NOT press any keys, and allowed Windows setup to bypass the "Press any key to boot from CD," message, hoping it would access the Windows Setup CD which was still in the CD tray. Moments later, a message appeared saying: Windows Cannot Read Disk. Press any key to Continue.

Okay Computer techs, what did I do wrong? I was told to download a software by the name of Gpart-Live which would allow me to repartition the drive. I also have a Spotmau PowerSuite2009 CD which is suppose to help me repartition my drive, but I cannot seem to get either of these softwares to work.

Can anybody out there help me?

My system was built my MicroPC back in 2000. I am told that MicronPC is in bankrupcy, but the information I was able to obtain said that my Motherboard is an Aurora-Gigabyte 7DX Motherboard with an AMD T-bird 1000MHz 200FSB PGA (Socket A) processor. My BIOS is SMBIOS: Ver:APM APM: ACPI: PCI: 2.2:PC99.
My (former) Operating System is Windows XP Professional w/o Service packs but I did purchase Service Packs 1&2 and installed them on a old 80GB hard drive.

---

### Post by martrn on 2009-03-05
Does your BIOS recognize you hard drive when you boot up ?  Like what it the BIOS saying about your hard drive when you press the <delete> key when switching on ?

I looked at your motherboard manual and the BIOS should give you exactly what your computer is capable of reading/writing to ! I can't see a yr2000 motherboard, reading/writing 500GB.

For Spotmau PowerSuite2009 CD, contact software / vendor or their forums.

---

### Post by abn91c on 2009-03-05
Like **martm** said I also do not think you PC can handle a 500 gig HDD, check the micron website for specs. Or look in the Tom's hardware website

---

### Post by Mark Phelps on 2009-03-07
Your problem lies in the outdated BIOS and how MS Windows installer sees the drives.  I have exactly the same problem with an old (2004) P4 PC with a failing primary drive.  Its BIOS could  "see" large drives but an attempt to reinstall Windows XP Pro failed to find the drives.

My solution was to do the following:
1) Stick in an old 60GB drive (which I had previously wiped)
2) Install Win XP Pro to that drive (which Windows COULD see)
3) Attach my new drive (320GB)
4) Use Acronis utilities to "copy" the OS installation to the new drive
5) Replace the old drive with the new drive
6) reboot

And now ... I have XP Pro booting and running from the new drive.

Kludgy, but hey -- it worked!

---

