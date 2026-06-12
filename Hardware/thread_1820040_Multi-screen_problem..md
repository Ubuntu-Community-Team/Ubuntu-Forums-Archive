---
title: "Multi-screen problem."
date: 2011-08-07
forum: Hardware
---

### Post by florian_monfort on 2011-08-07
Hello everyone !

I just bought a new HP Pavilion DM1 11,6" laptop with E-Zacate E-350 platform. I installed Ubuntu on it, and after fixing the wifi problem, here is another one :

I have another 23" screen by Samsung ( SyncMaster SA350 ) that I want to use as a larger screen ( better for using Inkscape, the GIMP and Scribus ). But it is almost impossible for me to configure it properly, as it won't accept good parameters, even through the ATI Catalyst Control Center ...
I also have to admit that the performances for Compiz are quite crappy ... :/. For a brand new computer I am quite disappointed :/.

I need a solution, if someone could help me configure my screen I would be greatfull :). I assume there must be a solution because it's working perfectly well under Windows 7.

---

### Post by SalHelder on 2011-08-07
I guess you are doing it wrong, the ATI Catalist is not for that as far as I'm concerned, you should go to System > Preferences > Monitors, and there you should find the options to configure the resolution of the external one.

---

### Post by florian_monfort on 2011-08-07
I actually thought first about it, but before I installed the proprietary drivers it would only show one screen ... :/. It's not working.

---

### Post by florian_monfort on 2011-08-07
I'm gonna reinstall ubuntu and check !

---

### Post by florian_monfort on 2011-08-07
I have news. With the radeon free driver I can have 1080p resolution on my 23" screen. 

The problem is now that i don't have a complete virtual desktop on the screen, I only have a top panel without the launcher ...

Plus I'm suspecting my screen to use 16Bits colors, instead of 32bits, because the colors are not really good ...

---

### Post by SalHelder on 2011-08-07
I've found out a few things about your graphics card, one is that it doesn't have dedicated memory so its normal that compiz works poorly, so maybe it's a good idea to either turn it off or just use metacity's compositing (not sure if it will work well under Unity).

It seems that the graphic card is not well configured, the drivers are not right. I guess the version of Catalist available on the repos is the 11.4. As far as I've found the Catalist 11.7 should solve your problems, since you don't have yet the computer settled down to work, since this could go wrong, anyway give it a try:

[http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html]("http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html")

---

### Post by florian_monfort on 2011-08-07
I'm using only the free driver right now. Installing Catalyst drivers would solve the problem ?

---

### Post by SalHelder on 2011-08-07
Well I guess its worth giving it a run, anyway if it goes wrong you can always re-install and get what you have now.

---

### Post by florian_monfort on 2011-08-07
Well, here I am, I just tried the 11.7 version, And I still have problems... The 23" screen won't go further than 1776x1000 and the laptop screen doesn't have any proper "Desktop", it's just an area where I can put other windows ...

---

### Post by SalHelder on 2011-08-07
Just wondering are you using an HDMI cable or a VGA?

---

### Post by florian_monfort on 2011-08-07
HDMI why ? 1.4 version.

---

### Post by SalHelder on 2011-08-07
I've no clue what is wrong with it. Just tell me if with Catalist 11.7 you get better colors on the laptop. Anyway could you post your xorg.conf it might be usefull to see why you can't have bigger resolutions on the Monitor.

---

### Post by florian_monfort on 2011-08-08
I'll do it this evening, for now I'm at work ( using Windows XP haha ... ).

---

### Post by florian_monfort on 2011-08-08
And with Catalyst 11.7 I don't have better colours... It's weird that there is no option to change it and get from 16 Bits to 32 ! O.o

---

### Post by florian_monfort on 2011-08-08
At which adress will I find it ? The file.

---

### Post by SalHelder on 2011-08-08
It is located at /etc/X11/xorg.conf just open with gedit and past here the content inside a quote.

---

### Post by florian_monfort on 2011-08-08
Here is the content of the xorg.conf file, while I am using only the 23" screen at 1776x1000 resolution :

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:0:1:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[0]-1"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:0:1:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[0]-1"
	Device     "amdcccle-Device[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Hope this will help ...

---

### Post by SalHelder on 2011-08-08
Lets try editing the file.

1. First of all make a backup:
su -
cd /etc/X11
cp xorg.conf xorg.conf.bak

2. Run gedit as root:

gedit

3. First the Laptop, go to the section that says:

"Section "Screen"
 Identifier "aticonfig-Screen[0]-0"
 Device "aticonfig-Device[0]-0"
 DefaultDepth 24
 SubSection "Display"
 Viewport 0 0
 Depth 24
 EndSubSection
 EndSection"

Before the Replace:
"SubSection "Display"
 Viewport 0 0
 Depth 24
 EndSubSection"
with this:

>     Subsection "Display"
        Viewport 0 0
        Depth 8
        Modes "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection
    
    Subsection "Display"
        Viewport 0 0
        Depth 16
        Modes "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection
    
    Subsection "Display"
        Viewport 0 0
        Depth 24
        Modes "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection

4. Now the Monitor, in:
"Section "Screen"
 Identifier "amdcccle-Screen[0]-1"
 Device "amdcccle-Device[0]-1"
 DefaultDepth 24
**> SubSection "Display"
 Viewport 0 0
 Depth 24
 EndSubSection<***
 EndSection"

With this:

>     Subsection "Display"
        Viewport 0 0
        Depth 8
        Modes "1920x1080" "1600x900" "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection

    Subsection "Display"
        Viewport 0 0
        Depth 16
        Modes "1920x1080" "1600x900" "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection
    
    Subsection "Display"
        Viewport 0 0
        Depth 24
        Modes "1920x1080" "1600x900" "1366x768" "1280x720" "1024x576" "854x480" "640x360"
    EndSubsection

5. Restart the session, if anything goes wrong, try accessing the tty terminal, using Ctrl + Alt + F1 and then type:

su
cd /etc/X11
mv xorg.conf.bak xorg.conf
reboot

I also hope this works.

---

### Post by florian_monfort on 2011-08-08
I'll try this in a few minutes. Something else strikes me, it's that when I arrived to the desktop and I went to the Monitors window, it displays "1900x1080" while my screen was displaying in 1776x1000. And at the same time it was kinda "blured", if you see what I mean, and when I selected 1776x1000 and applied, it became clean ... Or "precise" like it was trying to display at 1900x1080 but the screen would "reduce it"...

---

### Post by SalHelder on 2011-08-08
Honestly I find this very weird, 'cause I never had any issue connecting with Linux computers/laptops either using VGA and HDMI to projectors/monitors at all, I don't get what is wrong here.

---

### Post by florian_monfort on 2011-08-08
I can't use the command su : O.o

monfort@monfort-HP-Pavilion-dm1-Notebook-PC:~$ su
Password: 
su: Authentication failure
monfort@monfort-HP-Pavilion-dm1-Notebook-PC:~$ 

I do enter the correct password because I can use the sudo command without any problem.
Am I supposed to use another password ?

---

### Post by SalHelder on 2011-08-08
Ok... Have you created more than one user? It doesn't matter anyway:

1.
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak

2.
gksudo gedit xorg.conf

I forgot one thing, if you need to resort to the tty, you need to enter with your username and then use the "new" commands:

cd /etc/X11
sudo mv xorg.conf.bak xorg.conf
sudo reboot

---

### Post by florian_monfort on 2011-08-08
Well it wasn't the right solution ...

After saving the file, I clicked on "log out" and all I got was a deactivated 23" screen and twho command lines on the laptop screen ...

After reboot by using the power button, I couldn't get further than the Plymouth Splash screen so ...

---

### Post by SalHelder on 2011-08-08
I pretty much ran out of ideas... I can point you out to a few links that may help:

[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers&highlight=ati+6310](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers&highlight=ati+6310)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[http://ubuntuforums.org/showpost.php?p=10449816&postcount=26](http://ubuntuforums.org/showpost.php?p=10449816&postcount=26)

---

### Post by florian_monfort on 2011-08-08
Well, I have wasted enough time on this.

---

### Post by florian_monfort on 2011-08-08
I will use Seven most of the time, and keep Ubuntu on another partition until better drivers/support/versions. Thanks for your help though !

---

### Post by florian_monfort on 2011-08-13
I have news now. I plugged in the screen with VGA, and I now have full resolution on both screens but still not good colors on the 23" screen...

---

