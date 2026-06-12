---
title: "The volume &quot;boot&quot; has only 0 bytes disk space remaining.    Need complete basic fix."
date: 2013-11-06
forum: Hardware
---

### Post by TomBrooklyn on 2013-11-06
v.13.2 (I think)

1. How do I fix the subject error?     I would appreciate complete, detailed, and basic instructions.  


1.1  Under the Disk Usage Analyzer, my boot usage is 100% and the size is 236MB with Contents of 297 items. 


1.1.1  The computer is a circa 2008 Lenovo ThinkPad 400 laptop with a 40 GB hard disk and 2GB of RAM. 


1.2    I googled the problem and found solutions.     The solutions indicated to enter some gobbledigoop into the Terminal; but it didn't say what the Terminal was or where to find it.    So I googled the Terminal; and I found instructions to find it in The Dash; but it didn't say what the Dash was or where to find it.   But I searched and found The Dash; and I opened it.     But there is no Terminal in my Dash.     

Now I think I've put more than enough effort into searching dead ends and incomplete responses.     I'd appreciate it if someone could post, or direct me, to a complete and accurate set of instructions on what to do.     The operative word there is complete.   That would mean not assuming any prior knowledge on the part of the user.  


1.3      In the meantime, I am being offered to upgrade to v. 13.10.   If I do that, will the whole issue disappear?

1.3.1  How about if I format the hard drive and then install v. 13.10?

1.3.2  Is it possible to designate more space to this so-called boot sector so this doesn't happen again so soon? (I have barely used this computer for 30 hours to watch a few videos on you tube and that I uploaded.)

1.3.2.1  Are there any other methods of preventing this error from happening so frequently, or at all?

---

### Post by ian-weisser on 2013-11-06
> **TomBrooklyn said:**
> v.13.2 (I think)
Doubtful. No such release exists.

> **TomBrooklyn said:**
> 1. How do I fix the subject error?     I would appreciate complete, detailed, and basic instructions.  
Please describe, as detailed as possible, exactly how you get the error.
We will help you, but please understand that we are not psychic and do not know your ability level. "Complete, detailed, and basic" may mean something quite different to each of us.

For example, most solutions require the use of Terminal, which is simple for most users to locate in the dash (open Dash, type "terminal")...*if* you are actually using the Unity version of Ubuntu. Other versions have different ways of accessing a terminal Since you seem unsure about what you are using, and seem this may be a slow process. Please be patient.

Have you been able to locate a terminal on your system? Do you need more help finding it?


> **TomBrooklyn said:**
> 1.1  Under the Disk Usage Analyzer, my boot usage is 100% and the size is 236MB with Contents of 297 items. 
Do you know if you have a separate /boot partition? Most people don't have one. You must do extra work to create one.
What about the usage of your entire Ubuntu partition?

> **TomBrooklyn said:**
> 1.3      In the meantime, I am being offered to upgrade to v. 13.10.   If I do that, will the whole issue disappear?
Don't do it! You *must* fix the boot problem first. Otherwise you risk a broken upgrade.

> **TomBrooklyn said:**
> 1.3.1  How about if I format the hard drive and then install v. 13.10?
This is one possible solution.
While it's easy for you to do, it's time-consuming, unnecessarily intrusive, and risks data loss.
With a bit of patience, several easier and faster alternatives are possible.

> **TomBrooklyn said:**
> 1.3.2  Is it possible to designate more space to this so-called boot  sector so this doesn't happen again so soon?
It's probably not a boot *sector* (which is a real thing), it's probably a boot *partition *(which is a very different real thing)
You should know if you created a /boot partition. Do you recall doing so?
If not, then your entire Ubuntu partition may be full. Adding space to it may be easy or tricky depending upon your system. 40GB is a lot, but a few movies will eat through that pretty quickly.

---

### Post by btindie on 2013-11-06
It sounds more like your /boot partition has been filled up with new kernel's and the old ones have been left hanging around.

Please provide the output of
```
df -h /boot
```
```
dpkg-query -W -f='${Package}\n' 'linux-image-*'
```

You'll probably just need to uninstall the old kernels.

---

### Post by grahammechanical on 2013-11-06
Perhaps this is a problem with not having a complete understanding of how Linux works and what disk usage analyser is reporting. I have Ubuntu in a partition of 38 GB. Disk Usage Analyser tells me that only 12.7 GB is used. But when I get Disk Usage Analyser to scan the partition I get the report that / (not boot) but the / (root) folder has 100% usage at 12.6 GB. The root folder is a folder that can vary in size. It will always show 100% usage. All the other folders in LInux come under the root folder. I have found when testing the development version of Ubuntu on a 10 GB partition I get disk full warnings when the unused space on the partition drops to around 500 - 600 MB. Are you getting any warnings like that? I would not recomend trying to fix things through a terminal until you have a better understanding of Linux and Ubuntu. You certainly need to give us more information about your setup and partitioning scheme before we can make any recommendations. Otherwise there will be a great risk of causing more damage. I have yet to be convinced that you do indeed have a problem.

---

### Post by TomBrooklyn on 2013-11-07
> **ian-weisser said:**
> Doubtful. No such release exists.The correct release of ubuntu I have is 13.04.

> **ian-weisser said:**
> Please describe, as detailed as possible, exactly how you get the error.-  The error appears on boot up.   On every boot-up now.    

- The Window is titled: Low Disk Space

- The exact message wording with formatting replicated to the best of my ability is:
 
[INDENT] **The volume "boot" has only 0 bytes disk space remaining.**  [/INDENT]

[INDENT]You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.     
Don't show any warnings again for this file system.
[/INDENT]

[INDENT][INDENT]Examine... [/INDENT]Ignore[/INDENT]

> **ian-weisser said:**
>  we are not psychic and do not know your ability level.  I attempted to describe my ability level of knowledge of ubuntu in my original post.    My Level=absolute neophyte.    My Knowledge of the OS is virtually non-existent.    That is why I requested a solution that assumes I have no prior knowledge of the OS.    

> **ian-weisser said:**
>   most solutions require the use of Terminal, which is simple for most users to locate in the dash (open Dash, type "terminal")  Have you been able to locate a terminal on your system?.I found it now by following your clear instruction to type Terminal in the Dash. 

> **ian-weisser said:**
>  Do you know if you have a separate /boot partition? Most people don't have one. You must do extra work to create one.  I didn't create a separate boot partition, so unless ubuntu made something I don't know about, I don't have one. 

> **ian-weisser said:**
>  What about the usage of your entire Ubuntu partition?If you're asking what I have on the partition, I have about 2.5 hours of videos  and a few applications like Libre Office.       I have very little data.   I can't check exactly what I have because I don't know how to find the directory structure or what is on the hard drive.   I wish I knew how to do that too.

---

### Post by TomBrooklyn on 2013-11-07
> **btindie said:**
> It sounds more like your /boot partition has been filled up with new kernel's and the old ones have been left hanging around.
Yes.  That's all it is.  I already know that because I googled it and found numerous results explaining that.     Reference: 

[https://www.google.com/search?q=The+volume+%22boot%22+has+only+0+bytes+disk+space+remaining.&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=The+volume+%22boot%22+has+only+0+bytes+disk+space+remaining.&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)


The problem is that the solutions presented in the above results were not written in a way somebody with no knowledge of ubuntu could follow.    For instance, it was said to open the terminal, but not where to find the terminal, etc.   (I now know where the terminal is.)

Take a specific result for instance: 
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

Since I now know where the Terminal is, I was able to find the Linux kernel I am running.    However, I cannot follow the next instruction, "Open the Synaptic package manager from the System->Administration menu.", because I don't know where to find System->Administration menu.


Do you see my problem now?     That's why I asked for a set of instructions that was complete and doesn't assume I had any prior knowledge.

---

### Post by coffeecat on 2013-11-07
We need some terminal output otherwise we'll just be speculating. 

This:

> **TomBrooklyn said:**
> 
1.1  Under the Disk Usage Analyzer, my boot usage is 100% and the size is 236MB with Contents of 297 items. 

Sounds like a separate boot partition to me. And, no, Ubuntu does not create a separate boot partition unless you tell the installer to do so.

Post the output of these two terminal commands:

```
df -h
mount
```

They will tell us whether or not you have a separate boot partition and provide more information on disc usage. If you highlight the terminal output with your mouse, you can right-click -> copy, and then paste into the message editor for your post.

---

### Post by ian-weisser on 2013-11-07
Great answers!
It's progress.

First, please open a terminal and try the following command: **sudo fdisk -l**  (that's a lowercase L)
The system will ask for your password - when you type it and hit ENTER, the cursor won't move. It's supposed to not move.
The result should be something like:
```
$ sudo fdisk -l
[sudo] password for ian:    (THE CURSOR WON'T MOVE)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf2f58677

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   471780854   235890396   83  Linux
/dev/sda2       471780855   488392064     8305605    5  Extended
/dev/sda5       471780918   488392064     8305573+  82  Linux swap / Solaris

```

Copy and paste yours here in the thread. 
Copy is SHIFT +CTRL+C, or use the edit menu.
Paste is SHIFAT+CTRL+V, or use the edit menu
Use the code formatting tags to make your output readable: [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)


Second, please try the command **df** in a terminal. Paste the output there in within code tags.
Your df should look something like this:
```
$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      232188636 183962656  36431464  84% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1408532         4   1408528   1% /dev
tmpfs             284192      1140    283052   1% /run
none                5120         0      5120   0% /run/lock
none             1420960       216   1420744   1% /run/shm
none              102400        52    102348   1% /run/user
```

Third, please try the command **uname -r  **in a terminal, and post the result here.
Your uname -r should look something like this:
```
$ uname -r
3.11.0-12-generic
```

Finally, please try the command **ls -l /boot** (those are lowercase Ls) in a terminal, and paste the result here inside code tags.
Your result may look something like this:
```
$ ls -l /boot
total 141320
-rw-r--r-- 1 root root   734707 Oct  7  2011 abi-3.0.0-12-generic
-rw-r--r-- 1 root root  1009450 Oct  9 11:45 abi-3.11.0-12-generic
-rw-r--r-- 1 root root  1010091 Oct 23 13:00 abi-3.11.0-13-generic
-rw-r--r-- 1 root root   926513 Oct  1 17:08 abi-3.8.0-32-generic
-rw-r--r-- 1 root root   141616 Oct  7  2011 config-3.0.0-12-generic
-rw-r--r-- 1 root root   168533 Oct  9 11:45 config-3.11.0-12-generic
-rw-r--r-- 1 root root   168537 Oct 23 13:00 config-3.11.0-13-generic
-rw-r--r-- 1 root root   160909 Oct  1 17:08 config-3.8.0-32-generic
drwxr-xr-x 3 root root     4096 Aug 28  2012 extlinux
drwxr-xr-x 5 root root     4096 Oct 26 23:51 grub
-rw-r--r-- 1 root root 28416717 Oct 10 12:59 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root 24548221 Oct 25 09:23 initrd.img-3.11.0-12-generic
-rw-r--r-- 1 root root 24548820 Oct 26 23:51 initrd.img-3.11.0-13-generic
-rw-r--r-- 1 root root 31133475 Oct 17 18:06 initrd.img-3.8.0-32-generic
-rw-r--r-- 1 root root   176500 Jun 17 04:52 memtest86+.bin
-rw-r--r-- 1 root root   178680 Jun 17 04:52 memtest86+_multiboot.bin
-rw------- 1 root root  2130938 Oct  7  2011 System.map-3.0.0-12-generic
-rw------- 1 root root  2621091 Oct  9 11:45 System.map-3.11.0-12-generic
-rw------- 1 root root  2621288 Oct 23 13:00 System.map-3.11.0-13-generic
-rw------- 1 root root  2445627 Oct  1 17:08 System.map-3.8.0-32-generic
-rw------- 1 root root     1215 Oct  7  2011 vmcoreinfo-3.0.0-12-generic
-rw------- 1 root root  4632128 Oct  7  2011 vmlinuz-3.0.0-12-generic
-rw------- 1 root root  5632848 Oct  9 11:45 vmlinuz-3.11.0-12-generic
-rw------- 1 root root  5633040 Oct 23 13:00 vmlinuz-3.11.0-13-generic
-rw------- 1 root root  5375088 Oct  1 17:08 vmlinuz-3.8.0-32-generic
```

With those four items, there's a good chance we can help you diagnose and fix the problem.

---

### Post by TomBrooklyn on 2013-11-07
> **btindie said:**
> You'll probably just need to uninstall the old kernels. Yes, that's all I need to do.     That's why I started this thread.   To ask how to do that.

---

### Post by ian-weisser on 2013-11-07
Well, as long as you're sure that's the problem, then the solution is easy.
Just post #3 and #4 from my post above.

---

### Post by TomBrooklyn on 2013-11-07
> **btindie said:**
> provide the output of ```
df -h /boot
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       228M  226M     0 100% /boot

> **btindie said:**
> provide the output of```
dpkg-query -W -f='${Package}\n' 'linux-image-*'
```
linux-image-3.0
linux-image-3.5.0-17-generic
linux-image-3.5.0-28-generic
linux-image-3.8.0-21-generic
linux-image-3.8.0-22-generic
linux-image-3.8.0-23-generic
linux-image-3.8.0-25-generic
linux-image-3.8.0-26-generic
linux-image-3.8.0-27-generic
linux-image-3.8.0-29-generic
linux-image-3.8.0-30-generic
linux-image-3.8.0-31-generic
linux-image-extra-3.5.0-17-generic
linux-image-extra-3.5.0-28-generic
linux-image-extra-3.8.0-21-generic
linux-image-extra-3.8.0-22-generic
linux-image-extra-3.8.0-23-generic
linux-image-extra-3.8.0-25-generic
linux-image-extra-3.8.0-26-generic
linux-image-extra-3.8.0-27-generic
linux-image-extra-3.8.0-29-generic
linux-image-extra-3.8.0-30-generic
linux-image-extra-3.8.0-31-generic
linux-image-generic

---

### Post by TomBrooklyn on 2013-11-07
> **coffeecat said:**
> Post the output of these two terminal commands:
```
df -h
```
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root   35G  7.3G   26G  23% /
none                     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                     965M  4.0K  965M   1% /dev
tmpfs                    195M  892K  194M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     974M   80K  974M   1% /run/shm
none                     100M   20K  100M   1% /run/user
/dev/sda1                228M  226M     0 100% /boot


> **coffeecat said:**
> Post the output of these two terminal commands:
```
mount
```This result involves security and is thus not suitable for posting

---

### Post by TomBrooklyn on 2013-11-07
> **ian-weisser said:**
>  Third, please try the command **uname -r  **in a terminal, and post the result here.
```
$ uname -r
```
3.8.0-29-generic

> **ian-weisser said:**
>  Finally, please try the command **ls -l /boot** (those are lowercase Ls) in a terminal, and paste the result here inside code tags.
```
total 224260
-rw-r--r-- 1 root root   852490 Apr 23  2013 abi-3.5.0-28-generic
-rw-r--r-- 1 root root   918917 May 14 18:42 abi-3.8.0-21-generic
-rw-r--r-- 1 root root   919039 May 16 11:42 abi-3.8.0-22-generic
-rw-r--r-- 1 root root   919039 May 29 16:48 abi-3.8.0-23-generic
-rw-r--r-- 1 root root   919001 Jun  6 17:16 abi-3.8.0-25-generic
-rw-r--r-- 1 root root   919001 Jun 17 18:09 abi-3.8.0-26-generic
-rw-r--r-- 1 root root   919493 Jul  8 20:46 abi-3.8.0-27-generic
-rw-r--r-- 1 root root   919604 Aug 13 16:10 abi-3.8.0-29-generic
-rw-r--r-- 1 root root   919661 Aug 22 17:21 abi-3.8.0-30-generic
-rw-r--r-- 1 root root   919745 Sep 10 16:29 abi-3.8.0-31-generic
-rw-r--r-- 1 root root   148096 Apr 23  2013 config-3.5.0-28-generic
-rw-r--r-- 1 root root   154942 May 14 18:42 config-3.8.0-21-generic
-rw-r--r-- 1 root root   154943 May 16 11:42 config-3.8.0-22-generic
-rw-r--r-- 1 root root   154943 May 29 16:48 config-3.8.0-23-generic
-rw-r--r-- 1 root root   154943 Jun  6 17:16 config-3.8.0-25-generic
-rw-r--r-- 1 root root   154945 Jun 17 18:09 config-3.8.0-26-generic
-rw-r--r-- 1 root root   154960 Jul  8 20:46 config-3.8.0-27-generic
-rw-r--r-- 1 root root   154960 Aug 13 16:10 config-3.8.0-29-generic
-rw-r--r-- 1 root root   154960 Aug 22 17:21 config-3.8.0-30-generic
-rw-r--r-- 1 root root   154960 Sep 10 16:29 config-3.8.0-31-generic
drwxr-xr-x 5 root root     1024 Aug 27 02:03 grub
-rw-r--r-- 1 root root 16087977 May 19 17:38 initrd.img-3.5.0-28-generic
-rw-r--r-- 1 root root 16798170 May 19 18:00 initrd.img-3.8.0-21-generic
-rw-r--r-- 1 root root 16797380 May 24 23:57 initrd.img-3.8.0-22-generic
-rw-r--r-- 1 root root 16798391 Jun  2 13:11 initrd.img-3.8.0-23-generic
-rw-r--r-- 1 root root 16800135 Jul  6 03:04 initrd.img-3.8.0-25-generic
-rw-r--r-- 1 root root 16800891 Jul  6 03:05 initrd.img-3.8.0-26-generic
-rw-r--r-- 1 root root 16863463 Aug  7 05:48 initrd.img-3.8.0-27-generic
-rw-r--r-- 1 root root 16862084 Aug 27 02:03 initrd.img-3.8.0-29-generic
drwxr-xr-x 2 root root    12288 Apr  2  2013 lost+found
-rw-r--r-- 1 root root   176764 Dec  5  2012 memtest86+.bin
-rw-r--r-- 1 root root   178944 Dec  5  2012 memtest86+_multiboot.bin
-rw------- 1 root root  2901505 Apr 23  2013 System.map-3.5.0-28-generic
-rw------- 1 root root  3060094 May 14 18:42 System.map-3.8.0-21-generic
-rw------- 1 root root  3060454 May 16 11:42 System.map-3.8.0-22-generic
-rw------- 1 root root  3060454 May 29 16:48 System.map-3.8.0-23-generic
-rw------- 1 root root  3060761 Jun  6 17:16 System.map-3.8.0-25-generic
-rw------- 1 root root  3060957 Jun 17 18:09 System.map-3.8.0-26-generic
-rw------- 1 root root  3061544 Jul  8 20:46 System.map-3.8.0-27-generic
-rw------- 1 root root  3062491 Aug 13 16:10 System.map-3.8.0-29-generic
-rw------- 1 root root  3062704 Aug 22 17:21 System.map-3.8.0-30-generic
-rw------- 1 root root  3062541 Sep 10 16:29 System.map-3.8.0-31-generic
-rw------- 1 root root  5130128 Apr 23  2013 vmlinuz-3.5.0-28-generic
-rw------- 1 root root  5356592 May 14 18:42 vmlinuz-3.8.0-21-generic
-rw------- 1 root root  5356688 May 16 11:42 vmlinuz-3.8.0-22-generic
-rw------- 1 root root  5356656 May 29 16:48 vmlinuz-3.8.0-23-generic
-rw------- 1 root root  5357392 Jun  6 17:16 vmlinuz-3.8.0-25-generic
-rw------- 1 root root  5355920 Jun 17 18:09 vmlinuz-3.8.0-26-generic
-rw------- 1 root root  5359184 Jul  8 20:46 vmlinuz-3.8.0-27-generic
-rw------- 1 root root  5360272 Aug 13 16:10 vmlinuz-3.8.0-29-generic
-rw------- 1 root root  5361936 Aug 22 17:21 vmlinuz-3.8.0-30-generic
-rw------- 1 root root  5362320 Sep 10 16:29 vmlinuz-3.8.0-31-generic
```

---

### Post by ian-weisser on 2013-11-07
Open a terminal and try each of the following commands. Each should remove an old kernel:
If you get an error, stop and show it to us. There are other ways to remove old kernels depending upon the error.
```
sudo apt-get remove linux-image-3.5.0-17-generic
sudo apt-get autoremove linux-image-3.5.0-28-generic
sudo apt-get autoremove linux-image-3.8.0-21-generic
sudo apt-get autoremove linux-image-3.8.0-22-generic
sudo apt-get autoremove linux-image-3.8.0-23-generic
sudo apt-get autoremove linux-image-3.8.0-25-generic
sudo apt-get autoremove linux-image-3.8.0-26-generic
sudo apt-get autoremove linux-image-3.8.0-27-generic
sudo apt-get autoremove linux-image-3.8.0-30-generic
sudo apt-get autoremove linux-image-3.8.0-31-generic
sudo apt-get update && sudo apt-get upgrade

```
The "autoremove" cleans out any orphaned (obsolete) dependency packages.
The final command simply updates your system, and coincidentally shows that your package manager is working properly again.
Do NOT remove linux-image-3.8.0-29-generic. Your system is using it!

Here is an example of what happens when you run one of those commands.
On my system, this command took about 20-30 seconds to complete.
```
$ sudo apt-get autoremove linux-image-3.0.0-12-generic 
[sudo] password for ian:          (THE CURSOR WON'T MOVE)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.0.0-12-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 117 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 331203 files and directories currently installed.)
Removing linux-image-3.0.0-12-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
run-parts: executing /etc/kernel/prerm.d/last-good-boot 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by TomBrooklyn on 2013-11-11
> **ian-weisser said:**
> Open a terminal and try each of the following commands. Each should remove an old kernel:How about if I used the Synapic Package Manager.   I came across that idea while I was waiting for your response in this thread and I installed it.     It is a GUI program that removes multiple kernels at one time, I think.

---

### Post by ian-weisser on 2013-11-11
Synaptic is a great way to do it. Lots of great ways to do it.

The first time, I recommend removing one old kernel...a test.
If the test works, then remove the rest at once, sure.

Er, be *really* sure you don't erroneously remove your current running kernel, but you knew that already.

---

