---
title: "Acer Aspire 5 Thin Windows 10 / Ubuntu 19.10 Dual Boot - Howto"
date: 2020-02-27
forum: Hardware
---

### Post by dwentz on 2020-02-27
[COLOR=#000000][FONT=Arial]Acer Aspire 5 Thin  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Windows 10 / Ubuntu 19.10 Dual Boot[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Model A515-54-5649 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Intel Core i5-10210U Processor 1.6GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]8GB DDR4 RAM; 512GB Solid State Drive; Intel UHD Graphics 620[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I am really impressed with this laptop for the price, I picked it up at Micromart on sale for 450.00[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I am mainly a Mac and Linux guy, but I need a laptop now and then. The current Mac books just don't do it for me. And I could have purchased 4 of these for what a Mac Book would have cose.   [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I made a list of what I needed and wanted in a laptop and the only place this machine fell short was that it is missing a built-in SD card reader. A big bonus is there is also room in it for an additional 3.5' SATA SSD. I will be addint a 1TB drive to the it also.  [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This will be used for light coding development work, light 3d graphics design, and as a general purpose laptop for me. [/FONT][/COLOR]



[LIST]
[*]Setup and register your laptop as normal.
[*]Create a Windows Rescue disk
[LIST]
[*]Just in case somethign goes wrong we have a fall back position.
[*]Mine required a 16GB thumb drive.
[/LIST]

[*]Open Disk Manager and Shrink the partition.
[LIST]
[*]I shrunk my main windows partition by 150GB for my Ubuntu install.
[/LIST]

[*]Reboot to make sure everything is good.
[*]Download and create the Ubuntu install onto a USB stick.
[LIST]
[*]Remove the Ubuntu USB stick from the laptop.
[/LIST]
[/LIST]

[COLOR=#000000][FONT=Arial]The Acer ships with a PCIe NVMe SSD, and it's only boot mode is UEFI. We need to make some changes to the BIOS and Prep Windows to boot with the SSD in AHCI mode with Secure Boot turned off, which is a requirment for Ubuntu. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Before we change the BIOS setting we need to prep windows so that it will boot with Secure Boot off and using the SSD AHCI interface mode.[/FONT][/COLOR]


[LIST]
[*]From the Command Prompt
[/LIST]
[COLOR=#000000][FONT=Arial]bcdedit /set {current} safeboot minimal[/FONT][/COLOR]

[LIST]
[*]Restart the computer and enter BIOS Setup (Hit F2 during when the green Acer screen appears.
[*]Acers require a Supervisor password to be set if you turn off Secure Boot
[*]From the BIOS screen
[LIST]
[*]in the Security Section enter a Supervisor Password.
[*]In the Boot Section set Secure Boot to Disabled
[*]In the Main section be sure F12 Boot menu is set to Enabled
[*]Hit CTRL S and you should see the SATA mode appear in the menu.
[LIST]
[*]Change it from IRST with Optane to AHCI
[/LIST]

[*]Also set the Function Key Behavior to Funcion Key
[*]Set Fast Boot to Disabled
[*]Hit F10 to Save and Exit.
[/LIST]
[/LIST]

[COLOR=#000000][FONT=Arial]Your system should boot into WIndows 10 in Safe Mode. If you had set a PIN up in windows you will need to enter your password to login and not your PIN.[/FONT][/COLOR]


[LIST]
[*]Open a command prompt window in windows and enter
[/LIST]
[COLOR=#000000][FONT=Arial]bcdedit /deletevalue {current} safeboot[/FONT][/COLOR]

[LIST]
[*]Reboot the machine once more and it should start up Windows 10
[/LIST]

[COLOR=#000000][FONT=Arial]Your laptop should now be running in standard mode with Secure Boot off, and the AHCI drivers enabled.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have not noticed any performance differences in using AHCI mode from the   IRST with Optane mode.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]We are now ready to install Ubuntu alongside Windows 10 on the laptop.[/FONT][/COLOR]

[LIST]
[*]Insert the Ubuntu Thumb drive. reboot the machine,
[*]Hit the F12 key a few times at the Green Acer screen.
[*]Select Install Ubuntu
[*]Select Install alongside WIndows.
[*]Once the installation is done, you will have the option to boot into Ubuntu or to boot to the WIndows Boot Manager.
[/LIST]


[COLOR=#000000][FONT=Arial]Hope this helps you out on getting Ubuntu and Windows 10 working side by side on this laptop.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-02-28
Great tutorial! :guitar:

This machines can be fiddly to install, particularly in dual-boot with the preinstalled Windows 10.
They require several UEFI settings changed and you covered all of it. The difficulty isn't in the Ubuntu installation itself - easier then ever - but in everything you need to do before the installation.

Just a few additional comments:
> [COLOR=#000000][FONT=Arial]A big bonus is there is also room in it for an additional 3.5' SATA SSD[/FONT][/COLOR]

I think you mean 2.5" SATA (SSD or HDD) ;)


> [COLOR=#000000][FONT=Arial]We need to make  some changes to the BIOS and Prep Windows to boot with the SSD in AHCI  mode with Secure Boot turned off, which is a requirment for Ubuntu. [/FONT][/COLOR]

AHCI is a requirement indeed but disabling Secure Boot isn't, both for Windows and Ubuntu. I always suggest disabling it for convenience, especially for newbies with Nvidia graphics and Broadcom WiFi chipsets that almost always need proprietary and unsigned drivers. It's a lot more convenient to disable Secure Boot - you do it once - then to be fiddling with secure boot tools like mokutils for each and every one. But if you don't need such drivers or using virtualization (often installs virtual drivers), Secure Boot shouldn't make any difference. That is your case, the Intel Graphics runs with open-source drivers already included in the kernel. If you won't be using virtual machines then Secure Boot doesn't matter.



>  [COLOR=#000000][FONT=Arial]Before we change  the BIOS setting we need to prep windows so that it will boot with  Secure Boot off and using the SSD AHCI interface mode.[/FONT][/COLOR]

Windows will boot normally with or without Secure Boot. The AHCI part is what matters most because otherwise Windows wouldn't boot after we change the mode to AHCI. Well done in the details. This is often a hurdle that makes many people give up the dual-boot. And kudos for starting it all with the Windows Rescue disk.



> 
[LIST]
[*]Acers require a Supervisor password to be set if you turn off Secure Boot
[/LIST]


Indeed.

But this is optional: > 
[LIST]
[*]Also set the Function Key Behavior to Funcion Key
[/LIST]


Many users prefer having the other functions like the multimedia keys and that's why we see so many laptops set that way nowadays. 
If you're using software with shortcuts including the function keys then change it to the classic behavior, of course.


> 
[LIST]
[*]Set Fast Boot to Disabled
[/LIST]


Also optional but I highly recommend disabling it. It doesn't significantly slow down POST and accessing UEFI settings or one time boot menus easier.



> [COLOR=#000000][FONT=Arial]I have not noticed any performance differences in using AHCI mode from the   IRST with Optane mode.[/FONT][/COLOR]

Me neither. 
I remember reading something about Intel confirming it but I didn't pay much attention so, I can be wrong.


Lastly, if you have a similar Acer but with a brand new dGPU Nvidia, you have to do all this steps plus eventually having to boot the live session with 'nomodeset' and then make sure to select installation of third-party drivers to have the Nvidia drivers installed right away (only in newer Ubuntu releases) or, after installing the OS, boot with 'nomodeset' again and then install the drivers.

---

### Post by mörgæs on 2020-02-29
Yes, thanks for a good tutorial. 

If you mark this thread solved and link to it from [https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006) there is a better chance that people will find it.

---

