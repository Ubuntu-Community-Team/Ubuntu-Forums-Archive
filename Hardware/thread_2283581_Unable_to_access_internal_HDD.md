---
title: "Unable to access internal HDD"
date: 2015-06-22
forum: Hardware
---

### Post by xwitthus34 on 2015-06-22
Background: Hey guys, I'm new here. Recently my windows computer was corrupted and I read that the process to follow would be to boot linux (I used ubuntu), backup my files on my internal HDD onto an external drive, and proceed to reinstall windows from there.

Problem: I have used a Live USB to boot linux, and whenever I attempt to access the internal HDD, i get the following error:
'Unable to access Windows8_OS"
Error mounting /dev/sdb5 at /media/ubuntu/Windows8_OS1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sdb5" "/media/ubuntu/Windows8_OS1"' exited with non-zero exit status 18: Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sdb5': No such file or directory

Any ideas?? Thanks in advance. Also, ubuntu is really nice!!!

---

### Post by veddox on 2015-06-23
Glad to hear that you like Ubuntu :-) And welcome to the Forum!

To be able to help you better, we need a bit more information. So here are a few questions:

What do you mean when you say that your computer was "corrupted"? How did that manifest itself? Are you still able to boot Windows?
How did you try to access the HDD from Ubuntu? Did you just click on it in Nautilus (the file manager), or did you use the terminal?
How is your computer partitioned?

---

### Post by Bucky Ball on 2015-06-23
Yep, your Win8 disk is in hibernate. That's the way they like it! You'll need to jump through some hoops to get into it, but that is your issue I would imagine. Unless you have manually set it NOT to hibernate in Win8 itself, then that's probably it. You could try switching off the computer, reboot to the BIOS, switch of 'fast start' and any other Win-centric settings, reboot and try again. 

Other than that, research getting into a crashed Win disk that is stuck in hibernate mode and ways to 'unhibernate' it. You should find plenty as this is not an uncommon issue round and elsewhere.

If you can boot Windows, search for how to switch off hibernate from a running Win install. They'd be users here who would know how to fix this in a jiffy I would think and I have high hopes one of them will leap in eventually. 

Good luck.

PS: If you can boot Win, I did find this:

> To make hibernation unavailable, follow these steps:

    Click Start, and then type cmd in the Start Search box.
    In the search results list, right-click Command Prompt, and then click Run as Administrator.
    When you are prompted by User Account Control, click Continue.
    At the command prompt, type powercfg.exe /hibernate off, and then press Enter.
    Type exit, and then press Enter to close the Command Prompt window.

To make hibernation available, follow these steps:

    Click Start, and then type cmd in the Start Search box.
    In the search results list, right-click Command Prompt, and then click Run as Administrator.
    When you are prompted by User Account Control, click Continue.
    At the command prompt, type powercfg.exe /hibernate on, and then press Enter.
    Type exit, and then press Enter to close the Command Prompt window. 

... from [here]("https://support.microsoft.com/en-us/kb/920730"). You might be able to do something with a Win recovery CD/DVD if you have one. I believe there's other ways, but I have no experience of Win in UEFI mode with hibernation so never had to deal with it. ;)

---

### Post by xwitthus34 on 2015-06-23
When I say that, I mean that there were some 'disk errors' according to Windows. I shut down my computer and when I attempted to boot to Windows, I was stuck in an endless boot-loop. Now I'm unable to boot :/
I did try to access the HDD using the file manager, though I tried to mount it in the terminal without success.
I hope this image helps, feel free to ask any other questions as well! Thank you so much for the reply as well

---

### Post by weatherman2 on 2015-06-23
First, make sure your hard drive isn't in fact failing.  Check its S.M.A.R.T. status.  I recommend installing GSmartControl.  You can install this in a live USB session of Ubuntu, but you have to enable the Universe repository (in Ubuntu Software Center, under Software Sources).

Anyway - install GSmartControl, then click on the Attributes tab for your hard drive.  Any Attributes highlighted in pink or red?  These are the ones to pay the most attention to.  (An Attribute marked "pre-failure" doesn't mean it is failing - that's the type of value or Attribute it is.)  You can also run S.M.A.R.T. tests with GSmartControl.  I'd run the short test - takes about two minutes.

If there are no flagged Attributes and the short S.M.A.R.T. test passes, then next I'd try running Windows chkdsk (error check) on the C: file system.  Your computer probably has a "repair your computer" menu option if you restart and hit the F8 key a few times.  You should be able to run chkdsk /f C: from a command prompt there.  Otherwise, if you have any sort of bootable Windows USB or CD, you can try to run it that way.  There may be Linux tools for trying to repair an NTFS file system but I prefer to use the native Windows tools.

---

### Post by Bucky Ball on 2015-06-23
Follow the instructions above to check if your disk is failing, but whether it is or isn't, you still want to back up those files pronto, so I'd ... 

... mount that partition in a terminal by using the following commands, one command at a time and hit enter after each:

```
sudo mkdir /mnt/Win
sudo mount /dev/sdb1 /mnt/Win
```

Open a file manager and see if you can access 'Win' or if it shows in the left panel of the file manager.

My money is still on the fact it is hibernated, but let's see ... :)

PS: I get it now. This:

```
Error mounting /dev/sdb5 at /media/ubuntu/Windows8_OS1
```

... from your first post, indicates you may have tried to mount it via a terminal and it's failed. Please include what you've attempted (particularly any commands you tried). It will save time. :)

You've tried to mount sdb5. From your screenshot you have the first partition marked and it is NTFS and that is sdb1. The rest is a bit hard to read.

---

### Post by xwitthus34 on 2015-06-23
I tried to find more info, and have found that my partition is listed as RAW

---

### Post by yancek on 2015-06-23
> found that my partition is listed as RAW 		

Where?  From your Ubuntu system?  Have you been able to boot windows, installed or Recovery.  Windows doesn't recognize Linux filesystems and that is common if seen from windows.  You haven't posted the information requested above.

---

### Post by xwitthus34 on 2015-06-23
I performed the S.M.A.R.T. test and looked at the Attributes tab for my HDD in GSmartControl and everything checks out. I have also performed a chkdsk /f C: command and have discovered that my HDD is locked. I'll be able to link the rest of the drive partitioning in an hour, lol.
Unfortunately, I can't remember much of the commands I've tried because I have done so much in the past 2 days. If it helps, my HDD is locked and can't be accessed in windows recovery either.

---

### Post by Bucky Ball on 2015-06-24
> **xwitthus34 said:**
> I have also performed a chkdsk /f C: command and have discovered that my HDD is locked.

Yea, it's in hibernate. I get the doughtnuts!!! :)

---

