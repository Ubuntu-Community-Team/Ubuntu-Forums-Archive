---
title: "Can't Uninstall: Demo and Full Installation Problem!!!"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Svedka on 2009-09-12
Hi,

I'm entirely new to Ubuntu, just got it a few days ago. Basically I chose the Demo and Full Installation option to try it out and see how I liked it.
After doing so, I decided to keep it, but only with virtualbox as I need XP to run my audio applications.
Now, everytime I reboot the computer I have the option to boot from XP or Ubuntu. I want to completely remove that Ubuntu option since I already have it in virtualbox.

My first thought was to start Ubuntu (9.04) and see if there was an uninstall option. To my demise, everytime I do try i get the following message:

Loading Please wait...

Busybox v1.10.2 (Ubuntu 1:1.10.2-2Ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)

-------------------------------

It just stays there and Ubuntu never loads up.

I tried a fresh reinstall but I get the same exact problem.
The first time I installed it I did it directly from the ISO. I've now tried CD and USB approach, both with the same results.

I unmounted the ISO (I was using magic disc), uninstalled wubi and still everytime I restart I get the option to choose an OS.

Can anyone please help?

I'm running Windows XP Pro on a Dell XPS 630, if that's of any help.

Thanks in advance.

---

### Post by presence1960 on 2009-09-12
Boot from your XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"). Follow the instructions for XP.

Let's see if I understand you correctly. You have XP installed and are running Ubuntu from Virtual Box within XP? You do not have Ubuntu installed to a partition on your hard disk? If this is correct proceed with the above process. That will put windows back on MBR of your hard disk and you will boot right into windows.

If it is any other scenario we need to see what setup & boot process you have. Do this:

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Svedka on 2009-09-13
Thanks for your help. I guess I should clarify. 
First thing I did was install from the Ubuntu Live CD. After trying it and loving it I decided that instead of making a new partition for it I would just use Virtualbox to run Ubuntu.
[B][I]
"Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads"[/I][/B]

See, at this point Ubuntu won't even load up from the Live CD, which is my main problem. I can run Ubuntu from Virtualbox, but not for the partition that it seems the Live CD created (tho I used the Demo and full installation option).

Everytime I reboot my computer I get the option to boot from Windows XP or Ubuntu.
What I want to do is completely remove the Ubuntu option.

I've tried fresh reinstalls of Ubuntu from the Live CD but it always gets stuck at the following message:


Loading Please wait...

Busybox v1.10.2 (Ubuntu 1:1.10.2-2Ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)

---

### Post by Svedka on 2009-09-13
anyone?

---

### Post by raymondh on 2009-09-13
Svedka,

To uninstall Ubuntu ... it depends on how you installed it in the first place.

Did you do a wubi install?  If so, uninstalling ubuntu is like uninstalling a program in windows (using add/remove from control panel).  Now, to remove the ubuntu when you boot (even after you remove Ubuntu), you will need to edit the boot.ini file ..... **remember, just the wubi related line or else you will not boot into XP as well**.  [See this guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?").

If you installed Ubuntu in its' own partition, then you have to

1.  Use a disk management tool to delete Ubuntu and it's swap
2.  Boot into an original XP installation disc (not the recovery disc) and access a command prompt to FixMbr.
3.  Enlarge windows to take up the empty space

So, how did you install Ubuntu in the first place?  Post back if you need clarification or assistance.

---

### Post by Svedka on 2009-09-13
Thank you so much, editing boot.ini took care of it! :D

I wonder why this all happened tho? I never made a partition for Ubuntu, all I did was run the livecd to test it out and it looks like it installed a corrupted version of it.

---

### Post by raymondh on 2009-09-13
> **Svedka said:**
> Thank you so much, editing boot.ini took care of it! :D

I wonder why this all happened tho? I never made a partition for Ubuntu, all I did was run the livecd to test it out and it looks like it installed a corrupted version of it.

Excellent news.

It seems that you have installed Ubuntu "inside-windows" (or WUBI-installed).  You may have put in the liveCD when windows was running.  Nevertheless .... wubi is when Ubuntu is accessed thru a .exe file hence making Ubuntu a "file" within windows.  You delete/remove it using the add/remove option.  As for the boot option, it (ubuntu) is attached to your existing windows bootloader to give the 2-boot option.

You mentioned that you have Ubuntu now virtualized with XP as the 'host'.  Keep XP clean, defragged and happy.

Just out of curiosity .... take a look at your XP disk management utility.  Does it show a ext3 partition ... or just NTFS (or FAT) formats?

Happy ubuntu-ing.

---

### Post by Svedka on 2009-09-13
[I][B]"You delete/remove it using the add/remove option"

[/B][/I]That's one of the first things I tried unsuccessfully as it wouldn't show up under Add/Remove programs.

***"Does it show a ext3 partition ... or just NTFS (or FAT) formats?"***

NTFS, FAT and FAT32

---

### Post by raymondh on 2009-09-13
> **Svedka said:**
> [I][B]"You delete/remove it using the add/remove option"

[/B][/I]That's one of the first things I tried unsuccessfully as it wouldn't show up under Add/Remove programs.

***"Does it show a ext3 partition ... or just NTFS (or FAT) formats?"***

NTFS, FAT and FAT32

Hmmmm, 

Nevertheless, am glad you have your issue solved.  If you want, kindly mark your thread solved by going to THREAD TOOLS (on top).

Congratulations and happy ubuntu-ing.

---

### Post by theozzlives on 2009-09-13
> **Svedka said:**
> [I][B]"You delete/remove it using the add/remove option"

[/B][/I]That's one of the first things I tried unsuccessfully as it wouldn't show up under Add/Remove programs.

***"Does it show a ext3 partition ... or just NTFS (or FAT) formats?"***

NTFS, FAT and FAT32

If you installed via VirtualBox or WUBI, Ubuntu is in a file on your NTFS partition. It's NOT a demo.

If you installed by booting off the CD, it Too is not a demo and will be on an ext3 partition.

---

