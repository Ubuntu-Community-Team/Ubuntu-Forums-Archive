---
title: "install winXP after ubuntu"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by aBitLater on 2009-03-02
Hello,
I have ubuntu loaded on a machine with two drives.  I put ubuntu on the 2nd drive, and if I recall correctly, I chose to have the master boot record installed on the second driver (though I seem to recall that the install confirmation listed the first drive as the location for MBR).

So, now I want to put windows on the first drive, and am afraid it will overwrite the MBR.

How can I confirm where the MBR is, and backup / restore after windows is installed?  Isn't the MBR on the boot partition? if so, I have the 'recommended' ubuntu format - one large partition for the whole disk.

---

### Post by Partyboi2 on 2009-03-02
Windows will override the mbr, but you can just boot a ubuntu live cd and restore grub. See [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") on how to.

---

### Post by aBitLater on 2009-03-03
I'm having serious problems with this.

I've started over from scratch several times, and don't know how to proceed.

My latest attempt.

1) install winxp on 1st sata drive
2) install ubuntu on 2nd sata drive - with grub on hd0 (1st drive)

Then I try the grub option for winxp, and I get
```

Windows could not start because the below file is missing or corrupt:

C:\Winnt\System32\Ntoskrnl.exe
```

my google searches reveal that this is due to a missing or corrupt boot.ini file.

So then I load the windows install disk for repair ("R" option), do a "fixboot" and "fixmbr", which gets windows to boot, but overwrites grub

Then I go to ubuntu livecd and do some grub magic, per instructions from googling, and get grub back.  But it still won't load windows, I get the same error as above.

So I tried using the windows XP bootloader by dd'g the grub mbr and copying to windows c drive and modifying the boot.ini.  When I try this option and select my ubuntu install, I only get a blank black screen that says only "GRUB" at the top... it fails to load.

Need some help!  Appreciate any pointers!  (I'm wondering if SATA is the issue here??? or is it because I want to put both operating systems on separate drives? - most of the google results seem to be geared around having windows and linux on the same hard drive)

Thanks again, in advance!

---

### Post by aBitLater on 2009-03-03
bump

---

### Post by Partyboi2 on 2009-03-03
This was taken from [[COLOR=Blue]here[/COLOR]]("http://www.computerhope.com/issues/ch000646.htm") Give it ago.

> If the ntoskrnl.exe file is corrupt or               missing this can also generate the error. To restore this file               follow the below steps.

[LIST=1]
[*]**Insert the Microsoft Windows XP CD**. Note: If you have                   a recovery CD or a restore CD and not a Microsoft Windows XP                   CD it is likely the below steps will not resolve your issue.
[*]Reboot the computer, as the computer is starting you should                   see a message to press any key to boot from the CD. When you                   see this message **press [any                   key]("http://www.computerhope.com/jargon/a/anykey.htm")**.
[*]In the Microsoft Windows XP setup menu press the R key to                   enter the recovery console.
[*]**Select the operating system** you wish to fix, and then                   **enter the administrator password**.
[*]**Type [expand]("http://www.computerhope.com/expandhl.htm") d:\i386\ntoskrnl.ex_                   c:\windows\system32**
[*]You will then be prompted if you wish to overwrite the file **type                   Y** and **press enter** to overwrite the file.
[*]**Type exit** to reboot the computer.
[/LIST]


---

### Post by aBitLater on 2009-03-04
thanks for the link.  

I did the expand command, but I still get the same error.  I might mention, that I know I am at least getting to the boot.ini in windows, because I added a line in it (when I was trying to get XP to give an option to boot linux).  

So, at grub menu I select the Windows XP option.  That brings me to boot.ini, where I have the boot.ini menu (default XP or linux).  When I select the default, or just let it auto-select on timeout, I get the ntoskrnl.exe error again.

I'll post back again with contents of boot.ini, and grub's menu.lst

---

### Post by aBitLater on 2009-03-04
I am receiving some help at linuxquestions.org.  Yet unresolved, but I thought it would be easier to refer this thread to the other...

[http://www.linuxquestions.org/questions/linux-newbie-8/cant-install-xp-and-ubuntu-on-separate-sata-drives-708855/#post3465160]("http://www.linuxquestions.org/questions/linux-newbie-8/cant-install-xp-and-ubuntu-on-separate-sata-drives-708855/#post3465160")

---

