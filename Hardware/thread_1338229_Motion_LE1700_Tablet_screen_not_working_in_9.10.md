---
title: "Motion LE1700 Tablet screen not working in 9.10"
date: 2009-11-26
forum: Hardware
---

### Post by mictho100 on 2009-11-26
Hi Everyone :)

I've got a Motion LE1700 tablet pc here with 9.10 running but I cannot get the main screen to work. At the moment I have an external Dell monitor plugged into the VGA port and i'm using that. Ubuntu 9.04 worked fine on this laptop and I could adjust the resolution for the main screen and the external screen without any issues, but for some reason when I boot 9.10 the main screen on the tablet pc just flickers a couple of times and stays off.

I have tried all sorts of stuff including xrandr and setting the resolution manually but each time the screen just flickers and nothing. I've also tried Xorg -configure and then starting the X server with the newly created xorg.conf file but that doesn't work at all and also kills the external screen. 

I had a look and booted the tablet from a 9.04 live CD, configured both screens and then thought I could copy the xorg.conf file from the /home/ubuntu directory, but that file didn't contain much. 

So... i'm stuck. Can you guys suggest any way to get this running? I have a backup of the /etc/gdm and the /etc/X11 directories from the 9.04 Live CD. Maybe there's something in there that might help. Let me know if you need any of the files.

Cheers! :)


Mich

---

### Post by mictho100 on 2009-11-26
BTW, been trying a couple of more things today but to no avail:

**sudo dpkg-reconfigure -phigh xserver-xorg** <- That command doesn't seem to work anymore in 9.10 :(

Rebooted the box into recovery mode and couldn't find **xfix**. So I dropped into a root shell and went to /usr/share/recovery-mode/options and manually ran **xfix**. Nuffink... it just doesn't work.

Running the **System -> Preferences -> Display** utility doesn't detect the laptop screen. Only the external screen. Under 9.04 this utility detects both screens.

The output of LSPCI is below, so the graphics card seems to be detected. So, just to recap, upon booting the main screen on the laptop just flickers and then goes dead, while I can see the ubuntu logo on the external screen. Weird!

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
08:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
08:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
08:05.0 USB Controller: NEC Corporation USB (rev 43)
08:05.1 USB Controller: NEC Corporation USB (rev 43)
08:05.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


---

### Post by mictho100 on 2009-11-26
Anyone?

---

### Post by lorue on 2010-05-28
Hi Mich
I am having the same problem right now :(, did you fix it??
best regards
Lorue

---

### Post by Favux on 2010-05-28
Hi lorue,

Welcome to Ubuntu forums!

You may need to add 'i915.modeset=0' to your kernel boot line.  It's described in this thread:  [http://ubuntuforums.org/showthread.php?t=1339048&page=2](http://ubuntuforums.org/showthread.php?t=1339048&page=2)

Hope this helps.

---

### Post by lorue on 2010-06-01
Hi Favux, and maybe Mich
I have been analysing the problem and looks worst:
I instaled ubuntu-9.10-alternate-i386.iso (checked with md5sum) and finished very well.
The instalation told me to take out the cd, and then I took out the CD from unit-CD and then I re-start le1700 tabletpc, but now the screen display very very soft all the time. At the begining I believe it was off. 
Now I connected an external monitor, but it do not display information.
As the main monitor display very soft I can not see the information from the BIOS, from Grub, from ubuntu etc etc.
At the begining I believe my problem was as the description from Mich's problem
but now I believe it is very different and worst. By some reason the instalation of ubuntu 9.10 strike, punch something in my machine.
I realy do not know what to think,:confused: and what to do. And I am very worried because the machine is not mine.:( Thank you for your HELP!! in advance.
Lorue

---

### Post by lorue on 2010-06-02
Hi Favux
I finally could send signal to my external monitor plugged into the VGA port.:)
Then I added line:
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"    to file:
/etc/default/grub
now the file is like:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


then I ran update-grub command as root.
then I restart the LE1700 TabletPC and ..... the problem continue:cry:, there is no signal on my main screen, only in my external monitor:(:(:confused::(:(:confused:
The grub instelled is: 1.97 beta 4

Thanks in advance
Lorue

---

### Post by Favux on 2010-06-02
Well that didn't work.

OK, if you're sure the hardware/LCD works.  If you can reach the command line let's see if there has been an update to the driver that will fix it:
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by lorue on 2010-06-03
Hi Favux
I suposse my hardware/LCD works because I can see in the main screen the same image as I can see in the external monitor but very very very soft.
I did 
sudo apt-get install xserver-xorg-video-inteland
I recieved msg "installed in the most recent version"
Synaptic show: 2:2.9.0-1ubuntu2.1 version, same as last version
My VGA controller is: Intel 945GM/GMS, 943/940GML Express Integrated Graphics Controler (rev 03)
regards
Lorue

---

### Post by lorue on 2010-06-08
[SIZE=2]Hi Favux!

I finally found the problem!!!! is the BIOS!!
The LE1700 Tablet PC is from Motion Computing. In the next Address:
[http://www.motioncomputing.com/drivers/LE1700/LE1700_BIOS_AB18_RN.htm](http://www.motioncomputing.com/drivers/LE1700/LE1700_BIOS_AB18_RN.htm)
You can read:
[/SIZE][SIZE=2]**[FONT=Verdana]""Motion   Computing advises all LE1700 users to install this update.  [/FONT]**[FONT=Verdana]See *Fixes in this Release* and *Known Issues and Limitations* below for   more details.""[/FONT][/SIZE]
[SIZE=2]And the first fix said: [FONT=Symbol][FONT=&quot]  [/FONT][/FONT][FONT=Verdana]Enable external display video   during system boot. !![/FONT][/SIZE]
[SIZE=2][FONT=Verdana]exactly my problem!!!![/FONT][/SIZE]
[SIZE=2]
[FONT=Verdana][/FONT][/SIZE]
[SIZE=2][FONT=Verdana]NOW: I do not know how to install the new BIOS. What I have to do??[/FONT][/SIZE]
[SIZE=2][FONT=Verdana]In the same address there is an explain about what to do but using windows[/FONT][/SIZE]
[SIZE=2]
[FONT=Verdana][/FONT][/SIZE]
[SIZE=2][FONT=Verdana]best regards[/FONT][/SIZE]
[FONT=Verdana]Lorue
[/FONT]
[FONT=Verdana][/FONT]
[FONT=Verdana][/FONT]

---

### Post by Favux on 2010-06-08
Outstanding!  Nice work.  The bios, huh?

OK, you almost for sure need to install the bios update through windows.  Sorry for the bad news.  It's suppose to be possible to install a bios update through linux but it is very risky.  That's one reason a lot of people dual boot, they shrink but don't remove their windows install.

---

