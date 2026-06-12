---
title: "Blank Screen After Installation"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by owyzzz on 2009-11-01
Hi All,

I have a problem installing Ubuntu 9.10 in my Compaq Presario laptop. These are the specs of my laptop:

------------------
System Information
------------------

   Operating System: Windows Vista™ Home Premium (6.0, Build 6002) Service Pack 2 (6002.vistasp2_gdr.090803-2339)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: Compaq Presario CQ61 Notebook PC
               BIOS: Default System BIOS
          Processor: Genuine Intel(R) CPU           T1600  @ 1.66GHz (2 CPUs), ~1.7GHz
             Memory: 1978MB RAM
          Page File: 1476MB used, 2723MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6001.18000 32bit Unicode


---------------
Display Devices
---------------
        Card name: Mobile Intel(R) 4 Series Express Chipset Family
     Manufacturer: Intel Corporation
        Chip type: Mobile Intel(R) 4 Series Express Chipset Family
         DAC type: Internal
       Device Key: Enum\PCI\VEN_8086&DEV_2A42&SUBSYS_3069103C&REV_07
   Display Memory: 797 MB


I'm planning a dual boot OS for my laptop. I have already parted a space (40GB) for Ubuntu using Windows Vista. Then I downloaded the latest version of Ubuntu (filename-ubuntu-**9.10-desktop-i386**) and then burned it on a cd. My first problem has something to do with burning the cd, but I found that the solution that is to burn at the slowest possible burning speed. So starting up, I changed the priority level of disc devices in BIOS. It set the CD-ROM at the top of the list. Then came the Ubuntu cd menu. Here's the problem:

a.) I first chose "Try Ubuntu with out changes..." just to try and see it and then, the screen went plain black. I waited for 30 minutes and still nothing happened.

b.) I then tried to choose "Install" then the screen again went black. It didn't install--think there was an error message.

c.) Now I tried using WUBI and it did install. And so after installing, and rebooting, came the boot OS menu, I chose Ubuntu but the screen went black. I waited for 20 minutes and it rebooted on its own. Came again the boot OS menu, I chose Ubuntu again and the screen went black again. I waited for another 20 minutes and nothing happened. 

d.) Now I formatted the Ubuntu partition and downloaded the former version 9.04 (**ubuntu-9.04-desktop-i386**), then burned in a cd. And did the same thing again. Then I reformatted again and downloaded the WUPI for 9.04 and successfully installed, but the screen went black again after choosing Ubuntu in the boot OS menu. What happened was just like in a.) b.) and c.)

e.) Just this morning, I found out about the alternate installer. I downloaded it **(karmic-alternate-i386**) and burned in a CD (because it cannot be installed using WUPI, correct me if I'm wrong) and installed. After placing all the needed info in the fields, it was successfully installed. It then rebooted, and then I choose again Ubuntu in the boot OS menu (GRUB) and the screen went black again.. :(  

I am able to install successfully Ubuntu but after choosing Ubuntu from the boot OS menu, the screen is going plain black blank. I'm really tired and stuck at this moment trying to install this OS. I really wanted to use this though since it was recommended to me by a colleague. Anybody knows how to solve this? I appreciate any helps. Thanks for viewing.

Regards,

Jan

---

### Post by mnmallik on 2009-11-01
I see the same issue on my macbook here are the specs

Model Name:	MacBook
  Model Identifier:	MacBook3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	4 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MB31.008E.B02
  SMC Version (system):	1.24f2

I tried 9.10 desktop, alternal iso and also 9.04 desktop and alternate iso. can some body please help.

I created a partition with bootcamp and used refit to multiple boot between mac and ubuntu. 

Thanks in advance for your help.

---

### Post by kammce on 2009-11-22
I am a novice in ubuntu but I will see what I can do. When you popped in the ubuntu CD and selected the "try without changes to your computer" option, did you see the splash screen or did the monitor immitatally become black after you selected this option? Can you still boot up from Vista or did you format your whole hard drive? Lastly, have you tried to select and boot from Ubuntu's recovery mode from the boot loader GRUB?

---

