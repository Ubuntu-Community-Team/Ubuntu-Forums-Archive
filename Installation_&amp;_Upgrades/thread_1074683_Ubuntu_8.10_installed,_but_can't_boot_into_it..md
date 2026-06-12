---
title: "Ubuntu 8.10 installed, but can't boot into it."
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by cyb3r0rg on 2009-02-19
Hi, i'm new here. 

Pardon me if i'm not clear. 

So, here is goes
1. Downloaded the latest version 8.10
2. Defragged my harddrive 120GB(but divided into C and D drive)
3. Burned into my thumdrive(1GB) using unetbootin
4. Boot via usb afterwards
5. Installing ubuntu
5.1. Choosed the default setting for partition
5.2. Asked to import settings from my default OS(Vista)
5.3. Checked those options
5.4. Error occured while importing(couldn't really remember what were those)
6. Rebooted to test out Fresh installed Ubuntu
7. Was brought to Vista at once
8. Downloaded easyBCD to manage bootloader, but when i checked, there were a few partitions

*c:\ 
*d:\
*?????? 
*native linux (10GB)
*swap (1GB)


I tried looking into the treads but i can't find any solutions. 
What should i do now?

---

### Post by Sub101 on 2009-02-19
Can I suggest you download the Grub Disc use the options on there. If that doesnt work, or grub is not there at all then follow this tutorial here:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by cyb3r0rg on 2009-02-19
i tried the second option, but it does not work. 

for the first, u mean super grub disc instead?

---

### Post by Sub101 on 2009-02-19
Yeh the super grub disc. What was the error with the second?

---

### Post by cyb3r0rg on 2009-02-19
i stopped at find /boot/grub/stage1 and couldn't continue. 

for super grub disk, i tried auto super grub disk [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub"), but to no avail

---

### Post by cyb3r0rg on 2009-02-19
i stopped at find /boot/grub/stage1 and couldn't continue. 

for super grub disk, i tried auto super grub disk [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub"), but to no avail

---

### Post by Sub101 on 2009-02-19
So what was your output to find boot/grub/stage1?

---

### Post by cyb3r0rg on 2009-02-19
Error 15: File not found

---

### Post by Therion on 2009-02-19
> **cyb3r0rg said:**
> 
...

5. Installing ubuntu
5.1. Choosed the default setting for partition
5.2. Asked to import settings from my default OS(Vista)
5.3. Checked those options
5.4. Error occured while importing(couldn't really remember what were those)
Okay, back up a second for me here.  I've done a few Unetbootin installs and I don't remember ever being asked about "importing settings" from the "default OS"...  And this occurs during the Ubuntu install you say?   As I recall, after setting up the partitions you're prompted for Language, Keyboard layout, timezone, computer name, user-name and password and that's about it. 

At what point during the Ubuntu install are you prompted to import these settings?  And what settings are you supposed to be able to import?

---

### Post by Sub101 on 2009-02-19
It sounds to me that Ubuntu has not installed properly. Maybe wait and see if any other users have any other ideas. If it was me, I would go for a reinstall.

---

### Post by cyb3r0rg on 2009-02-19
yea, after all those Language, Keyboard layout, timezone, computer name, user-name and password inputs. 

importing the settings was the last thing.

EDIT: as for importing, i was asked to import all those settings from my default OS.the settings were Mozilla Firefox, Internet Explorer, My Pictures, My Music, My Videos. i could recognise because it had my name there

---

### Post by maclinux on 2009-02-19
In my case its different.  I complete the 8.10 upgrade and after restarting it loads up and goes into a black screen with no prompt at all.  When restarting I find in grup the kernel upgrades and if I choose the 8.04 kernel it loads up perfectly and with the new upgrade to 8.10.  The going into the blackbox after loading also happens while trying to install from de 8.10 cd.  Live cd or straight to install it goes straight into a black screen.  with 8.04 everything is always fine.

What is happening?  How can I go around it?

---

### Post by cyb3r0rg on 2009-02-19
> **Sub101 said:**
> It sounds to me that Ubuntu has not installed properly. Maybe wait and see if any other users have any other ideas. If it was me, I would go for a reinstall.


i don't mind reinstalling, but right now im a little bit lost. because i have checked the partitions of my hard disk right now using easyBCD as mentioned in my previous posts, i have 5 partitions instead of 4, which i know that something is wrong right now as i can only have 4 partitions.

Before Ubuntu installation :
Harddisk : 120GB
C:\ 70GB
D:\ 50GB

After Ubuntu installation : 
C:\ 60+GB 
D:\ 40+GB
?????? 10GB //i have this unknown partition drive
Linux Native 12GB
Linux Swap 1GB

---

### Post by Sub101 on 2009-02-19
The 10Gb may be just space between the logical drives.

---

### Post by cyb3r0rg on 2009-02-19
i wonder would this help

---

### Post by Therion on 2009-02-19
If you want to run JUST Ubuntu version 8.10 click on the button that says "Guided - use entire disk" and proceed with the installation process.

That selection will effectively wipe out everything currently on the hard drive and then install Ubuntu 8.10 as the sole operating system.

---

### Post by cyb3r0rg on 2009-02-19
I still want to keep vista in my computer(for now)

Right now, i still can't solve the boot issues, i have tried 
1. sudo grub
1.1. find /boot/grub/stage1
1.2. find /grub/stage1 //Error 15: File not found
2. fdisk -l (it just shows me the usb information which i boot from)
It shows: 
Cannot open /dev/sda

Disk /dev/sdb: 1059 MB, 1059061760 bytes
64 heads, 32 sectors/track, 1010 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1010     1034208    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 63, 32) logical=(1009, 62, 32)

3. auto super grub disk
4. easyBCD

which are all stated in this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

i don't mind doing a reinstall since i have nothing inside ubuntu yet. but i can't find a way to reinstall it. i try booting using usb and clicking on the install button, follow through the steps(language etc.), but when i comes to partition, i need to create another two partition(which i can't). 

any ideas on how to tackle it from here?

---

### Post by cyb3r0rg on 2009-02-19
i just realized something, as i was trying to reinstall the whole thing.

the attached screenshot is the error

---

