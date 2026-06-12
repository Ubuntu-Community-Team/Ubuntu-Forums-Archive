---
title: "Turn off unnecessary laptop devices"
date: 2010-10-30
forum: Hardware
---

### Post by ario on 2010-10-30
Hi guys,
I have an acer Aspire 5536 laptop. I want to turn of all it's unnecessary devices to reduce power consumption. I'm already using cpu frequency applet in gnome and Ati Radeon HD3200 propriety driver to reduce power consumption of these components successfully.
I'm also using network-manager applet to turn off wireless and LAN. This will reduce about 2 Watts of power consumption as well.
Now I need to know how to turn off following devices:
[LIST=1]
[*]Webcam (It's internal but I can see it on **lsusb** list)
[*]Sound Chipset (Who needs to listen to music using laptop battery?)
[*]DVD drive (It automatically goes standby but not sleep mode)
[*]Internal Dial-Up modem
[*]Hard Drive (It's always in active/idle mode in **hdparm -C** command)
[/LIST]
I think by turning those things off I can reduce about 5 watts of laptop power which increases life time on battery about 1 hour! I need it guys. Guess a lot of people out there too. So please help me figure it out how to turn them off in Linux.
Thank a lot:)

---

### Post by IcarusR on 2010-10-30
Can any of this hardware be switched off in the bios ?
If not you could unload the relevant module for webcam & sound so they will not work.
To prevent them from loading at boot the modules need to be added to /etc/modprobe.d//blacklist.conf

Some soundcards have power saving options in the module.

At a guess the dialup modem is not in use as they tend not to be setup by default.

No ideas on the DVD or HDD

Have you tried using powertop to help reduce power consumption.

---

### Post by ario on 2010-10-30
> **IcarusR said:**
> Can any of this hardware be switched off in the bios ?Obviously not! Also I prefer to do that by software.> 
If not you could unload the relevant module for webcam & sound so they will not work.Will this turn them off as well? The only important thing for me here is to reduce power consumption. Not just disabling something for example for security reasons.> 
To prevent them from loading at boot the modules need to be added to /etc/modprobe.d//blacklist.confNo this is not needed. I can add some modprobe -r commands to a script which runs whenever laptop goes on battery.> 

Some soundcards have power saving options in the module.
Also I ran powertop. Which suggested me to press <A> to let it disable sound chipset. But although I were root, it couldn't do that and used to prompt me again and again to press the <A> key! Don't know why.>  
At a guess the dialup modem is not in use as they tend not to be setup by default.
But they are still pci devices and using a bit of battery power. Aren't they?> 
No ideas on the DVD or HDD
For HDD I used **hdparm -B1 /dev/sda** to let it spin down. But didn't use -S parameter as well, because my WD Caviar Hard Drive wont accept any timeout value from hdparm and sticks to a default value of 5 seconds. I don't know why!> 
Have you tried using powertop to help reduce power consumption.
Of course I did. That sometimes reduced about 1 watts. But definitely need more than that.
By the way, thanks for your helpful tips. Any other ideas will be appreciated as well:)

---

### Post by ario on 2010-11-09
I think I can not reduce more of my laptops power consumption in Linux that I do already.
Thanks.

---

