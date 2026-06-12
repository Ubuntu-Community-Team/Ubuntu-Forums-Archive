---
title: "Acer Aspire One - Screen goes black after install."
date: 2012-05-01
forum: Hardware
---

### Post by aeliz on 2012-05-01
I have an Acer Aspire One laptop. A0751h-1392. Model #ZA3. 

I downloaded ubuntu-12.04-desktop-i386.iso and made a bootable USB stick using UNetbootin. While installing Ubuntu it shows only half of the screen. After getting it to install it goes black. If I reboot it starts up and goes to purple before turning black. And then it just stays black. I asked for help in #Ubuntu on IRC and someone told me that it could be from the video card. He helped me update GRUB. In the terminal he said to write:

gksu gedit /etc/default/grub

I put my password and then the text editor appeared. He told me to comment by adding # in front of GRUB_CMDLINE_LINUX_DEFAULT. 

Then I added the line: GRUB_CMDLINE_LINUX_DEFAULT="poulsbo.blacklist=yes console=tty1" Then saved and closed it. 

In the terminal screen I added: sudo update-grub

After saving and rebooting it still had the same problem with loading just a purple screen and then back to black. 

I'm completely new to Linux. If anyone can help me, I would really appreciate it. I'm still confused about terminology and commands.

---

### Post by prince_of_death on 2012-05-02
Hello and welcome to Linux. I remember my first time trying to install Ubuntu on the same net-book as you. In face that's what i'm using right now with Ubuntu 12.04. I'll try to walk you through the steps as much as i can. 
When you power on the netbook and it goes to the black screen wait a few seconds for it to fully load then press Ctrl+Alt+F1. This will switch you to a terminal like screen. Type your user name and press "Enter" then type your password. Next type this command and press Enter "sudo service lightdm restart"
This will now load your desktop but this is only temporary and will have to be done every time you boot. To make this permanent you have to edit your grub. Now that you are at your desktop press Ctrl+Alt+t to open a terminal and enter these commands 
"gksudo gedit /etc/default/grub"
After entering your password a text fill will open. Find this line "GRUB_CMDLINE_DEAULT="quiet splash" and change it to look like this "GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb"
Now save and close the file. After that enter this command in the terminal "sudo update-grub"
After that is finished reboot and if you did everything exactly as said your netbook will boot perfectly. No more black screen

---

### Post by aeliz on 2012-05-03
It worked!!!

Thank you so much! I was thinking it wasn't possible to have Ubuntu on my laptop. Several people tried to help me, but nothing worked. Now it boots up and I have a desktop. :D

I really appreciate the help.

---

### Post by carni91 on 2012-05-10
I am new to Linux.

For some reason I cannot install Ubuntu to the same type of Acer, I get Errno 30 when installing. I run the install off the "Try Ubuntu without installing" and I run the installation of a FAT32 Sandisk Cruzer with unetbootin. I managed to install Android x86 on the Acer but it shot the same errors until I created two partitions on the same drive with gparted, those partitions being a NTFS (empty) and a ext3 partition (Android x86). Although possibly the solution to my problem this is bothersome since I wish to allocate the entire disk to Ubuntu.

What am I doing wrong?

At the moment I am going to attempt to create the smallest possible NTFS partition on the drive and then a ext4 partition with the rest of hard drive.

Did not work... using ubuntu 12.04 alternative, and then UBCD to check HDD.

---

### Post by carni91 on 2012-05-10
Faulty hard drive. Removed 2gb RAM disk and trashed the computer.

---

### Post by heik on 2012-06-06
Many thanks for this. This helps me to see my Desktop and no Black screen after installing Ubuntu to my Acer Aspire One (ZA3)

---

### Post by heik on 2012-06-06
> **prince_of_death said:**
> Hello and welcome to Linux. I remember my first time trying to install Ubuntu on the same net-book as you. In face that's what i'm using right now with Ubuntu 12.04. I'll try to walk you through the steps as much as i can. 
When you power on the netbook and it goes to the black screen wait a few seconds for it to fully load then press Ctrl+Alt+F1. This will switch you to a terminal like screen. Type your user name and press "Enter" then type your password. Next type this command and press Enter "sudo service lightdm restart"
This will now load your desktop but this is only temporary and will have to be done every time you boot. To make this permanent you have to edit your grub. Now that you are at your desktop press Ctrl+Alt+t to open a terminal and enter these commands 
"gksudo gedit /etc/default/grub"
After entering your password a text fill will open. Find this line "GRUB_CMDLINE_DEAULT="quiet splash" and change it to look like this "GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb"
Now save and close the file. After that enter this command in the terminal "sudo update-grub"
After that is finished reboot and if you did everything exactly as said your netbook will boot perfectly. No more black screen

Thank you very much… It works perfectly (Acer Apire One ZA3). No Black screen anymore…
You are the Champ:)

---

### Post by heik on 2012-06-06
Now there is another Problem. If i bring the system to sleep mode…

The Screen stays black after awake from sleep mode. 

Any Ideas ?

Best regards heik.

---

### Post by richdell on 2012-08-06
I'm having a similar problem: when I type "gksudo gedit /etc/default/grub" the text editor does not show up, there is a pause, then the terminal goes back to the prompt. I have Grub2.

Opps, I found out I need to install gedit, sorry

---

### Post by robinelizabeth on 2012-09-08
> **prince_of_death said:**
> Hello and welcome to Linux. I remember  my first time trying to install Ubuntu on the same net-book as you. In  face that's what i'm using right now with Ubuntu 12.04. I'll try to walk  you through the steps as much as i can. 
When you power on the netbook and it goes to the black screen wait a few  seconds for it to fully load then press Ctrl+Alt+F1. This will switch  you to a terminal like screen. Type your user name and press "Enter"  then type your password. Next type this command and press Enter "sudo  service lightdm restart"
This will now load your desktop but this is only temporary and will have  to be done every time you boot. To make this permanent you have to edit  your grub. Now that you are at your desktop press Ctrl+Alt+t to open a  terminal and enter these commands 
"gksudo gedit /etc/default/grub"
After entering your password a text fill will open. Find this line  "GRUB_CMDLINE_DEAULT="quiet splash" and change it to look like this  "GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_backlight=vendor  acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb"
Now save and close the file. After that enter this command in the terminal "sudo update-grub"
After that is finished reboot and if you did everything exactly as said  your netbook will boot perfectly. No more black screen


It won't let me enter in my password? Then says login fail.

---

### Post by cortman on 2012-09-08
> **robinelizabeth said:**
> It won't let me enter in my password? Then says login fail.

FYI, It's usually best to start your own thread when you have an issue.
You do know that it won't show any characters when you type your password, right? What you type still applies.

---

### Post by NikosV on 2012-09-28
> **prince_of_death said:**
> Hello and welcome to Linux. I remember my first time trying to install Ubuntu on the same net-book as you. In face that's what i'm using right now with Ubuntu 12.04. I'll try to walk you through the steps as much as i can. 
When you power on the netbook and it goes to the black screen wait a few seconds for it to fully load then press Ctrl+Alt+F1. This will switch you to a terminal like screen. Type your user name and press "Enter" then type your password. Next type this command and press Enter "sudo service lightdm restart"
This will now load your desktop but this is only temporary and will have to be done every time you boot. To make this permanent you have to edit your grub. Now that you are at your desktop press Ctrl+Alt+t to open a terminal and enter these commands 
"gksudo gedit /etc/default/grub"
After entering your password a text fill will open. Find this line "GRUB_CMDLINE_DEAULT="quiet splash" and change it to look like this "GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb"
Now save and close the file. After that enter this command in the terminal "sudo update-grub"
After that is finished reboot and if you did everything exactly as said your netbook will boot perfectly. No more black screen

I am trying to install on the same netbook. Evrething seems to be correct until the moment i switced it of and restarted it. It will not boot unless I have the USB attached. I have changed the BIOS configuration but no luck. It denies to start up. I have only a blinking dash on the screen and nothing else. On the netbook I have installed the ubuntu 12.04 without keeping any other operating system. Any ideas? Thanks

---

### Post by ssands10 on 2012-11-01
Hi Prince of Death, I too have an Aspire AO751H and have the black screen from upgrading the OS.  I tried your suggestion to restart the service lightdm and it responded with lightdm not found.  May I have another suggestion?  Thank you.

---

### Post by whiliq on 2012-11-11
Thank you so much! :) It worked..

---

### Post by aiden707 on 2013-02-15
Hi i have followed all the instructions from prince of death, but even after saving in gedit when i reboot it is still the black screen that needs comand sudo service lightdm restsart.
any ideas to fix this plaese?

---

