---
title: "(Unique*) UEFI being a pain stopping successful restart afer install"
date: 2014-05-25
forum: Hardware
---

### Post by dani6 on 2014-05-25
Hi I have a slight problem getting my install to work, it is installed on to my hard drive, i can load from my hard drive but only in legacy. My HP pavillion has two possible boot orders uefi and legacy, uefi is preferred but i cant boot from the hard drive in this list of boot options. My install works to finished when i restart but i can only figure it isn't completing the process because i'm having to interrupt the restart, watching the install files it looks like everythings in there grub etc and when trying to reinstall i am having to watch it delete it all to re-install again 
  Sorry if this is worded extremely badly just woke up after a night of drinking and watching multiple installs   THANKS FOR READING :~)

---

### Post by dani6 on 2014-05-25
Any help would be appreciated WINDWS AND BILL GATES ARE DRIVING ME MAD, i was happily married to ubuntu 11.10 on my last machine for years and have grown very accustomed to it comared to gimmicky windows 8.1

---

### Post by grahammechanical on 2014-05-25
Please read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It is very hard to identify what you are trying to do and what is going wrong. 

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> [FONT=inherit]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[FONT=inherit][/FONT][/FONT]

[*=left]Then:[FONT=inherit][/FONT][FONT=inherit][/FONT]
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu"
[/LIST]
[/LIST]


Regards.

---

### Post by oldfred on 2014-05-26
Post link to BootInfo report from Boot-Repair, so we can see details.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Another HP user posted this:
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

