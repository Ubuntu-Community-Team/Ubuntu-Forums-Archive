---
title: "Partitioning My Hard Drive, Ubuntu -&gt; XP"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Mandraix on 2009-07-04
I have Ubuntu currently installed as my OS, but not XP. (Due to a failed attempt at trying to get Ubuntu and XP working on the same computer.)

I'm trying to get XP and Ubuntu to both be able to run on this computer, I have *everything* from my old XP on this hard drive, accessible as a 275GB disk in my Ubuntu navigation bar.

As the computer starts, along with my Ubuntu OS option, I can see "Windows XP Media Center" and "Windows NT/2000/XP" listed as options. Upon selecting "Windows XP Media Center" I receive the following message.

[I]"Windows could not start because the following file is missing or corrupt:
Windows root>\system32\hal.dll.
Please re-install a copy of the above file."
[/I]
When I select "Windows NT/2000/XP" I'm taken to a Windows boot screen, and am given option to recover my OS:

[I]"Full System Restore (Destructive)
**Warning** This option will format your hard disk and re-install all factory-shipped files. Use this if all other options fail to restore the machine to a satisfactory condition. All your personal data files and applications will be lost."[/I]

The other option is:

[I]"Full System Restore (with Backup)
This option will move all Hard Disk contents to the "c:\My Backup" directory and install a new copy of Windows. This option preserves your existing data files, however all applications and settings will need to be reinstalled. This option requires 4GB of free Hard Disk space for the new OS."[/I]

I'm at a loss of what to do, I would like to keep my Ubuntu partition intact, while being able to use Windows for purposes at which Ubuntu can be stubborn. (Windows applications that disagree with Wine.)

Any help or suggestions is greatly appreciated.

---

### Post by merlinus on 2009-07-04
A suggestion -- run windows in VirtualBox.  THen you will never have to dual-boot again.

---

### Post by Mandraix on 2009-07-04
I'll give it a shot, thanks.

---

### Post by Mandraix on 2009-07-06
Upon further reading regarding VirtualBox, I'm not sure it's the best course of action. My intentions behind wanting to dual-boot are to use XP for my games, (StarCraft is my issue at this point in time. I also use WoW but it runs pretty well under Wine), and VirtualBox doesn't seem to be a good fit for this.

To further elaborate on my question, under the 'with Backup' selection, I'm not entirely sure what will and will not be deleted. I have a portable hard drive which I could use to back up the files myself, but the idea behind this is NOT to get rid of my Ubuntu partition.

Thanks for your time.

---

### Post by JC Cheloven on 2009-07-06
Your "windows xp media center" is your true xp installation.

Your "windows NT..." is a recovery partition. Most likely is deployed by the computer vendor, and is intended to put the computer in the brand new state. It will destroy your ubuntu install no matter if the "backup" option is selected, as windows doesn't (like to) understand linux filesystems.

As to my knowlegde, your options are:

1- Try to repair windows by all means. Try to pick up the "hal.dll" from elsewere (another win install?) as the message suggests. Or if you have a true windows disk, try choosing the option "repair an existing installation" or similar.

2a- Go through the hell of reinstalling windoze. You can use the recovery partition for that. Then you can reinstall ubuntu, which is not so much pain if you don't have a lot of configuration. OR:

2b- Go through the hell of reinstalling windoze, but save an image of your ubuntu partition first (only advisable if you have spent a lot of time configuring it). Later you will be (hopefully) able to restore your ubuntu as it was, perhaps changing some UUID's in /etc/fstab and /boot/grub/menu.lst. I use FSArchiver to save images of partitions, works fine for me.

---

