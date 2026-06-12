---
title: "Basic question: how do I get to terminal window from Live CD?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by angus1000 on 2009-05-20
I am in the process of trying to dual boot Ubuntu 9.04 and Windows 7.
 
I've done the following:
 
1. Installed Ubuntu
2. Set up new partition for Windows 7 with gparted
3. Installed Windows 7
 
Right now when I boot my machine it boots into Windows 7. So, I am following some suggestions I've seen on the web to restore my MBR via GRUB. I'm told that I can boot the Ubuntu Live CD and install GRUB from the terminal.
 
I'm embarrassed to ask this, but how do I get to the terminal?
 
When I boot the Live CD I see the options:
 
1. Try Ubuntu without any change to your computer
2. Install Ubuntu
3. Check for disk defects
4. Test memory
5. Boot from first hard disk
 
Any help will be appreciated.
 
Thanks,
Angus

---

### Post by lisati on 2009-05-20
If you choose "Try ubuntu without any change to your computer" you will be able to use the Applications->Accesories->Terminal for a command line interfiace.

---

### Post by angus1000 on 2009-05-20
Thanks, I just figured this out as well. I was able to
"sudo grub"
grub > find /boot/grub/stage1
 
however it then says to go to terminal from normal ubuntu and type:
 
"sudo gedit /boot/grub/menu.lst"
 
I guess now it is a reboot of my PC into Ubuntu before I can actually do the editing?

---

