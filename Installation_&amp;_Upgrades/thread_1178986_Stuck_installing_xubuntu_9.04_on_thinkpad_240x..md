---
title: "Stuck installing xubuntu 9.04 on thinkpad 240x."
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by ylar34 on 2009-06-05
[FONT=Verdana][SIZE=2]I have a Thinkpad 240x and I am trying to get it to run Xubuntu 9.04. It feels close to being completed but everytime I boot it takes me to the point where the splash screen finishes its loading graphic, then it flickers and then the screen shuts off. I've tried many things and I am pretty stumped.
 

Installation Process:

The installation process hasn't been easy since the computer has no cd drive or usb that i can boot from. however i do have the ibm portable drive bay that connects to the pcmcia slot so once the computer boots, the cd drive can be used.

I downloaded xubuntu 9.04 alternate release iso on to my other computers disk.
physically removed the 240x's harddrive and placed it in a IDE enclosure.
made a small 800mb fat32 partition to the disk and put the xubuntu iso on there.
I put the harddrive back into the 240x and at the same time burned the xubuntu cd.
I connected the cd drive to the pcmcia slot with the xubuntu cd inside then started the 240x.
The 240x booted to the harddisk iso of course and i began the installation process. When it got to the stage where it needed the cd, it began to read the files from the install cd that was in the drive bay. i wiped my disk and partitioned with ext3 and swap.


The splash screen finishes its loading graphic, then it flickers and then the screen shuts off.

 At first I thought it was a xorg problem so i went into the recovery console and did the dpkg-reconfigure xserver-xorg command. no change.

I tried the following boot options with no change:
 noquiet nosplash
[/SIZE][/FONT][FONT=Verdana][SIZE=2]noacpi [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] acpi=force [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] pci=noacpi [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] pci=acpi [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] acpi_irq_balance [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] acpi_irq_nobalance [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] acpi=oldboot [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] acpi=ht [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] noapic [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] nolapic [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] noapm [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] irqpoll [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2] xforcevesa 
[/SIZE][/FONT]

[SIZE=2][FONT=Verdana]Thinkpad 240x specs[/FONT][/SIZE]:
[FONT=Verdana][SIZE=2]Intel Celeron 450 MHz[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]192 MB of RAM
 [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]BIOS is the latest version[/SIZE][/FONT][FONT=Verdana][SIZE=2] 1.03.23[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Any help would be greatly appreciated.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]


[/SIZE][/FONT]

---

### Post by kerry_s on 2009-06-05
on boot up, select the second option in grub to boot into rescue mode.

type: nano /etc/X11/xorg.conf

in the driver section put:

```
	Option 		"BusType" 	"PCI"
```

example:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option 		"BusType" 	"PCI"
EndSection
```

---

### Post by ylar34 on 2009-06-05
entered the new xorg information, no real change however now the screen comes back only to flicker off again.

---

### Post by kerry_s on 2009-06-05
> **ylar34 said:**
> entered the new xorg information, no real change however now the screen comes back only to flicker off again.

what is the vid driver? i see neomagic or savage?
also have you added vga=788 for the screen size? 800x600@16bits

---

### Post by ylar34 on 2009-06-05
I tried the VGA= option with no success. I don't know what driver I have but the video card is a SMI LynxEM+ video controller with 2M.

---

### Post by ylar34 on 2009-06-05
Just want to add that the installation boots properly on my friends Thinkpad 240 but not on my 240x.

---

### Post by stavrosz on 2011-01-11
i have another issues
i have xubuntu running on the 240x
its not the fastest but it works for the basics.
all I want is to be able to connect a 2nd display !
i tired the xfce display manager, but it only shows Screen O and will not allow me to add 

when i connect my 2nd monitor upon booting up, the bios sees it, and actually it works all the way until Xubuntu kicks in, then the VGA signal stops

HELP !!

---

