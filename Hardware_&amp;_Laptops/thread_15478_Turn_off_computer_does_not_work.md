---
title: "Turn off computer does not work"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by Marcoon on 2005-02-14
I just installed Ubuntu and everything works fine except when I try to use Turn Off Computer. It goes through the shut down process until it shows the ACPI information and then it stops. It will not turn off the computer.

---

### Post by Xian on 2005-02-14
What kernel are you using and what are your general hardware specs? 
Might also want to post the relevant contents of your /boot/grub/menu.lst config file.

---

### Post by Marcoon on 2005-02-14
Sorry.
Athlon XP 2000+
Via K400A chipset MB
512 Mb Ram
Seagate 80Gb SATA HD
NVidia MX4000 video card
Kernel 2.6.8 warty

I'm really new and don't know exactly what's 'relevant' so here's what's there:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by az on 2005-02-14
Do dmesg and look for relevant lines (APM or ACPI)  If the acpi system is not being loaded properly, add the words
acpi=force to your kernel line in grub

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda1 ro quiet splash acpi=force


If that does not work, screw acpi.  Remove the acpi module and load the apm module to see if that helps.

---

### Post by Marcoon on 2005-02-15
Okay, I tried that and it didn't work. But I've started noticing several other problems in addition to that one. For one, Ubuntu has decided I need my screen resolution set to 1600x1200 @ 75hz which I don't want. It causes little white lines to run across the screen. No matter how many times I set the resolution I want (1280x1024@85hz) it goes back to 1600x1200 on startup. Its the little aggravations like this that have caused me to try and subsequently give up on Linux several times before. Oh, I also have a Logitech MX500 mouse with several buttons I can't use in Ubuntu. The one I miss is the thumb button that lets me go back while using the web browser. Frustrating.

---

### Post by Xian on 2005-02-15
[QUOTE=Marcoon]For one, Ubuntu has decided I need my screen resolution set to 1600x1200 @ 75hz which I don't want. It causes little white lines to run across the screen. No matter how many times I set the resolution I want (1280x1024@85hz) it goes back to 1600x1200 on startup. Oh, I also have a Logitech MX500 mouse with several buttons I can't use in Ubuntu. The one I miss is the thumb button that lets me go back while using the web browser. [/QUOTE]
What method are you using to set the resolution? Post the "Screen" section of your /etc/X11/XF86Config-4 file. Further, that would seem to be fairly popular mouse. What is in the "InputDevice" section of your Xconfig and does it match what is recommended for that mouse?

---

### Post by Marcoon on 2005-02-15
[QUOTE=Xian]What method are you using to set the resolution?[/QUOTE]
Computer menu>System Configuration>Screen Resolution

> Post the "Screen" section of your /etc/X11/XF86Config-4 file.
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"NEC FE991SB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

> Further, that would seem to be fairly popular mouse. What is in the "InputDevice" section of your Xconfig and does it match what is recommended for that mouse?
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

---

### Post by az on 2005-02-15
sudo dpkg-reconfigure -plow xserver-xfree86

When it goes into the monitor resolution section, just do not select anything lower than what you want.

So what lines in dmesg are relevant to powere management (contain the words acpi or apm)  What did you try?

---

### Post by Marcoon on 2005-02-15
[QUOTE=azz]sudo dpkg-reconfigure -plow xserver-xfree86

When it goes into the monitor resolution section, just do not select anything lower than what you want.

So what lines in dmesg are relevant to powere management (contain the words acpi or apm)  What did you try?[/QUOTE]

Thanks! That fixed the resolution problem.
Why doesn't the resolution control in the 'Computer' menu work? Any idea?

What I tried was adding ACPI=Force

What should I be looking for in dmesg? There are quite a few lines referring to acpi.

---

### Post by Tiede on 2005-03-05
I too m having some (a LOT of ) problems with Ubuntu...
This is the minimalist one. The comouter won't shut down by its self and I have to press n hold the pwer button for 5 seconds erverytime to make it work.

Here is the outpost of my grepping for acpi

```

marc@Linuxed:~ $ dmesg |grep acpi
You can enable it with acpi=force
thermal: Unknown symbol acpi_processor_set_thermal_limit
acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance
marc@Linuxed:~ $

```

dmesg | grep apm gives nothing.

---
The last too lines of my shutdown screen:
```

md: stopping all md devices
Power Down.

```

---

### Post by bored2k on 2005-03-05
[QUOTE=Tiede]The last too lines of my shutdown screen:
```

md: stopping all md devices
Power Down.

```[/QUOTE]


[http://ubuntuguide.org/#acpipoweroff](http://ubuntuguide.org/#acpipoweroff)

> "Q: acpi_power_off called

   1. Read General Notes
   2.

      $ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
      $ sudo gedit /boot/grub/menu.lst
   3. Find this section

      ...
      title           Ubuntu, kernel 2.6.8.1-4-386
      root            (hd0,0)
      kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash
      ...
   4. Replace with the following lines

      title           Ubuntu, kernel 2.6.8.1-4-386
      root            (hd0,0)
      kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash acpi=off apm=off
   5. Save the edited file (sample)
   6.

      $ sudo cp /etc/modules /etc/modules_backup
      $ sudo gedit /etc/modules
   7. Append the following line at the end of file

      apm
   8. Save the edited file"

I think Chua Wen Kiat's guide should pop up everytime u fresh install ubuntu ...

---

### Post by Tiede on 2005-03-05
Thanks bored2k. Works for me!

I just want to add for any others trying the acpi=force way that it did not work and gave me the message [/code]
ACPI:unable to locate RSDP
[/code]

but bored2k's solution from ubuntuguide works. Thanks for the quick reply ;)

---

### Post by bored2k on 2005-03-05
[QUOTE=Tiede]Thanks bored2k. Works for me!

I just want to add for any others trying the acpi=force way that it did not work and gave me the message [/code]
ACPI:unable to locate RSDP
[/code]

but bored2k's solution from ubuntuguide works. Thanks for the quick reply ;)[/QUOTE]

It should be a rule to read Chua Wen Kiat's guide.
I have user linux for about 1year and some months and i can still find some quick answers on it . I was starting my own guide based on that one , but learning C++ made me lazy

---

