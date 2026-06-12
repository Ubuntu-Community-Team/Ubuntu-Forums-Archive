---
title: "Problem Installing Xubuntu on old PC"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by hangman13us on 2009-05-08
Hi All,
I hope here somebody could help me. I have old PC (more then 10 years old). It’s my first PC and it’s some kind of sentimental value for me. The machine is not so bad – see attached report from Everest home edition below:

~~~~~~~~~
EVEREST Home Edition © 2003-2005 Lavalys, Inc. 
________________________________________
  			
		Version   	EVEREST v2.20.405 
		Homepage   	[http://www.lavalys.com/](http://www.lavalys.com/) 

		Report Type   	Report Wizard 
		Computer   	ZEN 
		Generator   	Shared PC 
		Operating System   	Microsoft Windows XP Professional 5.1.2600 (WinXP Retail) 
		Date   	2009-04-28 
		Time   	08:56 

Summary 
________________________________________
  				
		Computer: 
			Operating System   	Microsoft Windows XP Professional 

			OS Service Pack   	Service Pack 2 
			DirectX   	4.09.00.0904 (DirectX 9.0c) 

			Computer Name   	ZEN 
			User Name   	Shared PC 
  				
		Motherboard: 
			CPU Type   	Intel Celeron-A, 533 MHz (8 x 67) 

			Motherboard Name   	Unknown 
			Motherboard Chipset   	Intel 82440LX/EX 

			System Memory   	256 MB (SDRAM) 
			BIOS Type   	Award Modular (09/23/98) 

			Communication Port   	Communications Port (COM1) 
			Communication Port   	Communications Port (COM2) 
			Communication Port   	Printer Port (LPT1) 
  				
		Display: 
			Video Adapter   	Trident Video Accelerator 3D Image975 (4 MB) 

			3D Accelerator   	Trident 3Dimage 975 

  				
		Multimedia: 
			Audio Adapter   	Trident 4DWave DX Sound Accelerator 
  				
		Storage: 
			IDE Controller   	Intel(R) 82371AB/EB PCI Bus Master IDE Controller 

			Floppy Drive   	Floppy disk drive 
			Disk Drive   	FUJITSU MPE3136AH (13 GB, 7200 RPM, Ultra-ATA/66) 

			Disk Drive   	USB 2.0 Flash Disk USB Device (972 MB, USB) 
			Optical Drive   	HL-DT-ST CD-ROM GCR-8520B (52x CD-ROM) 

			SMART Hard Disks Status   	OK 
  				
		Partitions: 
			C: (NTFS)   	13013 MB (9438 MB free) 
  				
		Input: 
			Keyboard   	PC/AT Enhanced PS/2 Keyboard (101/102-Key) 
			Mouse   	Microsoft PS/2 Mouse 

  				
		Network: 
			Network Adapter   	Realtek RTL8139/810x Family Fast Ethernet NIC (xxx.xxx.xxx.xxx) 

  				
		Peripherals: 
			Printer   	Microsoft Office Document Image Writer 
			USB1 Controller   	Intel 82371AB/EB PIIX4 - USB Host Controller 
			USB Device   	USB Mass Storage Device 
~~~~~~~~~~


Recently I found Xubuntu and a friend of mine strongly recommended it to me especially for old machine like this one. I tried to install it few times but all attempts just failed. The machine even did not show Xubuntu – when I selected and entered in the install Xubuntu it showed some notes and start to repeat them on the black screen of the console.
Can somebody help me. I suspect some hardware incompatibility. 

regards,
hangman13us

---

### Post by jerrrys on 2009-05-08
never tried Xubuntu. but if you can run xp pro you should be able to run 804...
804 likes old computers...

---

### Post by hangman13us on 2009-05-08
I know that... I think some of my hardware is not compatible with Linux at all. The only distribution which has been installed on this PC was Kubuntu 6 - the performance was very low... but there is no problem with XP. :(

regards,
hangman13us

---

### Post by hangman13us on 2009-05-08
I just tried again the error is:

[I][319.210210] end_request: I/O error on device sr0, sector 1207256


[319.123122] Buffer I/O error on device sr0, logical block 301815[/I]

This starts when I try to install Xubuntu. I can see the logo of Xubuntu but later the errors displays on the screen and this repeats for ever (I test it for 30 mins). Also the numbers above changes on each line...

please help... this should be something.

rgrds,
hangman13us

---

### Post by Colin@oxford on 2009-05-09
The sr0 device is the CD, so perhaps there is a problem with that CD. I suggest that you try Puppy Linux in the first instance since it is very small and works successfully on my 10-year old machine with only 128MB.  This will at least prove whether your hardware is compatible with Linux or not.  I suggest version 4.0 which uses an older kernel supporting older architectures.  If you get similar sr0 problems, then it might indicate a problem with your CD drive.

---

### Post by kerry_s on 2009-05-09
i would suspect a bad cd, try burning a new one, burn slow 4x for the best results, you might also want to use the alternate cd, you don't have enough memory for a live install.

533mhz and 256mb ram is very low specs, but it is usable, *ubuntu's are not the best for such a machine, there are faster, better choices.

---

### Post by hangman13us on 2009-05-16
Puppy Linux in very nice. I'm impressed that you have such a small and nice looking OS. Puppy runs fine. I had to use Xvesa instead of Xorg. Suppose the problem with my PC Linux compatibility is in the Video Card. Trident 3D 4 Mb is very low and I had a lot of problems with Non Windows installations.

Kerry_s: can you recommend some of the OS you mentioned. This is an old computer on which I can practice and try new things.  Thanks for your time on this one. :D

---

### Post by Bartender on 2009-05-16
+1 on kerry's comments.
You need to download the alternate install version.  I just recently tried to install Ubuntu to a PC with 256 RAM using a LiveCD.  It sat there and spun the CD for ten minutes without accomplishing anything.
I doubled the RAM and install went fine.
The alternate CD needs less RAM to install than the LiveCD, so if you can't boost the actual RAM inside the alternate CD is the best workaround.  Installing more RAM would actually be the better solution!!

You can burn the install CD on any computer of course, but use a good quality CD-R, not RW, and burn it slow.

---

