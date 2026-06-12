---
title: "Running successful LiveCD Kubuntu 5.10 on HP laptop zd8230us"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by GJC on 2006-03-28
Running successfully [B]LiveCD Kubuntu 5.10 on HP laptop zd8230us
[/B]
[SIZE="4"]Hardware[/SIZE]
Product Name 	zd8230us 
US Product Number 	EC294UA#ABA
Microprocessor 	3.4GHz Intel® Pentium® 4 Processor 650,SpeedStep®, and HT Technology
Microprocessor Cache 	2MB L2 Cache
Memory 	1024MB 533MHz DDR2 System Memory (2 Dimm)
Memory Max 	2048MB
Video Graphics 	ATI MOBILITY RADEON X600
Video Memory 	128MB DDR (dedicated)
Hard Drive 	100GB 4200 Hard Drive
Diskette Drive 	External USB Floppy Drive available for customers via hpshopping.com or local retailers
Multimedia Drive 	LightScribe 8X DVD±RW and CD-RW Combo Drive with Double Layer Support with 1 CD-R blank media
Display 	17.0" WXGA+ High-Definition BrightView Widescreen wide viewing angle (1440 x 900) Display 
Fax/Modem 	high speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	54g™ 802.11b/g WLAN with 125HSM / SpeedBooster™ and BroadRange™ support & Bluetooth™
Sound 	Altec Lansing 
Keyboard 	Notebook keyboard with scroll bar and integrated numeric keypad & 2 quick launch buttons
Pointing Device 	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
PC Card Slots 	•	1 ExpressCard/54 Slot (also supports ExpressCard/34)
•	1 Type I/II 32-bit card bus (also support 16-bit) 
External Ports 	•	4 Universal Serial Bus USB 2.0
•	1 VGA (15-pin)
•	1 RJ-11 (modem)
•	1 TV-Out (S-video)
•	1 RJ -45 (LAN)
•	1 Expansion Port 2 connector
•	1 headphone-out
•	1 microphone-in
•	1 IEEE 1394 Firewire (4-pin)
•	1 Consumer IR (Remote Receiver)
-------------------
I use the following parameters at boot prompt
	__Boot: live-expert vga=771 noapic nolapic acpi=off nofb

Loading……………..

Keep using default parameter (tab + enter keys follow boot instructions) until LOAD INSTALLERS COMPONENTS screen appears. In my case, I selected
	__NTFS-modules….
	__RTC-modules……
	__TZsetup-udeb…..

At SET UP USERS AND PASSWORDS screen, I selected
	__Enable shadow password?                  YES
	__Choose a root password                      ********* (choose your own pwd)
	__Create a normal user account now?     YES

Keep using default parameter (tab + enter keys follow boot instructions) until CONFIGURING XSERVER-XORG screen appears, selected
	__Attempt to autodetect video hardware?      NO
	__Select the desired x sever driver                VESA
	__Enter an identifier for your video card         GENERIC VIDEO CARD
	__Enter the amount of memory (in KB)           128000 (in my case)
	__Use kernel framebuffer device interface?     NO

Keep using default parameter (tab + enter keys follow boot instructions) until
	__Attempt monitor autodetection?                 NO
	__Enter an identifier for your monitor              GENERIC MONITOR

Select the modes you would like the X server to use
	__Choose the last three 1024x768, 800x600 and 640x480 (do not use more than 1024x768 because the x server will not run with higher resolutions, at least in my case)

Please choose a method for selecting your monitor characteristics……
       __I chose   SIMPLE (if you know what you are doing, you may try something else)

Monitor size? In my case           17 inches
Default color depth in bits.        24

After some more loading of parameters Kubuntu will load. I found out a little bit slow the speed of the internet connection (using DSL phone-line)

Hope my friends; all of this will help some of you with similar situation. SIGNING OFF.

---

