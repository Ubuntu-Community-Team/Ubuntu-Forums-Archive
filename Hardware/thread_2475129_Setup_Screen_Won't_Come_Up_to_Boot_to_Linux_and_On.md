---
title: "Setup Screen Won't Come Up to Boot to Linux and Only Boots to Windows"
date: 2022-05-17
forum: Hardware
---

### Post by geeky-1 on 2022-05-17
I was given an HP Envy desktop with Windows 10 on a hard drive. I went into the BIOS/UEFI setup and changed it to show the memory for the maximum - a minute with the prompt to press Esc to go into settings. This worked so I moved the drive to the SATA_2 port and I pulled an Ubuntu UEFI SSD and data drive from a Dell desktop and hooked them up to SATA_0 and SATA_1 ports. However, after rebooting, the computer displays the screen to go into setup, but displays "keyboard error" and no matter how many times I press Esc, F12, and/or F10, it won't go into Setup, but boots into Windows. In Windows drive utility, I can a UEFI partition on the Windows drive and see the 2 Ubuntu drives.
I tried re-registering the GRUB using the procedure here [https://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](https://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot) but there is no \EFI directory, probably because it was never a dual boot system to begin with.
Also, I'm not even sure I'll be able to use Boot-Repair as I can't even get into the Setup screen to choose a different drive to boot from.

---

### Post by yancek on 2022-05-18
If you can't get into the BIOS firmware to change boot options there isn't much anyone here will be able to suggest except using another keyboard.  Do you get a specific error message.

If you have an EFI directory on the windows drive, mount it from the Ubuntu install USB and check to see if there is an Ubuntu directory there.  If not and there is no EFI partition on the Ubuntu drive, you may have installed Ubuntu in Legacy mode which means you will have to change some setting in the BIOS firmware.  If you have a Legacy install of Ubuntu with windows EFI, the Grub bootloader on Ubuntu won't boot it.  Sound like your problem is basically with your hardware (keyboard)>

---

### Post by geeky-1 on 2022-06-18
I figured out that if I disconnected my wired MS ergonomic keyboard (that worked fine on the old Dell) and reconnected the wireless MS keyboard, the keyboard error goes away. Not sure why, but the HP boot doesn't handle wired keyboards. I decided to abandon the dual boot since I'd only want to boot to Windows less than 1% of the time and figured I didn't want a second spinning drive in there I hardly use and pulled the Windows drive and put it in the old Dell. Turns out I had to load a Windows UEFI file from that drive to set it up and run (I didn't realize UEFI is from the OS and not the hardware). Also it seems the Ubuntu drive was set up legacy instead of UEFI and is why Grub would never boot to it instead of Windows. After re-configuring the HP as I preferred (with minimal wait to enter setup - fast boot) I swapped the wired keyboard back to it and will just have to keep the wireless keyboard around the next time I have to enter setup to change things.

---

### Post by yancek on 2022-06-19
If you use windows infrequently, you might try installing it in virtual software (Virtualbox, vmware, etc.) on your Ubuntu.

If you had windows intalled UEFI and Ubuntu Legacy, you could have accessed either by going into the BIOS firmware each time you wanted to change to boot a different system.  Pretty simple process.  Grub will not boot an EFI install of windows if your Linus OS using Grub is installed in Legacy mode but will boot windows if both are installed EFI.

---

### Post by geeky-1 on 2022-06-23
The problem was I couldn't get to the setup or boot options screen when I used a wired keyboard.

The Windows drive also wouldn't work in the old Dell as Windows locks itself to the hardware so didn't like being moved to another machine. I suspect trying to move it from the hard drive to a virtual drive configuration would have problems as well. So I just reformatted the Windows drive with Ubuntu and am once again a Windows-free house. When I built my first computer in 2007, I originally installed Ubuntu with Windows Vista in Virtualbox, but Windows couldn't access some peripherals (floppy drive) through Virtualbox, so gave up on that and just installed Windows on a separate drive for a dual boot.

---

### Post by yancek on 2022-06-24
>  The Windows drive also wouldn't work in the old Dell as Windows locks  itself to the hardware so didn't like being moved to another machine. 

Definitely.  Generally, when using windows you are 'licensed' to use one instance of it and it is fixed to the hardware.  If you read your windows license (license.rtf) it will tell you that.  You are allowed to install a second instance as a back up but cannot use both per the license.  I believe you can move it to another machine but need to contact them before doing so and get their 'permission'.

---

### Post by yancek on 2022-06-24
>  The Windows drive also wouldn't work in the old Dell as Windows locks  itself to the hardware so didn't like being moved to another machine. 

Definitely.  Generally, when using windows you are 'licensed' to use one instance of it and it is fixed to the hardware.  If you read your windows license (license.rtf) it will tell you that.  You are allowed to install a second instance as a back up (including on virtual software) but cannot use both per the license.  I believe you can move it to another machine but need to contact them before doing so and get their 'permission'.

---

