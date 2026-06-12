---
title: "No Install alongside Windows 10 option appears when installing"
date: 2021-05-12
forum: Hardware
---

### Post by eddugo on 2021-05-12
Trying to dual boot windows 10 with Ubuntu 20.04 on a brand new HP 17-BY4063CL Laptop.  No option to install alongside appears.  Have tried disabling hibernate with no success.  Have not made any changes in the BIOS.  Thank you in advance for your assistance.

---

### Post by SeijiSensei on 2021-05-12
Likely the entire disk is already allocated to Windows leaving no space for Linux. HP does this all the time.  

Boot from an Ubuntu installation medium (DVD, USB drive) and pick "Try Ubuntu" from the menu.  Then open a terminal and run the command:

```
sudo fdisk -l /dev/sda
```

I bet you'll find there is no free space on /dev/sda (the main hard drive).  There are guides on how to reallocate space on the hard drive like this one, [https://www.amyschlesener.com/posts/2020/04/increasing-ubuntu-partition/](https://www.amyschlesener.com/posts/2020/04/increasing-ubuntu-partition/). This can be tricky if you need to preserve the Windows data intact.

I suggest instead [installing VirtualBox]("https://download.virtualbox.org/virtualbox/6.1.22/VirtualBox-6.1.22-144080-Win.exe") on the Windows machine, then installing an Ubuntu distribution into a new virtual machine.

---

### Post by eddugo on 2021-05-12
You are exactly right.  Just looked at Windows disk management and they have Windows using 100%.  The C; partition is 930 GB.  I don't know anything about virtual boxes and will have to do some research.  I only use windows when absolutely necessary and there is no Linux software so I may opt to shrink the partition.  Thank you for you reply and expertise.

---

### Post by QIII on 2021-05-12
If you choose to shrink the Windows partition, do so using the ***Windows tools***.

Using gparted or another Linux tool can completely destroy your Windows installation.

---

### Post by eddugo on 2021-05-12
I shrank the C: partition using Windows tools and now have a 537 GB unallocated partition - checked in disk management.   I rebooted Windows twice, booted to a live distro of ubuntu 20.04 and there is still no option to install alongside windows 10.  I checked the drive in Ubuntu and it doesn't appear in the d\Disk app.  Does Windows have a way to hide the Hard drive?

---

### Post by tea for one on 2021-05-12
Here is a little list of things to double check:-

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

Backup your data
Turn off Bitlocker
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

### Post by eddugo on 2021-05-18
No luck.  Ubuntu still cannot see the hard drive.  I tried all the above that were available and no change.  I have attached pics of the bios settings and the "Disks" ubuntu app.   
[ATTACH=CONFIG]288499[/ATTACH][ATTACH=CONFIG]288500[/ATTACH][ATTACH=CONFIG]288501[/ATTACH][ATTACH=CONFIG]288502[/ATTACH][ATTACH=CONFIG]288503[/ATTACH]

---

### Post by tea for one on 2021-05-18
> **eddugo said:**
>  Have tried disabling hibernate with no success.

Have you yet managed to shut down Windows 10 [COLOR="#FF0000"]without[/COLOR] hibernation?

From your attachment no. 2 in post no. 7, have you hit the little arrow near [COLOR="#0000FF"]UEFI HII Confuguration[/COLOR]?

Any clues there?

---

### Post by oldfred on 2021-05-18
I do not see any drive settings like AHCI/Intel RST in the UEFI screen shots?
Do you have latest UEFI from HP?
Or is drive setting under the UEFI HII config setting?

Changed to AHCI
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)

Used Intel App in Windows to disable Optane
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735)
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

---

### Post by eddugo on 2021-05-18
I opened the menu near UEFI HII Confuguration - tea for one.  There is a sequence of images attached.  I probably don't know enough about windows to find a clue there.  It's non-RAID and in AHCI mode.  olfred;  i have disabled optane.  I'm trying to find it in BIOS.  i have only disabled it in windows.  I miss the good ole days of 7.04 when all you did was put in the install disk and away you go.


[ATTACH=CONFIG]288510[/ATTACH][ATTACH=CONFIG]288511[/ATTACH][ATTACH=CONFIG]288512[/ATTACH][ATTACH=CONFIG]288513[/ATTACH]

---

### Post by eddugo on 2021-05-18
Actually, it looks like I don't have Optane (thought I disabled it - but must be wrong).  Device manager/Disks - shows no Optane drive

---

### Post by oldfred on 2021-05-18
Is there some way to turn off the Intel RST and just have AHCI?

---

### Post by tea for one on 2021-05-19
Your laptop has Intel 11th Generation processor and it seems that these processors were released in 2021.

Perhaps you can try a live session using Ubuntu 21.04 rather than 20.04?

---

### Post by eddugo on 2021-05-19
Good news!  It's loaded and everything works!  I loaded Ubuntu 21.04 on a DVD (which took a very long time to load - should have used a flash drive), got it to boot and all went normal from there.  I never thought about the fact that the 20.04 program might pre-date the processor - I just wanted the LTS program.  That was the problem.  Many thanks to all that worked on this.  !!SOLVED!!

---

