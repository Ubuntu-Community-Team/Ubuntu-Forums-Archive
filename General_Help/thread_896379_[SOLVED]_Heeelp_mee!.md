---
title: "[SOLVED] Heeelp mee!"
date: 2008-08-21
forum: General Help
---

### Post by maxmanapple on 2008-08-21
Guys, I need some help here. My PC has gone crazy! I installed my monitor and graphic drivers, and when I restarted X, he said "You are currently working on low quality. Your monitor and graphic device weren't recognized so you must do it manually."

What can I do to have my graphics back :confused:

Any help appreciated. Answer as soon as possible, please!

---

### Post by iaculallad on 2008-08-21
If you can get on the terminal, try reconfiguring your xorg file:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by maxmanapple on 2008-08-21
Then what should I do :confused:
I am new to Linux and someone told me to install drivers. The image was perfectly fine with "default", and I only installed my screen driver, which was "Plug and Play Monitor". I am afraid of killing Linux permanently because this is a All-linux PC.

Again, what should I do :confused:

Note: I use smileys because my keyboard is screwed too and can't find question mark.

---

### Post by mb_webguy on 2008-08-21
Open the terminal and post the output of the command "lspci" for us, please.

---

### Post by maxmanapple on 2008-08-21
After coding

```
maxmanapple@maxmanapple-desktop:~$ lspci
```

the output was:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
02:0a.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
```

---

### Post by mb_webguy on 2008-08-21
Okay, so you have an ATI Radeon 9200 video card.  *sigh* 

A few questions.  First, what do you see when you go to System->Administration->Hardware Drivers?

Second, when you ran the command "sudo dpkg-reconfigure xserver-xorg" in the terminal, did you tell it to use the fglrx driver?

Third, what's the output of the command "fglrxinfo" in the terminal?

---

### Post by maxmanapple on 2008-08-21
> **mb_webguy said:**
> Okay, so you have an ATI Radeon 9200 video card.  *sigh* 

A few questions.  First, what do you see when you go to System->Administration->Hardware Drivers?

Second, when you ran the command "sudo dpkg-reconfigure xserver-xorg" in the terminal, did you tell it to use the fglrx driver?

Third, what's the output of the command "fglrxinfo" in the terminal?

Answering the first question, it appeared "This system is not using propreatary drivers" and the list was empty.

Second answer: the code:

```
sudo dpkg-reconfigure xserver-xorg
```

lead me to a graphical DOS-like program and only asked me to set up my keyboard (didn't work though)

Third answer: the fglrxinfo command told me to install xorg-driver-fglrx by using the following code line

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by mb_webguy on 2008-08-21
Ah.  Now we're getting somewhere.  You need the fglrx driver, which you don't have installed.

Open the terminal and type "sudo apt-get install xorg-driver-fglrx", just like it told you.  Then run "sudo dpkg-reconfigure xserver-xorg" again, and see if it gives you the option of using the fglrx driver.

---

### Post by maxmanapple on 2008-08-21
It still didn't asked nothing about "fglrx". What he asks instead is:

Use the "framebuffer" driver interface of the kernel
Detect keyboard
Keyboard layout - Country
XKB rule set
Keyboard model
Keyboard variant
Keyboard options

and then outputs the following code lines:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080821105619

```

---

### Post by mb_webguy on 2008-08-21
I really hate ATI video cards...

Ok, let's see the contents of your xorg.conf file.  Type "cat /etc/X11/xorg.conf" in the terminal and post the output here.

---

### Post by maxmanapple on 2008-08-21
```
cat /etc/X11/xorg.conf
```

produced the following

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by Bliepo32 on 2008-08-21
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mb_webguy on 2008-08-21
I really need some sleep, so I'm going to have to leave you with one last nugget of wisdom.

Type the following command in the terminal.```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules
```

You should have already installed the fglrx driver, but whatever.  Now type the following to edit your xorg.conf file.```
sudo gedit /etc/X11/xorg.conf
```

Add the following line to the "Device" section.```
Driver "fglrx"
```
Now scroll down to the end of the file, and add the following lines.```
Section "Extensions"
Option "Composite" "disable"
EndSection
```
Save the file, exit, and then reboot the computer.  If all goes well, everything should now work.

Good night, and good luck.  I'll drop in on this thread tomorrow to see how things work out for you.

---

### Post by maxmanapple on 2008-08-21
Thanks. My screen and keyboard are better now, but my PC runs slow when I use X's graphical special effects. It runs better without them, but what's going on?

---

