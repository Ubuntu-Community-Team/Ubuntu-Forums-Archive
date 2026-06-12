---
title: "Ubuntu Adata Premier Pro SP900 M.2 2280 SSD"
date: 2016-03-16
forum: Hardware
---

### Post by jiapei100 on 2016-03-16
Hello:


Did anybody test  Adata Premier Pro SP900 M.2 2280 SSD under Ubuntu 14.04.4 or Ubuntu 15.10 ?

I've got a 256Giga Adata Premier Pro SP900 M.2 2280 SSD , which is now formatted into NTFS.
When I tried to install Ubuntu 14.04.4, I got the following error message:
[IMG]http:///longervision.com/questions/UbuntuInstallation/USBStick/ADATASSDUbuntu14.04.4.jpg[/IMG]
When I tried to install Ubuntu 15.10, I got the following error message:
[IMG]http:///longervision.com/questions/UbuntuInstallation/USBStick/ADATASSDUbuntu15.10.jpg[/IMG]


Seriously have NO idea what to do NEXT... Does it have something to do with BIOS settings?

Cheers
Pei

---

### Post by ajgreeny on 2016-03-16
Tell us more about what you have done so far in a lot more detail.

How are you trying to install Ubuntu?

Have you managed to run a live Ubuntu OS from the USB or DVD that you are, I presume, using for the installation, or do you get those errors etc when you try to boot to that installation medium?

---

### Post by jiapei100 on 2016-03-16
Thank you ajgreeny. Let me explain in more details.
Before I start, please read what's posted here:
 [https://forum-en.msi.com/index.php?topic=250805.0]("https://forum-en.msi.com/index.php?topic=250805.0")
I'm using a **gt72 6qe-033us dominator pro g**

I actually tried multiple ways to install Ubuntu on this laptop, but NONE succeeded.

1) Boot into Windows 10 (UEFI), and mount Ubuntu.iso (I tried both ubuntu-14.04.4-desktop-amd64.iso and ubuntu-15.10-desktop-amd64.iso).
After the following 4 steps, I got the Error Message Dialog finally.
[IMG]http://longervision.com/questions/UbuntuInstallation/Win10/Win10_1.png[/IMG]
[IMG]http://longervision.com/questions/UbuntuInstallation/Win10/Win10_2.png[/IMG]
[IMG]http://longervision.com/questions/UbuntuInstallation/Win10/Win10_3.png[/IMG]
[IMG]http://longervision.com/questions/UbuntuInstallation/Win10/Win10_4.png[/IMG]
[IMG]http://longervision.com/questions/UbuntuInstallation/Win10/Win10_5.png[/IMG]

2) If I boot into DVD (burned with Ubuntu) or a USB stick (Bootable Ubuntu made by LinuxLive USB Creator), it will boot into UEFI Ubuntu GUI for me to select:
[IMG]http://longervision.com/questions/UbuntuInstallation/USBStick/UEFIUbuntu.jpg[/IMG]
And, if I select **Install Ubunt**, I will get the following two results respectively:
For Ubuntu 14.04.4
[IMG]http://longervision.com/questions/UbuntuInstallation/USBStick/ADATASSDUbuntu14.04.4.jpg[/IMG]
For Ubuntu 15.10
[IMG]http://longervision.com/questions/UbuntuInstallation/USBStick/ADATASSDUbuntu15.10.jpg[/IMG]

This is all what I met so far. Any suggestions?


Cheers
Pei

---

### Post by oldfred on 2016-03-16
Please attach screen shots not post in line. Not all users have high speed Internet and it may slow their system down just trying to view your thread.
Easy to attach screen shots with paper clip icon in forum's advance editor.

You first screen shots are wubi, which is not supported anymore. You need to boot flash drive or DVD.
And you proabably need boot parameters added like this nomodeset parameter which is for nVidia or AMD video.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

But some other similar systems required different parameter(s).
       
 SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by jiapei100 on 2016-03-18
Thank you so much Oldfred, Problem now solved.

I actually did 2 things:
1) add: ```
acpi=off
```
2) add: ```
intel_idle.max_cstate=0
```
at the end of the "linux" line

And, of course, for both FIRST-BOOTING and afterwards PERMANENT BOOTING.

Thank you so much...
Cheers
Pei

---

### Post by oldfred on 2016-03-18
Glad that worked & you can change to [Solved].

---

