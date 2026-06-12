---
title: "Add the NVIDIA Driver for K1000M"
date: 2013-12-17
forum: Hardware
---

### Post by RichardET on 2013-12-17
I downloaded this driver from the NVIDA site - see [http://www.nvidia.com/download/driverResults.aspx/69372/en-us](http://www.nvidia.com/download/driverResults.aspx/69372/en-us) but I need to go to a command line log in with no X server running in order to install it.
The stock driver for this video card works but I do not get full use of the card.  How do I install the NVIDIA driver?

---

### Post by J_Me on 2013-12-18
The problem with manually installing nvidia drivers is that every time you upgrade/update your system you'll need to reinstall the nvidai drivers(not sure if things have changed for 13.10 so do some googling). If however when you initially installed the OS you selected to 'allow third party drivers' to be used you can goto 'additional drivers' from the menu and choose the nvidia proprietary drivers from there and updating your system won't break anything.

---

### Post by RichardET on 2013-12-18
In my system it does not allow adding drivers manually.  Also I see the issue - Ubuntu is only using the on board graphics and not the K1000M NVIDIA.  How do i do that?  is it a driver update which I can somehow force?

---

### Post by J_Me on 2013-12-18
You can manually add graphics drivers to any OS but issues happen when upgrading the kernel. Depending on your system either of these maybe possible 1- have a look at 'bumble bee' drivers, if they work for your system you'll be able to switch between different cards on the fly. 2- go into your bios and see if you can choose to enable/disable one card. Be careful with this as it may boot to a blank screen in which case you'll need to load up the drivers from the command line without the x-server running.  If your not sure on what to do post the pc model, the programs you need to get working and the output of 'lspci' Someone maybe able to help

---

### Post by RichardET on 2013-12-19
For me, if it does not work "out of the box", I will not go further;  I ordered the Windows 8 restore disks from Lenovo yesterday for $59;  I will go back to Windows host, with Ubuntu as a guest.  This way I have full access to the NVIDIA capabilities, and no other issues;  I am like the rest of you guys here - I really like Ubuntu, but for now, I will live with an MS-Lenovo solution.  

But I have been successful using Ubuntu on a Lenovo B590, which uses the on-board graphics of the third gen. core i3 and I am extremely impressed with it. 

Regarding the W530, there is a growing list of users out there who are demanding full Linux capability with it and the new W540 and eventually I am certain, these graphics drivers will improve for these type laptops on the Linux side, which are meant to be mobile workstations.

If others have more to add, feel free, but I guess I will stop with this one for now.

---

