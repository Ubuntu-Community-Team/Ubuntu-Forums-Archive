---
title: "installing ubuntu"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by alcav on 2009-04-06
Hi.

I have a spare hdd in my computer which I would like to install ubuntu.At the moment it is used for backing up my main c: drive but there is lots of free space.I would be grateful if someone could offer some help on how to go about acheiving this.

TIA   Alan

---

### Post by mikewhatever on 2009-04-06
Don't know if you realize it, but the question is very general to answer. If you want help with getting, preparing the media, or installing the system particulars, just elaborate. Otherwise, read one of the installation guides.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Edit: I've looked at your past posts, and it appears that you'd successfully installed Ubuntu on the backup HDD a week ago. How is now different from then?
[http://ubuntuforums.org/showthread.php?p=7023463#post7023463](http://ubuntuforums.org/showthread.php?p=7023463#post7023463)

---

### Post by artsci2 on 2009-04-06
I'm no Ubuntu expert and do get frustrated easily. I also make mistakes. This can sometimes result in horrible results related to the install of the program that manages operating system choice (Grub) on dual-boot systems. One way around this is to just disconnect the Windows hard drive and use your second hard drive for the first Ubuntu install. When you get to the "prepare hard drive" point of the installation select "use entire disk." This will wipe the disk clean of ALL information and give you a fresh start.

After doing this install you can then re-connect your Windows Hard drive and use the computer's BIOS boot device selector. On newer machines you can just press a key during startup (F9 on my machine) and it will present a boot selection screen. Go to the menu for Hard Drive and select whichever drive you want. 

I have tried to install without loading grub when the Windows drive is still connected and am having trouble getting that to work. The "install grub" section could be improved for me if therte was a choice of "I plan to use BIOS boot selector, do not install Grub and leave the windows drive untouched"

---

