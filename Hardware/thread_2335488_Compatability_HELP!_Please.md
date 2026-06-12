---
title: "Compatability HELP! Please"
date: 2016-08-29
forum: Hardware
---

### Post by fae88 on 2016-08-29
[COLOR=#333333][SIZE=2]Hi,

I'm new to Ubuntu and have just bought another new laptop.  I would like to be able to install Lubuntu 16.04 or Ubuntu 16.04... ....I have purchased the HP 250 G4 Laptop, and checked on the Intel site which said it was compatible with Linux.  My son has advised that I should find out if it is compatible with Ubuntu/Lubuntu 16.04 before I try to install it.
[/SIZE]
The reason I'm asking is I've tried to find out on various sites but not being very computer literate am having difficulty finding out. .....I purchased an [/COLOR][FONT=arial narrow][SIZE=2]HP 15-af165sa 15.6" Laptop last week [/SIZE]and had to send it back because of the problem with AMD graphics.

T[FONT=arial][SIZE=2]he specs for the [/SIZE][/FONT][/FONT][COLOR=#333333][FONT=arial]HP 250 G4 Laptop [/FONT][/COLOR][SIZE=2]are as follows:
[/SIZE][COLOR=#333333][FONT=&amp]Processor[/FONT][/COLOR]
[LIST]
[*]Intel Core i5-6200U Dual Core 2.3GHz
[*]Turbo boost up to 2.8GHz
[*]3MB Cache
[/LIST]
[COLOR=#333333][FONT=&amp]Memory[/FONT][/COLOR]
[LIST]
[*]8GB DDR3L 1600MHz
[*]Configuration 1 x 8GB
[*]2 x SODIMM
[/LIST]
[COLOR=#333333][FONT=&amp]Hard drive[/FONT][/COLOR]
[LIST]
[*]1TB HDD 5400rpm SATA
[/LIST]
[COLOR=#333333][FONT=&amp]Optical Drive[/FONT][/COLOR]
[LIST]
[*]DVD+/-RW SuperMulti DL
[/LIST]
[COLOR=#333333][FONT=&amp]Software[/FONT][/COLOR]
[LIST]
[*]Operating System: Windows 10 Home 64bit
[/LIST]
[COLOR=#333333][FONT=&amp]Display[/FONT][/COLOR]
[LIST]
[*]39,6 cm (15.6") diagonal HD SVA anti-glare flat LED-backlit
[*]Resolution: 1366 x 768
[/LIST]
[COLOR=#333333][FONT=&amp]Graphics[/FONT][/COLOR]
[LIST]
[*]Intel HD Graphics 520
[/LIST]
[COLOR=#333333][FONT=&amp]Audio[/FONT][/COLOR]
[LIST]
[*]DTS Studio Sound&#8482;
[*]Dual speakers
[/LIST]
[COLOR=#333333][FONT=&amp]Input Devices[/FONT][/COLOR]
[LIST]
[*]Touchpad
[*]Full-sized textured black island-style keyboard with numeric keypad
[*]Touchpad with multi-touch gestures enabled, taps enabled as default, default on for 2-finger scroll and pinch
[/LIST]
[COLOR=#333333][FONT=&amp]Networking[/FONT][/COLOR]
[LIST]
[*]Wireless: Realtek RTL8723BE 802.11b/g/n (1x1) WiFi
[*]Wired: Realtek Ethernet (10/100)
[*]Bluetooth 4.0
[/LIST]
[COLOR=#333333][FONT=&amp]Power Supply[/FONT][/COLOR]
[LIST]
[*]45 W Smart AC adapter
[*]3-cell, 31 WHr Li-ion battery
[/LIST]

Sorry if I've posted too much info but not sure exactly whats needed to check!......Any help would be very much appreciated

Rach x

---

### Post by Bucky Ball on 2016-08-29
Welcome. Try this. Download the Ubuntu or Lubuntu 16.04 ISO> create a bootable disk/USB> boot from it> choose 'Try Ubuntu' (this won't install to the hard drive or change anything on there). If everything works, it's compatible! You don't have to install it straight away. You can try it out first. If it works without issue, great. If not, get back to the forums and start asking questions. ;)

Seriously, the best way to find out is to just try it. The only issues you are really ever going have are with video and wireless and they can usually be fixed. Some machines can have their unique idiosyncrasies but they are generally hard to predict until you've installed and they arise. (Odd things can also happen with wireless, like it works on the 'Try Ubuntu' but not on an install or doesn't work on either but can be easily fixed or, more likely and hopefully, works on both 'out of the box').

You have Intel graphics, Realtek wireless, both well supported in Ubuntu. I'd advise you get to trying it out ASAP. I see nothing that rings alarm bells to me at least. Good luck and let us know how you go. :)

(If 'Try Ubuntu' works, there's a big icon on the desktop that says 'Install Ubuntu', but you might want to ask here before doing that, particularly if you are intending to install dual-boot with Win10.)

Your new machine specs will handle any flavour of Ubuntu you want to throw at it as far as CPU and RAM. Any questions, just ask. 

PS: Be aware that Linux is not Windows in as much as many, many drivers are already in the Ubuntu kernel so there is a very good chance you will not need to install any drivers for wireless (and almost certainly not for the Intel graphics) or punch in 25 digit authentication codes to do so.

---

### Post by ajgreeny on 2016-08-29
As this machine is new and has Win 10 installed it will almost certainly be UEFI compliant and Win 10 will be installed in UEFI mode.
See these for more info:-
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Are you wanting a Dual Boot with Win 10 or will you be wiping the Win 10 installation?
If Dual Boot you **MUST** install Lubuntu in the same mode as Win 10, ie, probably UEFI, but if you intend to wipe Windows and have a single boot Lubuntu machine you could set the BIOS/UEFI to use legacy-BIOS mode, called different things depending on the maker.

Read the **Systems that only boot Windows from UEFI.** in that second link as HP is one of those manufacturers, though I think that is not a problem should you choose to wipe Win 10 and install Lubuntu in legacy BIOS mode.

---

### Post by fae88 on 2016-08-29
Hi Bucky and ajgreeny,

First of all I'd really like to thank you for your quick reply...phew!....I did notice the 'Try Ubuntu' but ignored it and tried to install on the last laptop....what an idiot!!   Anyway I will now download to USB again and choose the Trial first with the HP 250 as you have suggested.

I don't intend to install dual-boot with Win 10 but I will still come back to ask if you don't mind before I do a proper install.

MMhhmm Ubuntu looks great :)...I will read more about it thanks for the links.

Thanks again, I was tearing my hair out :confused:

Rach x

---

### Post by Bucky Ball on 2016-08-29
> **fae88 said:**
> 

I don't intend to install dual-boot with Win 10 but I will still come back to ask if you don't mind before I do a proper install

That makes things easier (no dual-boot) and good idea, please do to the last bit. Good luck. :)

---

### Post by oldfred on 2016-08-30
Even if not planning on keeping Windows, best to fully back it up or dual boot.
We see many users have major issues trying to reinstall Windows as they have one application or requirement for school or work that must use Windows. Or later they want to sell system and it needs Windows to be saleable.

One user who must regularly upgrade systems, says he removes Windows drive, buys new SSD and installs Ubuntu. Then when he sells system, he just puts totally unused Windows drive back in and and has no issues of his data on drive.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Bucky Ball on 2016-08-30
> **oldfred said:**
> Even if not planning on keeping Windows, best to fully back it up or dual boot.
We see many users have major issues trying to reinstall Windows as they have one application or requirement for school or work that must use Windows. Or later they want to sell system and it needs Windows to be saleable.

oldfred makes a good point. First cab off the rank for me with a new machine that has Windows is to boot to Windows, create the recovery disk(s) (two sets) before doing anything else.

I recently found by accident then bought, as rare as a hen's tooth, an MSI laptop that came with NO OS so didn't need to bother with any of that for once. :)

---

### Post by simonsaysthis on 2016-09-03
I really recommend AOMEI Backup in Windows 10. It's a free program which can create a backup clone of your hard drive. I have very similar hardware and by default Ubuntu should set up dual boot quite well when you select "install alongside Windows". BUT I recommend wiping the dist and doing Ubuntu alone. I have now taken the leap and deleted Windows completely. These things there is  hardly much to miss for the average home user.

---

