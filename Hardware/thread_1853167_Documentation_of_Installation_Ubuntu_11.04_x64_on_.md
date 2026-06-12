---
title: "Documentation of Installation Ubuntu 11.04 x64 on inspiron n5110"
date: 2011-10-01
forum: Hardware
---

### Post by altometer on 2011-10-01
Final Edit: I closed this as it is no longer related to my interests. I am now attempting to do the exact same on Ubuntu 10.04 64x.
The guide I used below worked great. Just compile for Ubuntu/manic

Hello, in this thread I will be documenting the process of installing ubuntu 11.04 x64 on my laptop. It seems that every time I work on something like this, I have many issues. I will update the first post with updates.

> 
inspiron n5110

1	225-0535	Inspiron 15R
1	317-6273	2nd generation Intel Core i3-2310M processor 2.10 GHz
1	317-6282	6GB,DDR3,2 DIMM
1	320-2037	15.6in High Definition (720p) LED Display with TrueLife
1	320-2030	AMD Radeon HD 6470M - Seymour XT 512MB (Dual)
1	342-2260	500GB 5400 RPM SATA Hard Drive
1	318-0544	Black Exchangeable Cover + WLAN
1	331-0806	Windows 7 OS Label,CNB
1	421-5780	Genuine Windows 7 Home Premium 64 bit Service Pack 1, English, No Media
1	463-2282	Dell Owners Manual installed on your system,click on icon after system set-up to access
1	430-3605	Integrated 10/100 Network Card
1	318-0463	8X Tray Load CD/DVD Burner (Dual Layer DVD+/-R Drive)
1	313-8545	High Definition Audio 2.0 with SRS Premium Sound
1	430-4129	Intel Centrino Wireless-N1030, 1x2 bgn (2.4GHz) + Bluetooth
1	421-3874	Camera Software 2.X, Factory Install
1	331-2241	English Documentation, Inspiron N5110
1	331-2242	English Keyboard,US,C12SN,N/M5110
1	312-1179	48 WHr 6-cell Lithium Ion Primary Battery



The following will need to be resolved.

Graphics:
From what I understand, due to the integrated Intel graphics card, it becomes extremely difficult to use any other built in card while running Ubuntu. Clarification on this would be much appreciated. 
Edit1: ATI/AMD proprietary FGLRX graphics driver is available. Will attempt to install that.
Edit2: 
Booted up the laptop, It loaded using gnome instead of unity. Error "There was a problem initializing Catalyst Control Center Linux edition. No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI hardware, or configure using aticonfig.
I will attempt to uninstall the driver and get unity to start loading again.
Edit3:
Running the guide from [http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334). I get this happening on my screen. [http://i.imgur.com/gNZUL.jpg](http://i.imgur.com/gNZUL.jpg)  I think it has something to do with screen refresh rate. Will attempt to set refresh rate manually.
Edit4:
I connected a vga cable to the exterior port, the screen on the laptop un-tore. I was able to get into the ATI-configuration panel from inside unity. All appears correct. Reboot and it breaks again. Reconnect VGA and "fixes" it again. this HAS to be a configuration issue at this point.
Edit5:
Ubuntu classic mode's menubars on the windows aren't working. I attempted enable windows details via compiz fusion. I have the buttons of my menu back, but I can't move windows around. Any help at this point would be much appreciated. I also can't drag to re-size windows.

WiFi:
I will try to solve this first.
Edit: Wifi works now. I didn't have to make any changes.

---

### Post by bluepicaso on 2011-10-19
So did it go good?

---

### Post by altometer on 2011-12-06
Yes, the install of 10.04 lts 64x was a breeze.

First, install kernel 2.6.38 using the following command.
```
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```

then install the graphics drivers via the guide found at [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

