---
title: "Dual Boot Ubuntu already installed - 2 HD's"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by mannyfresh8 on 2009-10-07
I have just built my first desktop and want to run a dual boot between Xp Pro 64 bit and Ubuntu 9.04. I didnt realize I should have installed windows first until after I installed it so My BAD. Anyway I have been hearing that this isn't a problem since I have 2 separate Sata HD's. Currently the HD with Ubuntu is the Master and the 2nd drive is the Slave. Each has 750GB. Now currently Ubuntu doesn't recognize the 2nd drive as part of the Systems Disk Space but it can be found under places and asks me to mount the drive. I haven't done so since I have no clue what its asking me to do.
 
 Moving on I am thinking about doing the dual boot and have come across some examples where people install ubuntu on one drive and windows on the 2nd drive. How would I do this? Should I disconnect my ubuntu drive and install windows as if normal. Then once that is complete reconnect the Ubuntu drive. Does this seem correct?

Please let me know if i am going about this right or not. I am completely new to this. Thank you.

---

### Post by mikewhatever on 2009-10-07
Just install Windows on the second hdd, as if Ubuntu hadn't existed. It doesn't matter if you disconnect the drive with Ubuntu.

---

### Post by presence1960 on 2009-10-07
> **mikewhatever said:**
> Just install Windows on the second hdd, as if Ubuntu didn't existed. It doesn't matter if you disconnect the drive with Ubuntu.

if you do not disconnect the drive with Ubuntu make sure you go into BIOS and make the disk that you are putting windows onto first in the hard disk boot order. if you fail to do this you will get a message that windows is trying to write it's bootloader to the other disk which contains another OS, which is your Ubuntu disk- you don't want that to happen! Windows always writes it's bootloader to the first disk that boots in BIOS.

When windows install is complete switch the disk with Ubuntu back to first in the hard disk boot order in BIOS. This will bring up GRUB when the machine boots. 

After that you will have to add the windows entry in menu.lst so you will get an option to boot into Windows from the GRUB menu. post back and we'll help that get squared away after you install windows.

---

### Post by mannyfresh8 on 2009-10-08
> **mikewhatever said:**
> Just install Windows on the second hdd, as if Ubuntu didn't existed. It doesn't matter if you disconnect the drive with Ubuntu.
 
 
 
 
Thanks for the link, I got to read this when I get home.

---

### Post by mannyfresh8 on 2009-10-08
> **presence1960 said:**
> if you do not disconnect the drive with Ubuntu make sure you go into BIOS and make the disk that you are putting windows onto first in the hard disk boot order. if you fail to do this you will get a message that windows is trying to write it's bootloader to the other disk which contains another OS, which is your Ubuntu disk- you don't want that to happen! Windows always writes it's bootloader to the first disk that boots in BIOS.
 
When windows install is complete switch the disk with Ubuntu back to first in the hard disk boot order in BIOS. This will bring up GRUB when the machine boots. 
 
After that you will have to add the windows entry in menu.lst so you will get an option to boot into Windows from the GRUB menu. post back and we'll help that get squared away after you install windows.
 
 
Thanks I actually just finished installing windows last night. Now when I have each OS on its own HD can I access files on Either HD from Either OS? For example in my situtation I plan to do my school work using windows because I need to use Adobe CS4. Now after I save my current work I want to be able to post it to my Online Class using the Linux OS. Essentially I never want the Windows OS to have access to the Internet. Not sure if this setup actually is possible. Perhaps installing both OS on the same HD and then just formatting and mounting the 2nd HD in NTFS format, would be a better option. Thanks again for all your help. I really like Linux so far. Its a huge culture shock between windows and Linux but I like the change and the challenge to  learn.

---

### Post by presence1960 on 2009-10-08
> **mannyfresh8 said:**
> Thanks I actually just finished installing windows last night. Now when I have each OS on its own HD can I access files on Either HD from Either OS? For example in my situtation I plan to do my school work using windows because I need to use Adobe CS4. Now after I save my current work I want to be able to post it to my Online Class using the Linux OS. Essentially I never want the Windows OS to have access to the Internet. Not sure if this setup actually is possible. Perhaps installing both OS on the same HD and then just formatting and mounting the 2nd HD in NTFS format, would be a better option. Thanks again for all your help. I really like Linux so far. Its a huge culture shock between windows and Linux but I like the change and the challenge to  learn.

That set up is very east to do. Just set your firewall in Windows to lock down the internet connection.

Linux can access windows directories on any hard disk, but windows can not access Linux directories natively. There are drivers you can install to access linux ext2 or ext 3 file system from windows, but I think ext 4 is not available yet. See [here]("http://www.fs-driver.org/").

---

### Post by parrotred on 2009-10-08
i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty


I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following

sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work

so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

---

### Post by presence1960 on 2009-10-08
> **parrotred said:**
> i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty


I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following

sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work

so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

parrotred this is the third thread you have posted the same info about the same problem. Two are in Installation & Upgrades section and one in Absolute beginners section. Please refrain from creating multiple posts on the same subject/problem and try creating your own thread for your problem. it is hard to give directions to two people with two problems in the same thread.

Also I would suggest some patience to get a response as we are not paid support.

---

### Post by mannyfresh8 on 2009-10-08
> **presence1960 said:**
> That set up is very east to do. Just set your firewall in Windows to lock down the internet connection.
 
Linux can access windows directories on any hard disk, but windows can not access Linux directories natively. There are drivers you can install to access linux ext2 or ext 3 file system from windows, but I think ext 4 is not available yet. See [here]("http://www.fs-driver.org/").
 
 
Thank you so much you don't know how helpful you have been. I tell you right now that because of these forums I like Linux and I can't wait to be able to help people just as you helped me.
 
I will let you know how this turns out. I am going to try and set everything up tonight. The only thing I think I am missing is how to modify GRUB to include Windows on the boot list. I think I have found this info on other threads I will look around.
 
Thanks again.

---

### Post by presence1960 on 2009-10-08
> **mannyfresh8 said:**
> Thank you so much you don't know how helpful you have been. I tell you right now that because of these forums I like Linux and I can't wait to be able to help people just as you helped me.
 
I will let you know how this turns out. I am going to try and set everything up tonight. The only thing I think I am missing is how to modify GRUB to include Windows on the boot list. I think I have found this info on other threads I will look around.
 
Thanks again.
If you have problems or need help setting up GRUB post back.

---

### Post by mannyfresh8 on 2009-10-08
> **presence1960 said:**
> parrotred this is the third thread you have posted the same info about the same problem. Two are in Installation & Upgrades section and one in Absolute beginners section. Please refrain from creating multiple posts on the same subject/problem and try creating your own thread for your problem. it is hard to give directions to two people with two problems in the same thread.
 
Also I would suggest some patience to get a response as we are not paid support.
 
> **parrotred said:**
> i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty
 
 
I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following
 
sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"
 
This did not work
 
so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"
 
This did not work
 
 
Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.
 
 
Parrotred, I am also new to Linux and have found these forums very useful just be patient. I think in your situation Ubuntu must be first and then you can modify GRUB which can give you the option of loading windows or not. Otherwise another option is to change the boot order through BIOS each time. Just keep it on the Windows HD until you need Linux and then change the Boot order through BIOS. Not 100% sure but if I am this would be by first response that I helped someone. lol

---

### Post by presence1960 on 2009-10-08
parrotred,

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mannyfresh8 on 2009-10-09
Presence1960,

Thanks so much. I actually had the dual boot working perfectly with 720GB as a shared NTFS partition and Windows XP assigned to the remaining 30GB. Then on the 2nd drive I just installed ubuntu on the entire disk. I didn't even have to modify GRUB. Thats when I got greedy. I was like maybe I will partition the 2nd drive the same way as the first one. So I set Ubuntu to a 30GB partition and then a 20GB swap partition and then the remaining as free space( was going to format using windows to NTFS) but when I restarted my computer I received an error from the boot loader. 

Error 13: Invalid or Unsupported executable fromat

So I got frustrated and just reinstalled Ubuntu on the 2nd drive just as I did earlier. And the Dual boot works. But I am curious why this happened. Is it because I left that unpartitioned portion unformatted? Should I have formatted it as ext3 and then just reformatted with windows to NTFS? I am just curious at this point since I was just being greedy earlier.

Thanks again for your help. I am going to mark this thread solved since I understand how the shared drives and mounting works now. But I would still like to see what you say about this new issue.

---

### Post by parrotred on 2009-10-10
as per the instruction i have run the script and attached 2 results.txt.

results-live.txt
results-bios.txt

result-live.txt is done usung live cd

result-bios.txt is done by changing the hard disk from bios.

Thanx in advance.

Sorry for the multiple post but that was only out of frustration first because of the hardware problems and then with dual boot

---

### Post by presence1960 on 2009-10-10
[QUOTE]> **parrotred said:**
> as per the instruction i have run the script and attached 2 results.txt.

results-live.txt
results-bios.txt

result-live.txt is done usung live cd

result-bios.txt is done by changing the hard disk from bios.

Thanx in advance.

You need to do two things- first switch the order of hard disk booting in BIOS and add a windows entry to menu.lst.

1. Reboot your machine and go into BIOS. Set your 20 GB (sdc) as first hard disk to boot followed by the 80 GB (sda) then lastly the 160 GB (sdc). save changes to CMOS then exit. When you continue booting GRUB will come up. Choose Ubuntu.  

2. You need to edit menu.lst in sdc1 by adding a windows entry.Open as root menu.lst- Scroll down to:

**### END DEBIAN AUTOMAGIC KERNELS LIST**

skip a line then add this:

```
title           Windows XP
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

Click Save on the toolbar, close file and reboot. You should now be able to boot into Windows too.

---

