---
title: "Graphics Driver - What am I using?"
date: 2011-11-22
forum: Hardware
---

### Post by chesl73 on 2011-11-22
Hi all,

I have a relatively old laptop which the wife uses and I've had to rebuilt it. Instead of sticking on WinXP I decided to give Ubuntu 11.10 a try. This is working except for one fairly major point for me. When I close the laptop lid it goes into suspend as I'd want. However, it never comes out of it again and I have to do a hard-reboot. I reckon the display is not waking up again so I am trying to see if I can install a new/different graphics driver to see if this will make a difference. 
First thing I want to tell though is what driver I'm currently using? How can I tell?
The laptop is an IBM Thinkpad T41p, if I run the command: lspci | grep VGA it tells me it's an ATI Radeon RV250 (FireGL 9000).
If I go into System Settings - Additional Drivers there is nothing there at all.
If I go into System Settings - System Info - Graphics it tells me : Driver Unknown.

After Googling I can't get anywhere with this. What I'd like to know is:
1. What driver am I using now (open source one?)
2. Can I use a proprietary one (fglrx?) and if so how do I download it and install it? I've seen stuff on the web about just going to System Settings - Additional Drivers but I don't have this as an option.

Any help with the above questions and my suspend problem would be greatly appreciated.

Thanks

---

### Post by ajgreeny on 2011-11-22
With that video card you are stuck with the open source driver that you will undoubtedly already be using.

I think your problem is unlikely to be solvable, I'm afraid, just like my old laptop;  you may have to set the system to shutdown rather than suspend when you shut the lid.

---

### Post by collisionystm on 2011-11-22
This is for PowerPC but still relevant.
[https://wiki.ubuntu.com/PowerPCKnownIssues#Wont_suspend_when_you_close_the_lid](https://wiki.ubuntu.com/PowerPCKnownIssues#Wont_suspend_when_you_close_the_lid)

---

### Post by collisionystm on 2011-11-22
oh and go into your computers BIOS and power settings. Make sure S1 S3...etc. are enabled.

---

### Post by digithal on 2011-11-22
Try to boot your system with ***nomodeset*** option (which is disabling KMS) into the kernel line. Here is a quick [**how-to**]("http://ubuntuforums.org/showthread.php?t=1613132"). On my old Mobility Radeon it's doing the trick :)

---

### Post by chesl73 on 2011-11-23
> **digithal said:**
> Try to boot your system with ***nomodeset*** option (which is disabling KMS) into the kernel line. Here is a quick [**how-to**]("http://ubuntuforums.org/showthread.php?t=1613132"). On my old Mobility Radeon it's doing the trick :)
 
 
Thank You! This worked, with an addition. the **nomodeset** option by itself didn't work then I also included the option **acpi=off** and this worked a treat! 
Cheers

---

### Post by MoreOrLess on 2011-11-23
[http://www.thinkwiki.org/wiki/Category:T41p](http://www.thinkwiki.org/wiki/Category:T41p)

---

