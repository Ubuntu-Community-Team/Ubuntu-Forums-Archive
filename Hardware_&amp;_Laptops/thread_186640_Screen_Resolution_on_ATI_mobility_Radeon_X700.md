---
title: "Screen Resolution on ATI mobility Radeon X700"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by UrbanFallout on 2006-06-02
Hello

I've just installed Dapper 6.06, but I cannot get my native screen resolution of 1280x800 to work. (It did before without any issues when I used Breezy).

I have tried the following:
1. Adding the "1280x800" to my xorg.conf file manually on every line I see "????x???". Restarting X with ctrl+alt_backspace does nothing. Upon rebooting I get greeted with a blank screen.
2. Running "sudo dpkg-reconfigure xserver-xorg" gives the same results.

I've restored my backed up xorg.conf file and am working at 1024x768 for now.

A related but less important issue is that booting from the live CD I have to boot using "Safe video mode" (the 2nd option). If I boot in the standard way I again get greeted by a completely blank screen. 

Going to a text terminal after booting up, and then logging in works fine in all the above cases.

Does anyone have any hints?

I'm running an Acer Aspire 5024, with an ATI mobility Radeon X700.

Many thanls in advance
Nick

---

### Post by lucraft on 2006-06-02
I have just spent 2 hours solving virtually the same problem. I'm running an Acer Aspire 5024WLMi with ATi Radeon X700 so we are identical in hardware.

Steps I took to solve:
(1) Follow instructions in this howto (method 1): [http://wiki.ubuntu.com/BinaryDriverHowto/ATI](http://wiki.ubuntu.com/BinaryDriverHowto/ATI)

note: when it says "confirm this works" and tells you to run fglrxinfo, i get an error message about BadAlloc, but the following still works.

(2) Run
>  sudo dpkg-configure xserver-xorg
(2a) when it asks for drivers 'ati' should be auto selected. choose 'fglrx' instead.
(2b) I don't know if this matters but I'm saying yes to the framebuffer option.
(2c) when it asks you to choose the video resolutions, there are TWO 1280x800 modes, but only the top one seems to work. (selecting both also works.) I have no idea why this should be.
(2d) when it asks you how you would like to configure your monitor characteristics, the 'Advanced' option with all the defaults works.

Notes: 
(a) I'm only writing this because we have the exact same hardware, otherwise I would not expect this to work right, especially since errors come up during the howto.
(b) I have not yet tested video or 3d graphics.

best,
Dan

---

### Post by lucraft on 2006-06-02
woops, should have been > sudo dpkg-**re**configure xserver-xorg

---

### Post by UrbanFallout on 2006-06-02
Thank for the hints lucraft. 

I managed to get the proper resolution, but using a much simpler method:

1. Open synaptic manager
2. Search for "[COLOR="Red"]fglrx[/COLOR]"
3. Select "[COLOR="Red"]fglrx-control[/COLOR]" for installation and accecpt the additional packages it will install.
4. Close synaptic manager.
5. Open a terminal window and type 

[COLOR="RoyalBlue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

6. Accept the defaults in every case, except the following:
6a. Driver: When asked what driver should be used. Choose "[COLOR="Red"]fglrx[/COLOR]".
6b. Resolution: Choose "[COLOR="Red"]1280x800[/COLOR]".

7. Reboot. I think a simple "ctrl+alt+backspace" to restart X might also do the trick, but I didn't try this.

Viola. You now have 1280x800 resolution with minimal effort.
Hope this us helpful. 

Cheers
Nick

PS: If anyone remembers the specific syntax to call dpkg, I'd appreciate you posting it as it would do steps 1-4 in one terminal command. I couldn't get it to work.

---

### Post by Dr Gonzo on 2006-06-02
sudo apt-get install fglrx-control

---

### Post by Pistolpete2 on 2006-06-16
This is quite interesting for me because I have got the acer aspire 5024WLMi also. I'm gonna install ubuntu in a few days and I'm totally new as it comes to linux. So please correct me if I'm wrong:

If I want to get my x700 to work. The only steps I have to do are:

(1)  open terminal and  enter 
          ```
sudo apt-get install fglrx-control
``` 
          (probably have to give my pass(because of sudo)
(2)  than i type the following command in my terminal
             ```
sudo dpkg-reconfigure xserver-xorg
```
(3)   Accept the defaults in every case, except the following:
(3a) Driver: When asked what driver should be used. Choose "fglrx".
(3b) Resolution: Choose "1280x800".
(4)   Reboot.

If anyone (who knows what he's talking about) could confirm this,I would be thankfull to him. I'm allready thankfull for UrbanFallout,lucraft and Dr Gonzo their posts.

greetings

---

### Post by ovimunt on 2006-06-24
To start with, I'm a COMPLETE BEGINER with Linux in general. :-| However, I do know a thing or two about computers. ;) 

I've just installed Ubuntu 6.06 on my computer and I've got a bit of a problem. It would be great if anyone could help me.

I've downloaded the DVD version of Ubuntu and first tried it Live. It didn't seem to work or at least I got no graphics whatsoever.:confused:  I then tried the 'safe graphics mode' and it worked just fine.;) 

After this I decided to try and install Ubuntu on a separate partion. Installation went smoothly (except for the WiFi which I know will need some additional work :neutral: ), Grub works fine so I can use my Win XP, but again I get no graphics at all when trying to start Ubuntu.:confused:  I did try to edit the boot lines in Grub and add 'xforcevesa' as it appears in the command line on the 'safe graphics mode' of the Live DVD but it still didn't work.:( 

So I guess I'm stuck for now, good thing my Win XP starts just fine. I guess Microsoft are not that bad after all.  :neutral: 

Anyway, if you've got an idea on how I can get graphics, please let me know.

---

### Post by ovimunt on 2006-06-25
Problem solved, d**n it!

I mean, c'mon, this bl***y Linux can't be smarter then I am, right? (or so i hope :D)

The problem is that Xserver tries to display the image on the wrong device! You might know that the Acer Aspire 5024WLMi with ATI Mobility Radeon X700 has also a Standard Monitor connector, TV-Out and dual display capability besides its own screen. What probably happens is that the Xservers is sending the signal to the Standard Monitor connector. To sort this out you just need to tell it to also look for other display devices.

SOLUTION: (NOTE - ALL COMMANDS ARE cAsE sEnSiTiVe!)

1. After the drum sound press Ctrl+Alt+F1 once or several times until you're in text mode. 

2. Now enter your login and password details.

3. You're now in command line mode. Type the following lines:

[I]cd /
cd /etc/X11
sudo nano xorg.conf[/I]

Some of these commands are redundant but they'll get the job done.

4. You've opened the *xorg.conf* file in the Nano text editor. Scroll almost all the way down until you find these lines:

[I]Section "Monitor"
	Identifier	"Generic Monitor"
	Option ...
EndSection[/I]

5. Replace the line

*Option ...*

with

*Option "Monitor Layout" "LVDS,AUTO"*

I'm not 100% sure what this does but someone around here was saying that it tells the Xserver to look for additional display devices.

6. Press Ctrl+X. This will exit the text editor but first you'll be asked if you want to save the changes. Type Y and press Enter until you're back to the command line.

7. Type 

*sudo reboot*

This will reboot the system

That's it, everything should be just fine now. Good luck! ;)

---

### Post by Zahlerstreik on 2006-06-27
i love you
this took mr forever to find
THANK YOU
my x800 works now :)

---

### Post by euan on 2006-06-27
I've got a similar problem, I can select the mode, but it's corrupt.  I'm running a Uniwill 258KA0 with a Radeon Mobility 9700.   When I select the 1280x800 mode, the mode does change, but two columns on each side of the screen are messed up and full of noise, and the mouse cursor changes to a square block of garbage.  Any ideas?

log clippings:

```
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=40000; xclk=20500
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: Samsung LTN154X1 WXGA   
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 800x600
(II) RADEON(0): Valid mode using on-chip RMX: 640x480
(II) RADEON(0): Total number of valid FP mode(s) found: 3
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   68.90  1024 1288 1328 1408  768 800 803 816
(**) RADEON(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   68.90  800 1288 1328 1408  600 800 803 816
(**) RADEON(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   68.90  640 1288 1328 1408  480 800 803 816
(**) RADEON(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   68.90  640 1288 1328 1408  350 800 803 816
(**) RADEON(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   68.90  640 1288 1328 1408  400 800 803 816
(**) RADEON(0):  Default mode "720x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   68.90  720 1288 1328 1408  400 800 803 816
(**) RADEON(0):  Default mode "832x624": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   68.90  832 1288 1328 1408  624 800 803 816
(**) RADEON(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   68.90  1280 1288 1328 1408  768 800 803 816
(**) RADEON(0):  Default mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   68.90  1280 1288 1328 1408  800 800 803 816
(**) RADEON(0):  Default mode "1152x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"   68.90  1152 1288 1328 1408  768 800 803 816
(==) RADEON(0): DPI set to (75, 75)

```

---

### Post by euan on 2006-06-27
I installed the above fglrx driver as per above instructions.  All fixed.  My touchpad scroll bar even started working!  magic...

---

