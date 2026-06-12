---
title: "issue in installation of ubuntu in Dell PC"
date: 2018-12-10
forum: Hardware
---

### Post by tribeni.mishra on 2018-12-10
Hi,
I have a Dell Inspiron 5570 Laptop (8th Gen Ci7/ 8GB /2TB / Win10/ 4GB  Graph), which I bought one year ago. It had inbuilt windows 10 operating  system provided by Dell but I replaced windows 10 OS by ubuntu 16.04 as  I need linux for my analysis work. It worked fine for nearly 6 months  than it showed some I/O error and ACPI error.
Some computer personnels in my institute managed to fix the issue that  time. Than it ran smoothly for 3-4 months. It stopped working suddenly  few days back with error message:

[COLOR=#0000ff]ACPI Error: Namespace lookup failure, AE_NOT_FOUND
ACPI Error: Method parse/execution failed
[/COLOR]
I erased the disk and did fresh installation but I still couldn't fix  the issue. It is working fine with windows 10 but it is showing  following error while ubuntu installation.
I tried installing ubuntu 16.04, 18.04, 18.10 and CentOS. Either it  fails with some kind of following errors while installation or  started  showing errors after few hours of installation.

Error I saw while installation and after installation.
[COLOR=#0000ff]
[1]. alloc magic is broken at 0x4ac4f720: 720606892702957b:Aborted. Press any key to exit.

[2]. EXT4-fs error (device sda2):ext4_find_entry:1438: inode #44828174: comm gdm-session-wor:
     Buffer I/O error on dev sda2, logical block 0, lost sync page write
     EXT4-fs(sda2): I/O error while writing superblock

[3] pcieport 0000:00:1c.5: PCIe Bus Error:severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
     device [8086:9d15] error status/mask=00002001/00002000
[4] Error fsyncing/closing/dev/sda1:Input/output error
[/COLOR]

Though my laptop is under hardware warranty and I should get it repaired  for some hardware issue, but it is detecting the HDD in BIOS menu. I  goggled each of the above error messages and got some hints that it may  be because of hard drive issue. But the Dell Service Care is not agree  that it has hardware issue since the system is working fine with Windows  10.( which also sounds logical.)

Can anyone please help me out , suggest some solution, give some concrete reason behind the issue.

Thanks a lot in Advance.

Tribeni

---

### Post by Autodave on 2018-12-10
Anytime that I see an error relating to the superblock, that tells me that a HD is/has failed.  Hopefully someone else here will have a better answer for you.

---

### Post by oldfred on 2018-12-10
I think I get the ACPI errors on both of my systems in UEFI boot mode. But no other issues and I gather it is not critical.

But as Autodave says errors on drive can be a problem.
What does Smart Status say about drive. You can use Disks on live installer and in upper right corner icon is Smart Status. It can run lots of tests, but all I know is if it says drive is good or bad.

---

### Post by Autodave on 2018-12-11
If it says the drive is bad, its bad.  If it says it is good...........could be good or bad.

---

### Post by tribeni.mishra on 2018-12-12
Thanks, Autodave.. I also guess the issue is in HDD. But how should I get confirmation. When I call the Dell service care they asked to do a testing of HDD.

    Restart the computer.
    As the computer boots, press the ESC key when the HP Splash Screen appears.
    When the Startup menu appears, press F2 to enter System Diagnostics.
        System Information: Shows information such as hardware installed and BIOS version.
        Start-up Test: A quick, high level test of the system.
        Run-In Test: A stress test to verify stability of system components.
        Hard Disk Test: Test the hard drive for problems. First it will run a quick test and then a SMART test. This test will take approximately two hours to finish.


Everything showed fine, it is reading HDD and there is no issue in Hard Disk test. So, it is difficult to show the harddisk issue in Windows however I can't install ubuntu. If there is issue in HDD than I should see the same in Windows.

Is there is any other testing I can do ?

Thanks.

---

### Post by tribeni.mishra on 2018-12-12
Thanks oldfred, what do you mean by "smart status about drive". I am a new user of ubuntu ,so I don't know much about checking issues in ubuntu OS. but now the status is that I am not able to install ubuntu. Is there some way I can check this in windows ? In BIOS menu , it says HDD is good and it can read 2TB HDD.

---

### Post by deadflowr on 2018-12-12
> **tribeni.mishra said:**
> Thanks oldfred, what do you mean by "smart status about drive". I am a new user of ubuntu ,so I don't know much about checking issues in ubuntu OS. but now the status is that I am not able to install ubuntu. Is there some way I can check this in windows ? In BIOS menu , it says HDD is good and it can read 2TB HDD.

Oldfred means you can use Ubuntu's installer disk/usb to run a live session, where you can open a program called Disks and run a smart check.
smart is a disk health check utility built into most disks,

the live session can be invoked at boot by selecting the Try Ubuntu option.

Some on smart on Ubuntu here:
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en]("https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en")
More smart here:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

Try Ubuntu tutorial here:
[https://tutorials.ubuntu.com/tutorial/try-ubuntu-before-you-install#0]("https://tutorials.ubuntu.com/tutorial/try-ubuntu-before-you-install#0")

---

### Post by oldfred on 2018-12-12
Have you updated UEFI from Dell?
It will then need resetting any changes you made in UEFI settings as many are reset to defaults.

Have you changed drive setting in UEFI to AHCI from RAID or Intel SRT?

See link in my signature for general UEFI install instructions.

some other Dell 5000 series:
       Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)
Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

