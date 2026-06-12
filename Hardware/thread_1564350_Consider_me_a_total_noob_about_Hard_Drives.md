---
title: "Consider me a total noob about Hard Drives"
date: 2010-08-30
forum: Hardware
---

### Post by tennesseebrewer on 2010-08-30
Hello all (and especially to those who can help!)
I want to add another hard drive to my computer and install Ubuntu on it so I can have one hard drive with Microsucks Winblows (I need it to run only one program!) and one with Ubuntu. However, I have never done this before and I need a little help. I have searched the internet, but all I can find is how to add a second hard drive, format it for windows to use and so on. 

So my question is this, "After I physically put in and connect the new hard drive, what do I do?" Do I need to go into my computer's BIOS? will my computer recognize the new hard drive? Will GRUB let me choose which hard drive to boot from?

---

### Post by jerome1232 on 2010-08-30
After you plug in the new hard drive it should be automatically picked up by your BIOS. You would then run the Ubuntu installation and ensure it installs to /dev/sdb which would be the second hard drive. /dev/sda is your first hard drive with Windows so be sure not to install to that one.

I always do the partitioning myself so I'm not sure how Ubuntu's guided partitioner handles multiple disks. I would just do manual partitioning, and keep things simple set about 1 gb as swap and the rest of the disk as / (the root partition), format that / partion as ext4 and let her go.

Ubuntu will install the GRUB bootloader over your Windows one, don't worry though grub can boot both Windows and Ubuntu with no problem.



Another option to look into later down the road since you only use Windows for one application is to install Windows into a virtual machine. This allows you to essentially run Windows in a virtual pc under Ubuntu, so you don't have to reboot to access windows, the downside is it takes a bit of ommph from your computer to run two operating systems at the same time.

---

### Post by tennesseebrewer on 2010-08-30
Thank you very much! I will try to get that installed this weekend! I will also post my results! 

The program I have to run is a 3D CAD package for work that requires intensive graphics renderings. This program is called SolidWorks. It is an industry standard in the Mechanical Engineering Field. Fortunately, when they release the 2011 version, they are going to be supporting Linux installs, primarily Ubuntu, Red Hat/Fedora, and SuSE/Open SuSE. But until they release it (which they would be the first in the industry), I am stuck with Windows.

---

