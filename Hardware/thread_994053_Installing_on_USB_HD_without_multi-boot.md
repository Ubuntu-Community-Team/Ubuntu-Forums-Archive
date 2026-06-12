---
title: "Installing on USB HD without multi-boot"
date: 2008-11-26
forum: Hardware
---

### Post by CrunchyDoodle on 2008-11-26
I wish to set up ubuntu 8.10 on a USB hard drive that is stand-alone. That is, I do not want to have GRUB on the XP internal drive. The way I did this before was to remove the hard drive from the external USB case and install it in place of the XP internal hard drive and perform a normal ubuntu installation. I then edited the GRUB menulist to reflect the subtle, but necessary change in the name of the soon-to-be-a-USB-drive-again. I then put the ubuntu HD back into the USB case and put back the XP HD. To boot up ubuntu, I simply plugged in the ubuntu USB drive and power up the notebook. I then pressed F11 to get into the notebook's boot device menu and selected the ubuntu USB HD. It would then boot into ubuntu as expected.

I just got a new MSI netbook and want to set up the same thing for it with ubuntu 8.10. However, I'm reluctant to break the warranty seal to do that. 

What I did do was perform a regular ubuntu install on the USB hard drive which put GRUB on the internal XP HD. I then used the XP Recovery Console to restore the original XP boot stuff, so it would boot into XP as usual without the USB drive present.

So, how do I fix the now ubuntu 8.10 USB drive so the GRUB is local to it and I can just select it as the boot device in the machine BIOS?

Bye.   :cool:

---

### Post by CrunchyDoodle on 2008-11-27
I did some digging in the ubuntu documentation and got lucky. I found the exact solution in the manual for GRUB:

[FONT="Fixedsys"][COLOR="Blue"]You can try re-installing the grub using the Ubuntu Live CD, in two different ways. 

GUI
Boot your computer up with Ubuntu CD 
Go through all the process until you reach "[!!!] Disk Partition" 
Select Manual Partition 
Mount your appropriate Linux partitions  / /boot swap .....  

DO NOT FORMAT THEM. 

Finish the manual partition 
Say "Yes" when it asks you to save the changes 
It will give you errors saying that "the system couldn't install ....." after that 
Ignore them, keep select "continue" until you get back to the Ubuntu installation menu 
Jump to "Install Grub ...." 
Once it is finished, just restart your computer 

Command line
Boot your computer up with Ubuntu CD 
Open a terminal window or switch to a tty. 
Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary. 

Type "grub" 
Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines. 
Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu. 
Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition. 
Quit grub by typing "quit". 
Reboot and remove the bootable CD.[/COLOR][/FONT] 

I used the second method from inside a Terminal Window. The USB drive turned out to be (hd1,0), so that's what I used for the suggested commands. Since this USB hard drive was to be entirely used for ubuntu, I used "setup (hd1)" to install GRUB to its MBR. I now have a stand-alone USB hard drive that I can simply plug in and run ubuntu when I wish to without modifying the original XP drive.

Bye.     :cool:

---

