---
title: "installation help Intrepid"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by forestwalkerjoe on 2009-01-21
Ok.. got two seperate problems.. but lets start with this one. 
In the past i trialed Ubuntu.. long time back. 7.04. 
Some thing happend and i had to remove it and trialed another 8 other linux distro's. 
Then when i was picking JUST ONE.. i lost my mentor helper and never got past removing all my Distros. SO.. i have been without linux for over a year.. 
NOW i have purchased a CD of what they called  UBUNTU LINUX 09.. or 8.10 Intrepid. 
I am no weener.. but i am also very spooked by partitions. I have vinders on the first part. and i DID make a set of partitions.. they are 80 odd gig to place what i think you call the root.. and 4.5 gig for.. some thing.. not sure.. and 8. some.. for the .. i think its called swap. The default on the LIVE CD Install guide is for it to take over the whole drive. The other option is the Manual install. which pulls up my first NTFS drive.. shows the partitions i made after.. and asks for a root. I place root on the 80 gig. and then.. i have NO IDEA what to call the other two.. do i make them EXT 3's and then if i do.. how to I make the 3 needed partitions? can some one help me by explaining what i really need here.. and then.. if i can get past the choices there.. i can finish my install? i am typing off the LIVE USER CD now. My windows is fine.. but i figured is some one IS going to help me.. maybe we can have them take a look in Terminal thing if needed.. but.. i wont proceed with out some one .. making sure i dont complely mess up my drive. NOW.. after that.. it gets fun. 
I have a family that i have been friends with for years. 
I have talked about various experience in LINUX.. and they have been massively corrupted by some agressive virus and Trojan/mal ware things. 
I have spent hours removing.. doing REG EDITS to remove the auto runs.. they have.. got rid of BHO's in there IE 7 arrg. done every thing i know how.. ran net based removers.. root kit removers.. ad aware.. SPY BOT.. heck Glary utils. found the Gateway virus and read up.. and its coming to the point that they will need to either take back to factory.. as they have ONLY a set of Factory restore disks.. and FIGHT TO FIND EAch and every driver to make the dern thing work again.. or GET SOME ONE HERE TO HELP ME INSTALL UBUNTU.. and then.. use some of the work arrounds i have heard about.. for using windows e xe files or disks.. or even.. set up ACTIVE SYNC like stuff for their 4 phones that sync on windows.. a ZUNE and so on. 
these might be out of the box.. but if they are not.. and i do the ONLY linux install.. they are gonna be pissed. i want them to have the best FIRST CONTACT with LINUX as can be. they have little to no access to the net with their present windows system. I put in a LIVE CD of PCLINUX and its working for now.. but i want some thing very supported.. well documented to work with the greatest amount of hardware etc.. any one bait? i'll really need the help to bring a family of 4 to the " KINGDOM" so to speak. 
FWJ

---

### Post by Partyboi2 on 2009-01-21
Can you open a terminal (Applications>Accessories>Terminal) from the live cd and post the output to
```
sudo fdisk -l
``` (Small L) this will give us a better idea what your partition situation is.

---

### Post by pytheas22 on 2009-01-21
Since you already have Windows on the computer that you want to add Ubuntu to, you might want to use [wubi]("http://wubi-installer.org/faq.php") instead of the live CD.  wubi doesn't require partitioning, and you can install it right from within Windows.

Otherwise, we can help you figure out how to configure partitions if you post the output of 'sudo fdisk -l' while running the live CD, as asked for above.

---

### Post by forestwalkerjoe on 2009-01-22
ok.. i am not sure why SUDOing  F-disk is safe.. isn't FDISK a type of complete format code? 
I know nothing.. so i will trust you on that. 
Second.. more funny.. A " WUBBI?" is that like a Rassberry? or a WOOGIE MAN? 
I am to assume then that WUBI is a type of VM or virutal box type thing? i had the hardest time in my own vinders set up just last week.. Trying to get Ubuntu 7 installed into the Virtual Box. 
it would get to the whole install set up kernal stuff and then show me a Tan screen with nothing on it.. and freeze. it was my first choice to either install for them.. Windows with LINUX in VB.. or if all failed.. ATTEMPT to do a full install of UBUNTU on their system and then try a VBox to install their windows.. but their windows are on RESTORE TO FACTORY DISK.. and i was sure that it would take over the whole drive and whipe and really install back to factory. 
Whats WUBI like? is it easier to install VBox style stuff that VBox is? 
also.. i , as i said, live CD'd the newer Ubuntu.. and Dang if i cant figure out how to get the BERYL style FIRE close and FIRE open feature working. Maybe its not on LIVE CD? It does do the RUBBER pages.. that bounce and move when you move the page or close them. and IS very cool looking. yet i wanted to give them all the special features that ya got so they are WOWED and amazed. i guess for now.. the WOW factor will have to be that i saved their system. 
I am also suspecting that their 16 gigs of music .. largely downloaded will have issues with windows Digital management code. and NOT open or work ON this new install of Ubuntu we are going to do? 
that is half the reason i wanted to do a duel boot.. then they can use their URGE and a few other programs windows uses to re validate their music digitally.. and not loose anything. 
I'll get back to you when i can get more PC info from them. 
but answers to the above will help me make better choices when we continue the actual venture.. thanks for being my new forum. 
FWJ

---

### Post by pytheas22 on 2009-01-22
wubi is not a virtual machine.  It creates a 100% real Ubuntu installation, just like the live CD.  The only difference is that a system installed via wubi stores its files inside your Windows drive, while the live CD would create a dedicated partition for Ubuntu, separate from Windows.  But this difference doesn't really impact the user experience in any noticeable way, and wubi should be quite easy to install; this is all you have to do:

[IMG]http://wubi-installer.org/images/wubi-123_small.png[/IMG]

Then click 'Install' and it does the rest.  It's easier to use than even the live CD.

As for your other concerns:

-you need to install compizconfig-settings-manager to get the fire effect working, I think.  You could install it in the live session if you wanted through Synaptic or Add/Remove Programs.  After installing it, you can launch it from the System>Preferences>Advanced Desktop Effects Settings menu.
-your digitally-protected music might play on Ubuntu or it might not, depending on how exactly it's protected.  There's probably a way to work around it though, but we can deal with that when the time comes.
-if you want the full Ubuntu experience, don't install it inside a virtual machine.  There are limitations on the virtual machine; for example, desktop effects (including the fire effect) won't work there because 3D-acceleration is not possible in a virtualized environment.

Also, it would be helpful if you could please separate your paragraphs with blank lines in future posts...it makes things easier to read.

---

### Post by stunnedandconfused on 2009-01-25
> **pytheas22 said:**
> wubi is not a virtual machine.  It creates a 100% real Ubuntu installation, just like the live CD.  The only difference is that a system installed via wubi stores its files inside your Windows drive, while the live CD would create a dedicated partition for Ubuntu, separate from Windows.  But this difference doesn't really impact the user experience in any noticeable way, and wubi should be quite easy to install; this is all you have to do:

[IMG]http://wubi-installer.org/images/wubi-123_small.png[/IMG]

Then click 'Install' and it does the rest.  It's easier to use than even the live CD.

As for your other concerns:

-you need to install compizconfig-settings-manager to get the fire effect working, I think.  You could install it in the live session if you wanted through Synaptic or Add/Remove Programs.  After installing it, you can launch it from the System>Preferences>Advanced Desktop Effects Settings menu.
-your digitally-protected music might play on Ubuntu or it might not, depending on how exactly it's protected.  There's probably a way to work around it though, but we can deal with that when the time comes.
-if you want the full Ubuntu experience, don't install it inside a virtual machine.  There are limitations on the virtual machine; for example, desktop effects (including the fire effect) won't work there because 3D-acceleration is not possible in a virtualized environment.

Also, it would be helpful if you could please separate your paragraphs with blank lines in future posts...it makes things easier to read.

Hi, I have put Wubi on my sony vaio desktop but can only get to the ubuntu screen with the orange squares, all squares get filled, I hear a short blast of music and then nothing happens, anyone have any ideas as to whats going wrong? I decided to put Wubi into its own partition on my HD and get a prompt at boot asking if I want to boot in Vista or Ubuntu. As said above, it loads the orange squares, plays a litle music and then simply just hangs with a blank black screen.

System = Vista Home Premium
32 bit
3gb memory
Intel Core2 duo
Intel G45/G43 Express Chipset.

I did try to upload Ubuntu via live CD but that also failed, although, I could use the CD to try Ubunto OK. Had the same problem with the black screen when trying to upload to computer proper from the CD.

Thanks in advance.

---

### Post by pytheas22 on 2009-01-25
stunnedandconfused: what happens if you press control-alt-backspace while it's hanging?  What is the exact model of your laptop?  It may also help to defragment your hard drive in Windows, then reinstall wubi.

---

### Post by stunnedandconfused on 2009-01-26
> **pytheas22 said:**
> stunnedandconfused: what happens if you press control-alt-backspace while it's hanging?  What is the exact model of your laptop?  It may also help to defragment your hard drive in Windows, then reinstall wubi.

When I press "Control-Alt-Backspace", it runs a check, 6 items checked and all marked [OK], the last listed check is a battery check?. Screen goes totally black and get the drumroll again and hangs there. If I leave it about 5 minutes, it defaults and loads Vista as normal.

The computer is not a laptop, its a desktop, Sony Vaio JS1E

When I used the livecd and chose the safe graphics mode (I think thats what I read on here), it allowed me to use Ububtu, connect to the internet etc but couldnt use the CD to install, black screen and just hung, but without the drumroll music.

---

### Post by pytheas22 on 2009-01-26
stunnedandconfused: unfortunately I couldn't find any indication on the Internet of anyone else having problems with this computer and Linux, so I'm not sure why it doesn't want to work for you.  Could you try burning an Ubuntu 8.04 CD and see if that works better than 8.10?

If 8.04 also fails, we can try to get some output from logs to see if that leads to a solution.

You could also [file a bug report]("http://www.ubuntu.com/community/reportproblem") to get attention from Ubuntu developers.

---

### Post by stunnedandconfused on 2009-01-26
> **pytheas22 said:**
> stunnedandconfused: unfortunately I couldn't find any indication on the Internet of anyone else having problems with this computer and Linux, so I'm not sure why it doesn't want to work for you.  Could you try burning an Ubuntu 8.04 CD and see if that works better than 8.10?

If 8.04 also fails, we can try to get some output from logs to see if that leads to a solution.

You could also [file a bug report]("http://www.ubuntu.com/community/reportproblem") to get attention from Ubuntu developers.

Hi, Thanks for looking into this for me.

I downloaded the 8.04 Alternate CD and tried to install that, I got to an impass after partitioning the main HD section, when I clicked to move on, one of the options required was not configured (or configured correctly), I went back but could not see not see an option that had not been amended. 
I have now made a total of 10 different CDs and still cannot get this to work.
Hey ho, I guess, Im just supposed to live Ubuntu free.
Thanks again.

EDIT-
I have just tried the livecd again and selected the try without installing, the load screen worked and then their was the full sound (not just part as mentioned above with wubi install), the screen still stays black. To me, in my limited knowledge, it seemd as though it was loaded but just the screen would not display ubuntu for some reason. When I chose the limited graphics option, ubuntu loaded and i could access the interent fine, obviously limited size window which could not be changed by trying to configure it larger from the ubuntu windows.

Is my problem simply down to the graphics card? As its a brand new machine (all in one system) I would have assumed that it would have handled Ubuntu OK.

---

### Post by pytheas22 on 2009-01-26
From the sounds of things, it's likely that the graphics card is the problem.  Do you know what kind of card it is and the exact model?

If you press control-alt-F2 at any point after Ubuntu has loaded (or if you log in under safe graphics mode and open a terminal from the Applications>Accessories menu), you will be brought to a command prompt.  If you log in there and type:
```

lspci -nn | less
```

you will get a list of your hardware that you'll be able to scroll through.  One line in the list will describe your graphics card--it should mention something like 'VGA controller' or 'video device'.  Could you please copy down that whole line and post it here?

If your problem does come down to the video device, it shouldn't be too hard to fix it, so don't give up yet.

---

### Post by stunnedandconfused on 2009-01-26
> **pytheas22 said:**
> From the sounds of things, it's likely that the graphics card is the problem.  Do you know what kind of card it is and the exact model?

If you press control-alt-F2 at any point after Ubuntu has loaded (or if you log in under safe graphics mode and open a terminal from the Applications>Accessories menu), you will be brought to a command prompt.  If you log in there and type:
```

lspci -nn | less
```

you will get a list of your hardware that you'll be able to scroll through.  One line in the list will describe your graphics card--it should mention something like 'VGA controller' or 'video device'.  Could you please copy down that whole line and post it here?

If your problem does come down to the video device, it shouldn't be too hard to fix it, so don't give up yet.

The Graphics card is as follows-
Intel® Graphics Media Accelerator X4500HD (found on the Vaio website).
On the Intel website driver scan it states it is an -

Intel® G43/G45
Number 7.15.10.1511 (followed by "Customized computer manufacturer driver detected. Please contact the computer manufacturer for possible updates."

Not sure where that leaves me?

---

### Post by pytheas22 on 2009-01-26
> The Graphics card is as follows-
Intel® Graphics Media Accelerator X4500HD (found on the Vaio website).

Yes, it seems that this card has some serious issues with Linux, because it's new and the drivers haven't caught up with it yet.  See for example [this thread]("http://ubuntuforums.org/showthread.php?t=889323") and this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/271059").

One solution that seems to work for some people is to add the NoAccel option to xorg.conf.  To do that, first boot to your Ubuntu 8.10 install (not the live CD, but the real system installed to your hard drive).  Log in in safe graphics and open a terminal.  Then type:
```

sudo gedit /etc/X11/xorg.conf
```

A text file will pop open.  Look for this section:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Add in the NoAccel option so that the section looks like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        **Option          "NoAccel"**
EndSection
```

Then save the file and reboot your computer.  Is the behavior any different?

---

### Post by stunnedandconfused on 2009-01-26
> **pytheas22 said:**
> Yes, it seems that this card has some serious issues with Linux, because it's new and the drivers haven't caught up with it yet.  See for example [this thread]("http://ubuntuforums.org/showthread.php?t=889323") and this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/271059").

One solution that seems to work for some people is to add the NoAccel option to xorg.conf.  To do that, first boot to your Ubuntu 8.10 install (not the live CD, but the real system installed to your hard drive).  Log in in safe graphics and open a terminal.  Then type:
```

sudo gedit /etc/X11/xorg.conf
```

A text file will pop open.  Look for this section:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Add in the NoAccel option so that the section looks like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        **Option          "NoAccel"**
EndSection
```

Then save the file and reboot your computer.  Is the behavior any different?

What do I have to use to get into safe graphics mode? I have done it once and forgotten :( and do you mean the wubi install? Also, apart from Wubi, I have no other version on my HD.

---

### Post by pytheas22 on 2009-01-26
There should be an option at the login screen where you can select to log in in safe graphics mode (otherwise known as "Failsafe Gnome").  Alternatively, you could open your xorg.conf file for editing by pressing control-alt-F2, logging in there, and typing:
```

sudo nano /etc/X11/xorg.conf
```

And yes, this should be done on your wubi installation.

---

### Post by stunnedandconfused on 2009-01-26
> **pytheas22 said:**
> There should be an option at the login screen where you can select to log in in safe graphics mode (otherwise known as "Failsafe Gnome").  Alternatively, you could open your xorg.conf file for editing by pressing control-alt-F2, logging in there, and typing:
```

sudo nano /etc/X11/xorg.conf
```

And yes, this should be done on your wubi installation.

When I boot with the drive containing ubuntu, there is no options screen, the ubuntu programme simply tries to load itself straight off.

---

### Post by pytheas22 on 2009-01-26
In that case, you'll have to use the text-based editor to edit xorg.conf (I'm not sure how you would have gotten into failsafe mode before, unless the system defaulted there on its own).  After Ubuntu hangs, press control-alt-F2.  This should bring you to a prompt.  Log in, then type:
```

sudo nano /etc/X11/xorg.conf
```

Use the arrow keys to scroll down to the "Device" section, and add in the NoAccel line so that the entire section looks like:
```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "NoAccel"
EndSection
```

Then press control-O to save the file, and control-X to exit nano.  Reboot your computer by typing:
```

sudo reboot
```

Any luck?

---

### Post by stunnedandconfused on 2009-01-27
> **pytheas22 said:**
> In that case, you'll have to use the text-based editor to edit xorg.conf (I'm not sure how you would have gotten into failsafe mode before, unless the system defaulted there on its own).  After Ubuntu hangs, press control-alt-F2.  This should bring you to a prompt.  Log in, then type:
```

sudo nano /etc/X11/xorg.conf
```

Use the arrow keys to scroll down to the "Device" section, and add in the NoAccel line so that the entire section looks like:
```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "NoAccel"
EndSection
```

Then press control-O to save the file, and control-X to exit nano.  Reboot your computer by typing:
```

sudo reboot
```

Any luck?

Tried that and it has made no difference, still hangs.

I decided to use the liveCD again in "Restricted Graphics mode" and all worked well, I hit the desktop "Install" and it has installed but with the restricted graphics display (never thought it would install only at the restricted though).

Not quite sure what to do next, obviously I can connect to the internet etc and use ubuntu in its current restricted state but would rather have the full screen at some point.
Thanks again for your assistance so far :)

---

### Post by pytheas22 on 2009-01-27
It's good that you at least got it installed in safe graphics mode.  If you open a terminal under your new installation and type:
```

cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

what is the output?

---

### Post by stunnedandconfused on 2009-01-27
> **pytheas22 said:**
> It's good that you at least got it installed in safe graphics mode.  If you open a terminal under your new installation and type:
```

cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

what is the output?

When and how do I open a terminal?

---

### Post by pytheas22 on 2009-01-27
> When and how do I open a terminal?

Boot into failsafe graphics mode, then go to Applications>Accessories>Terminal.

---

### Post by stunnedandconfused on 2009-01-27
> **pytheas22 said:**
> Boot into failsafe graphics mode, then go to Applications>Accessories>Terminal.

Im sure you could have guessed the next question ;-)

How do I boot in failsafe graphics mode?

Im using Ubuntu now wahoo!!! Sorry, a bit excited that its working at all.

---

### Post by pytheas22 on 2009-01-27
> How do I boot in failsafe graphics mode?

That should be what you're in already if you're using Ubuntu.  In the upper-left corner, you should see the Applications menu.  Click it, then go to Accessories and you'll see the terminal.

---

### Post by stunnedandconfused on 2009-01-27
> **pytheas22 said:**
> That should be what you're in already if you're using Ubuntu.  In the upper-left corner, you should see the Applications menu.  Click it, then go to Accessories and you'll see the terminal.

Here is what happened-

	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 169
	LinNumberOfImagePages: 169
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 106
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 106
	LinNumberOfImagePages: 106
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 135
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 135
	LinNumberOfImagePages: 135
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 67
	LinNumberOfImagePages: 67
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 152
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 152
	LinNumberOfImagePages: 152
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 254
	LinNumberOfImagePages: 254
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000668a
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 203
	LinNumberOfImagePages: 203
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 2047 64KB banks (131008kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 131008 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Eaglelake Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Eaglelake Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0xaf937000,
	physical address = 0xd0000000, size = 134152192
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PIXART USB OPTICAL MOUSE
(**) PIXART USB OPTICAL MOUSE: always reports core events
(**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event3"
(II) PIXART USB OPTICAL MOUSE: Found x and y relative axes
(II) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
(II) PIXART USB OPTICAL MOUSE: Configuring as mouse
(II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
(**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
(**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Innovace USB Keyboard
(**) Innovace USB Keyboard: always reports core events
(**) Innovace USB Keyboard: Device: "/dev/input/event2"
(II) Innovace USB Keyboard: Found 5 mouse buttons
(II) Innovace USB Keyboard: Found keys
(II) Innovace USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Innovace USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Innovace USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Innovace USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Innovace USB Keyboard: xkb_layout: "gb"
(**) Innovace USB Keyboard: YAxisMapping: buttons 4 and 5
(**) Innovace USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Innovace USB Keyboard
(**) Innovace USB Keyboard: always reports core events
(**) Innovace USB Keyboard: Device: "/dev/input/event1"
(II) Innovace USB Keyboard: Found keys
(II) Innovace USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Innovace USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Innovace USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Innovace USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Innovace USB Keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event6"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Sony Vaio Keys: xkb_layout: "gb"


and

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by pytheas22 on 2009-01-27
Yes, you're using the 'vesa' driver, which is a failsafe generic driver that provides only limited screen resolution.

Let's give the NoAccel option another try, because everything I read says that it's likely to help.  To add the option in, log into Ubuntu in failsafe mode, open a terminal and type:
```

cp /etc/X11/xorg.conf ~/Desktop
```

to backup your existing file.  Then type:
```

sudo gedit /etc/X11/xorg.conf
```

Erase the contents of the file that opens, and paste these in in its place:
```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "NoAccel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Then save the file, log out of the desktop and log back in.  If your screen doesn't crash, please post the output again of:
```

cat /etc/X11/xorg.conf
```

If your screen does crash, please follow these steps to fix it:

1. press control-alt-F2 and log in on that terminal
2. type:
```

sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf
```

Press control-alt-F7, then wait a few seconds and press control-alt-backspace.  At this point your screen should work again using the failsafe settings.

---

### Post by stunnedandconfused on 2009-01-27
> **pytheas22 said:**
> Yes, you're using the 'vesa' driver, which is a failsafe generic driver that provides only limited screen resolution.

Let's give the NoAccel option another try, because everything I read says that it's likely to help.  To add the option in, log into Ubuntu in failsafe mode, open a terminal and type:
```

cp /etc/X11/xorg.conf ~/Desktop
```

to backup your existing file.  Then type:
```

sudo gedit /etc/X11/xorg.conf
```

Erase the contents of the file that opens, and paste these in in its place:
```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "NoAccel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Then save the file, log out of the desktop and log back in.  If your screen doesn't crash, please post the output again of:
```

cat /etc/X11/xorg.conf
```

If your screen does crash, please follow these steps to fix it:

1. press control-alt-F2 and log in on that terminal
2. type:
```

sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf
```

Press control-alt-F7, then wait a few seconds and press control-alt-backspace.  At this point your screen should work again using the failsafe settings.

Back to square one again, and Vista, no screen showing loading, music OK so assume its still trying as it did before I did the install that worked. The screen crashed and when I entered the code you gave, it said-

cp. missing destination file operand after home/name/Desktop/xorg.conf/etc/X11/xorg.conf

EDIT

Just booted Ubuntu again, ran sudo nano /etc/x11/xorg.conf(it was totally empty) and typed in the code you gave me the other day 

Section "Device"
        Identifier    "Configured Video Device"
        Option        "NoAccel
EndSection

and saved it, hey presto, ubuntu desktop back after typing

 sudo reboot

The saved file now appears to be residing on my desktop!?!?   

When opened it states the following

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Should I simply leave it alone or would you suggest the above can be tweaked?

---

### Post by pytheas22 on 2009-01-27
> The saved file now appears to be residing on my desktop!?!? 

Yes, because you created a backup copy of it before so that you could fall back to that copy (the one that Ubuntu created by default) in case of problems.
> 
The screen crashed and when I entered the code you gave, it said-

cp. missing destination file operand after home/name/Desktop/xorg.conf/etc/X11/xorg.conf

That happened because of a typo.  The correct command would have been:
```

sudo cp ~/Desktop/xorg.conf          /etc/X11/xorg.conf
```

Notice the space (you only need one space but I put several in above to make it clear).

I'm not positive where to go next, but if you could please post the output of this command, it would be helpful:
```

lspci -nn
```

Also, some things I've read suggest that this card would work out-of-the-box with Fedora 10, so if you have time and feel like burning another live CD, you may want to give that a try.  The card should also be supported when Ubuntu 9.04 is released in April, but until then it's probably not going to be fun to use under Ubuntu.

---

### Post by forestwalkerjoe on 2009-01-28
ok. I have recently left my issues for installing Ubuntu Intrepid and it was suggested i should install at home first .. then learning a bit.. try my install on the Host family.. i had been talking about. 
I chose some thing less likely to mess up my home PC. 
i have an older lap top.. and it has a PCMCIA card slot that works on this Card. 

SOHOware Ethernet Adapters PCMCIA
ND5120-E
My install went well.. i have it duel booted.. but can not connect to the NET and update. 
I am told there are work arrounds for the PCMCIA card.. but i can not make heads or tails of these. 
Most SOHOWARE PCMCIA cards of my numbering will recognize as MACRONICS brand.. it says. and some of these have downloadable or Terminal based FIXS.. but heck if i can understand a word of them. [http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm]("http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm")
Can some one please help me config the PC CARD in my laptop so i dont think i have messed up my lappy permanently? once connected to the net i can update every thing and it will be fully useable LAPTOP. i was trying to use the lap top so i could take it to the families house and use that for net connection while i talk to one of you to solve THEIR issues. i was also going to try the idea.. shown on a web site.. of "IN A DUEL BOOT" connecting the  shell. here is the link :[http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/]("http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/") once i can do that on my lap top i will try doing it on my own system then i'll set it up on the Host families system. Therefor alowing them to have Ubuntu running.. and use the few Windows require items they have.. INSIDE ubuntu. but first things first.. i can not do any of this with out the connection to the net.. please PLEASE help me out. the big sell point on ubuntu is that there is patient HELPFUL forums out there. i am going to hope that you all will help me out. 
FWJ

---

### Post by forestwalkerjoe on 2009-01-28
you are mixing up my requests. the LAP TOP is the one i am trying to get a connection to. 
I am not at this time interested in doing a WUBBY. i am interested in working out the issues with the Full install i have on the lap top.. which will be a support lap for the full instalation on the families PC i was telling you about. 
to the best of my ability here is the output on the Fdisk dash "L" .. i had to do it twice as i thought that was a I or a ONE. 
rj@rj-laptop:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
16 heads, 63 sectors/track, 58140 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x96819681

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24401    12297726    c  W95 FAT32 (LBA)
/dev/sda2           24401       58140    17004802+   5  Extended
/dev/sda5           24402       40654     8191480+  83  Linux
/dev/sda6           40655       44970     2175232+  82  Linux swap / Solaris
/dev/sda7           44971       58140     6637648+  83  Linux

Disk /dev/sdb: 8000 MB, 8000004096 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb193ae7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         972     7807558+   b  W95 FAT32
rj@rj-laptop:~$

as i said in the other notes.. i have a SOHOWARE PCMCIA ND5120 E ethernet card here. I need to get the support for "IT" so i can connect to the net.. then i can move onto the more adventurous ideas. 
ONCE this lap is set up .. i will not feel so broke up on my use of Ubuntu. HELP me fix this.. and then i can move onto the other issues. IF i cant get help with the lap.. then i was justified for using the lap as a TEST. if this were to happen on the full install on MY PC or the Host families PC.. we personally , would be messed up. 
once i can see the support.. i'll be glad to add 2 more PC's to the family. 
IF the PCMCIA card is hopeless.. i do have an on board old style modem on here.. but it is not recognized by Default. I did do a download and saved the text for the modem too. 
IF you ask.. i'll put that up as well. I used the scanModem.gz thing and followed a text explaining how to install it and use it. 
output by request.. 
FWJ

---

### Post by stunnedandconfused on 2009-01-28
> **pytheas22 said:**
> Yes, because you created a backup copy of it before so that you could fall back to that copy (the one that Ubuntu created by default) in case of problems.


That happened because of a typo.  The correct command would have been:
```

sudo cp ~/Desktop/xorg.conf          /etc/X11/xorg.conf
```

Notice the space (you only need one space but I put several in above to make it clear).

I'm not positive where to go next, but if you could please post the output of this command, it would be helpful:
```

lspci -nn
```

Also, some things I've read suggest that this card would work out-of-the-box with Fedora 10, so if you have time and feel like burning another live CD, you may want to give that a try.  The card should also be supported when Ubuntu 9.04 is released in April, but until then it's probably not going to be fun to use under Ubuntu.

Hi Pytheas,

Well, after a lot of messing, I used the uninstal from a forum post and all is well again on my brand new vaio, although some will think Im mad for even starting this at all ;)

I did download Fedora 10 and try to install it, and guess what, blank black screen, again. I will just have to wait and see what develops in the next Ubuntu release (any idea when, roughly?).

Thanks for all of your help and making this a rich and friendly learning experience for me as a newbie to linux, it will stand me in good stead at a later date hopefully.

---

### Post by pytheas22 on 2009-01-28
> you are mixing up my requests. the LAP TOP is the one i am trying to get a connection to.
I am not at this time interested in doing a WUBBY. i am interested in working out the issues with the Full install i have on the lap top..

**forestwalkerjoe**: I don't see ethernet problems mentioned in any of your previous posts in this thread.  Are you sure you're not confusing this thread with another one?

Anyway, in order to figure out why your ethernet connection isn't working on the laptop, please post the output of these commands:
```

lshw -C Network
dmesg | grep eth
lspci -nn
ifconfig
```

I need that information in order to figure out what's wrong.

> 
Well, after a lot of messing, I used the uninstal from a forum post and all is well again on my brand new vaio, although some will think Im mad for even starting this at all

I did download Fedora 10 and try to install it, and guess what, blank black screen, again. I will just have to wait and see what develops in the next Ubuntu release (any idea when, roughly?).

Thanks for all of your help and making this a rich and friendly learning experience for me as a newbie to linux, it will stand me in good stead at a later date hopefully.

**stunnedandconfused**: I'm glad your problem is resolved.  Is your Vaio still running in limited-graphics mode, or is it working normally?  Could you please provide a link to the thread that you used to solve the problem, just for the benefit of anyone else who reads this thread?

The next release of Ubuntu will be this April; hopefully your video card will 'just work' in that version.

---

### Post by stunnedandconfused on 2009-01-28
> **pytheas22 said:**
> **stunnedandconfused**: I'm glad your problem is resolved.  Is your Vaio still running in limited-graphics mode, or is it working normally?  Could you please provide a link to the thread that you used to solve the problem, just for the benefit of anyone else who reads this thread?

The next release of Ubuntu will be this April; hopefully your video card will 'just work' in that version.

My Sony is fine, the uninstall for Ubuntu is here [LINK]("http://ubuntuforums.org/showthread.php?t=113630"), no matter what I did, I couldnt get to full screen, just restricted and decided to get the best out of Ubuntu that I would be better off waiting for a version that would work at its best, unrestricted. 

I had tried to remove Ubuntu manually but that did create the boot "Grub" problen as mentioned in the removal link above. When the computer would only show the "Grub" error alone at boot, the only thing I could think of was to reinstal Ubuntu again to bring the "Grub" error back in line. It was after doing this that I found the uninstall link.

As said, I am looking forward to using Ubuntu in full mode one day pretty soon. Thanks again.

---

### Post by donaldt on 2009-01-28
I believe I see a pattern.  I have a sony vaio laptop, windows vista system.  I have tried 3 cd's, 2 dvd's and all hang during the install just after the horizontal barometer does it's last crawl across the screen.

I sometimes get the large X in the middle of the next screen, but that is the last trace of Ubuntu that shows up on the computer.  The screen is totally blank and nothing comes up.  I had the same problem trying to install on an old IBM T-20 portable with an outdated BIOS (dated late 1999).  Is my only choice to wait for another iteration of the software, or is there a work around?

In order to avoid mixing Ubuntu and Vista (I have been told that dual boots end up corrupting the Vista OS) I am now going to install Linux on an external hard drive.  I believe I can do that if I could ever get past the totally black screen and a dead end during numerous attempts to install.

Interestingly, I have on two or three occasions been able to install Ubuntu to both the Sony laptop Vista computer and the old T-20, but after closing them out they are mysteriously missing from any access I can summon up.

Any ideas would be welcome.  I am not a Vista fan and have been trying to set up a good Linux system for the last 8 years.  I thought the GUI that Ubuntu provided was a real break through.  It may be, but has not proven to be one for me.

Thanks...

---

### Post by pytheas22 on 2009-01-29
donaldt: the problems with the black screen described by stunnedandconfused result from his hardware being very new and not yet supported by the video driver that ships with Ubuntu 8.10 and earlier.  [This thread]("http://ubuntuforums.org/showthread.php?t=889323") deals with the issue.  Ubuntu 9.04, which will be released in April, should support his video card.

Your laptop may indeed have the same video card and hence the same problem, but it could be something else.  Do you know what kind of video device you have?

If you do have the same video card, your options at this point, besides waiting for Ubuntu 9.04, are:

1. install Ubuntu using the [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  It has a text-based installer, but don't be scared; it's not that hard to use.  It should allow you to install Ubuntu without a problem.

Once you've installed using the alternate CD, boot to Ubuntu.  When the display crashes, press control-alt-F2.  This should bring you to a command prompt.  Log in there, then type:
```

sudo nano /etc/X11/xorg.conf
```

A file will open.  Use the arrow keys to scroll through it.  Look for a section that looks like this:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Add in a line so that it looks like this:
```

Section "Device"
        **driver          "vesa"**
	Identifier	"Configured Video Device"
EndSection
```

Press control-o to save the file, and control-x to exit the text editor. Then reboot your computer by typing:
```

sudo reboot
```

After the reboot, you should be able to log into Ubuntu graphically, although your screen resolution will be low.

2. there are some work-arounds in [this thread]("http://ubuntuforums.org/showthread.php?t=889323") that may help you.  I can help you apply them if you can't figure it out, but it would be helpful if you could first follow the steps above so that you can log into Ubuntu in low graphics mode; this will make it easier to try further fixes.

And again, don't assume that the source of your problem is the same as stunnedandconfused's until we know which kind of video card you have.

Also, I don't know who told you that Ubuntu can corrupt Vista, but I've never heard of that.  A couple years ago, when the Linux NTFS drivers were not that good, there were reports of people corrupting some Windows files by editing them from Linux, but since Ubuntu 8.04 this should not be a problem.  You can also mess up Windows if you edit its drive from Linux while Windows is hibernating rather than completely shut down, but as long as you're careful not to do that, it shouldn't be a problem.  If you're worried about it, just avoid mounting your Windows partition from Linux altogether--Ubuntu will only mount Windows and open up the (small) possibility for damage if you explicitly tell it to do so--and you'll have no problem.

---

### Post by stunnedandconfused on 2009-01-29
> **donaldt said:**
> In order to avoid mixing Ubuntu and Vista (I have been told that dual boots end up corrupting the Vista OS) I am now going to install Linux on an external hard drive.  I believe I can do that if I could ever get past the totally black screen and a dead end during numerous attempts to install.

Donaldt, I am a rank amateur with Linux, have Vista and have not messed up my Vista whatsoever. The information within this thread alone has helped avoid any possibilities of that. If you read the thread, take advice and make your attempts dillingently, there should be no problems.

If you continue to have problems getting Ubuntu to run, having it on an internal drive or an external drive will make no difference to its outcome.

I have decided to wait for Ubuntu 9.04 in April, I have a great computer, Vista is obviously a good system and I am not forced to make changes until they are right for my computers configuration. Its a choice we all have.

---

### Post by forestwalkerjoe on 2009-01-29
> **Partyboi2 said:**
> Can you open a terminal (Applications>Accessories>Terminal) from the live cd and post the output to
```
sudo fdisk -l
``` (Small L) this will give us a better idea what your partition situation is.
Ok. i am getting confused and i am sure some of you are also. 
the original plan has been changed or at least the focus of it. I have a Desk top of my own.. which has been suggested i use it as my test for installing Ubuntu intrepid. i also have a lap top which i am having trouble getting the drivers for the modem set up. I was going to split the lappy to WIN/Ubuntu to be a support lap for converting the FAMILY i was telling you about.. their PC to ubuntu. the trouble witht he SOHO WARE DSL ETHERCARD has made that a problem. the FDISK output below is from the lap top.. not their PC.. as i have had no ability to get back them. I now need help getting either a download to install on the laptop to make the dial out modem work.. or a work arround for the PCMCIA ethernet card.. which is a SOHOWARE ND5129-E to be seen.. so that i can connect to either my own DSL system RJ 45 cable or the host familes ATT DSL system for that support. I can not do any updates or anything on the lap top till then. So my direction is forced to be LAP TOP first. 
i also did get to download and move a GZ on my flash to the laptop called scanModem.gz and install it. it hunted for my modem and then hunted for my PCMCIA CARD.. i have placed the first output of the Fdisk first.. then i will place the out put for MODEM only.. then the out put for the PCMCIA Ether card. 
If any of you are able to see what is needed to do i can download things at home PC.. then move to flash drive.. them move to lappy.. and if you have correct Terminal code to write.. i'll try it. thank you for the very great help. 


rj@rj-laptop:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
16 heads, 63 sectors/track, 58140 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x96819681

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24401    12297726    c  W95 FAT32 (LBA)
/dev/sda2           24401       58140    17004802+   5  Extended
/dev/sda5           24402       40654     8191480+  83  Linux
/dev/sda6           40655       44970     2175232+  82  Linux swap / Solaris
/dev/sda7           44971       58140     6637648+  83  Linux

Disk /dev/sdb: 8000 MB, 8000004096 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb193ae7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         972     7807558+   b  W95 FAT32
rj@rj-laptop:~$

Modem Output from ScanModem.Gz
These are very long.. i am sorry. i will divide the first from the last with a BIG break line. dont hate me.. 



----------------------------------------------------------------

System information ----------------------------
CPU=i686,  
Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008
 scanModem update of:  2009_01_19

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 067b:2506 Prolific Technology, Inc. 
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:0a.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0a.0	127a:2005	104d:805a	Communication controller: Rockwell International HCF 56k Data/Fax Modem 

 Modem interrupt assignment and sharing: 
  9:      21565    XT-PIC-XT        acpi, uhci_hcd:usb1, ohci1394, yenta, yenta, YMFPCI
 --- Bootup diagnostics for card in PCI slot 00:0a.0 ----
[    0.986853] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fede0000, fedeffff]
[    0.986865] PCI: 0000:00:0a.0 reg 14 io port: [fce0, fce7]
[    0.986910] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.986920] pci 0000:00:0a.0: PME# disabled

 The PCI slot 00:0a.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:0a.0:
	Modem chipset  detected on
NAME="Communication controller: Rockwell International HCF 56k Data/Fax Modem "
CLASS=0780
PCIDEV=127a:2005
SUBSYS=104d:805a
IRQ=9
IDENT=HCF.HSF

 For candidate modem in:  00:0a.0
   0780 Communication controller: Rockwell International HCF 56k Data/Fax Modem 
      Primary device ID:  127a:2005
 Support type needed or chipset:	HCF.HSF
 

----------------end Softmodem section --------------

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 127a:2005 could be either a HSF or HCF Conexant modem, because of ambiguous
 use of the PCI ID by modem assemblers. First try the hcfpcimodem package.
 If the installation aborts, then use the hsfmodem package. Read DOCs/Conexant.txt
 for details and Modem/DOCs/YourSystem.txt for follow through guidance.


Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.27_7_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.01full_k2.6.27_7_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-7-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 273064 2008-10-15 18:51 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: pan0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------












then the output for the PCMCIA CARD:

--------------------------------------------------------------------

System information ----------------------------
CPU=i686,  
Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008
 scanModem update of:  2009_01_19

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 067b:2506 Prolific Technology, Inc. 
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:0a.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0a.0	127a:2005	104d:805a	Communication controller: Rockwell International HCF 56k Data/Fax Modem 

 Modem interrupt assignment and sharing: 
  9:      21572    XT-PIC-XT        acpi, uhci_hcd:usb1, ohci1394, yenta, yenta, YMFPCI
 --- Bootup diagnostics for card in PCI slot 00:0a.0 ----
[    0.986853] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fede0000, fedeffff]
[    0.986865] PCI: 0000:00:0a.0 reg 14 io port: [fce0, fce7]
[    0.986910] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.986920] pci 0000:00:0a.0: PME# disabled

 The PCI slot 00:0a.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:0a.0:
	Modem chipset  detected on
NAME="Communication controller: Rockwell International HCF 56k Data/Fax Modem "
CLASS=0780
PCIDEV=127a:2005
SUBSYS=104d:805a
IRQ=9
IDENT=HCF.HSF

 For candidate modem in:  00:0a.0
   0780 Communication controller: Rockwell International HCF 56k Data/Fax Modem 
      Primary device ID:  127a:2005
 Support type needed or chipset:	HCF.HSF
 

----------------end Softmodem section --------------

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 127a:2005 could be either a HSF or HCF Conexant modem, because of ambiguous
 use of the PCI ID by modem assemblers. First try the hcfpcimodem package.
 If the installation aborts, then use the hsfmodem package. Read DOCs/Conexant.txt
 for details and Modem/DOCs/YourSystem.txt for follow through guidance.


Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.27_7_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.01full_k2.6.27_7_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-7-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 273064 2008-10-15 18:51 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: pan0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

as said above.. once i know how to install AT THE LEAST a standard Phone Dial out modem.. i can then more easily do any upgrades to install what ever work arround is needed for the SOHOWARE DSL connection. then all will be pretty much well with the lap top. from there i can get support from you all to help me install the UBUNTU properly on the HOST computer family. 
thanks for being so helpful. 
FWJ

---

### Post by donaldt on 2009-01-29
Video card is NVidia GeForce 8400M GS, driver version 7.15.11.0128

thanks,

djt

---

### Post by forestwalkerjoe on 2009-01-29
[QUOTE=pytheas22;6635736]**forestwalkerjoe**: I don't see ethernet problems mentioned in any of your previous posts in this thread.  Are you sure you're not confusing this thread with another one?

Anyway, in order to figure out why your ethernet connection isn't working on the laptop, please post the output of these commands:
```

lshw -C Network
dmesg | grep eth
lspci -nn
ifconfig
```

I need that information in order to figure out what's wrong.


here is the best of understanding the OUTPUT you requested. As to the comment my previous posts etc. I think you are right.. i am having a problem with figuring out how to add threads that are MY issue.. instead of dropping into a thread.. i have not figured out how to do the former. 
i am sorry for the incongruity.. trying to learn and get things right. If you all will support my growth.. and help me in my vast lack of experience.. both myself and a new family will be Ubuntu'ers. thank you. the SOHOWARE ND5120-E etherenet Card was not in the PCMCIA slot when i did the commands. If this changes things let me know..and i'll pop it in and resend the OUTPUT. 
I wish some one was willing to drop me their IM .. so i could get more work done faster. I know that sounds selfish.. but i did have 3 or 4 persons willing to do this a few years ago.. when i was trying out Freespire linux OS. thank you if you all would help. 


here is the out put:

rj@rj-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:09:a9:95:4b:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rj@rj-laptop:~$ 

rj@rj-laptop:~$ dmesg | grep eth
[    8.705185] Driver 'sd' needs updating - please use bus_type methods
[    8.706069]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
rj@rj-laptop:~$ 

rj@rj-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 FireWire (IEEE 1394) [0c00]: Sony Corporation CXD3222 i.LINK Controller [104d:8039] (rev 02)
00:09.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-744B [DS-1S Audio Controller] [1073:0010] (rev 02)
00:0a.0 Communication controller [0780]: Rockwell International HCF 56k Data/Fax Modem [127a:2005] (rev 01)
00:0c.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
00:0c.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 11)
rj@rj-laptop:~$ 

rj@rj-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23156 (23.1 KB)  TX bytes:23156 (23.1 KB)

pan0      Link encap:Ethernet  HWaddr 66:09:a9:95:4b:f6  
          inet6 addr: fe80::6409:a9ff:fe95:4bf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1308 (1.3 KB)

rj@rj-laptop:~$

---

### Post by pytheas22 on 2009-01-29
**donaldt**: you have an entirely different video card than stunnedandconfused's, so the source of your problem is likely not the same.  However, please follow my instructions in post #34 anyway to try to get a failsafe graphical session started using the 'vesa' driver.  From there, it will be easier to come up with a permanent solution.

I think it might also make more sense if you started a new thread, because this one is becoming quite fractured between several completely different problems.  Please let me know the URL of your new thread and I'll reply there.
[B]
forestwalkerjoe[/B]:

First, please do run these commands again with the PCMCIA ethernet card *plugged in* and post the output:
```

lshw -C Network
dmesg | grep eth
lspci -nn
ifconfig
```

The information that you posted earlier, with the card unplugged, unfortunately isn't very useful, but hopefully the output that you get with the card plugged in will allow me to find instructions for you to get the card working.

As for the laptop's dial-up modem: I have no experience configuring a dial-up modem in Linux, but from my research my understanding is that you should follow these steps to install drivers for yours:

1. first you need to install a compiler, which is available from the Ubuntu live CD.  With your Ubuntu CD inserted into your computer, go to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, you should see a box where you can enable the use of your CD as a software repository.  Make sure this box is checked, then close the window.  Now type these commands to install a compiler from the CD:
```

sudo apt-get update
sudo apt-get install build-essential
```

2. on a computer with Internet access, go [here]("http://www.linuxant.com/drivers/") and download the 'HSF softmodem' driver (you can find the download link in the left panel of the web page).  This should give you a file called cnxinstall.run.  Transfer this file to your Ubuntu computer and save it to your desktop there.  Then run these commands on Ubuntu:
```

cd ~/Desktop
sudo sh cnxinstall.run -- --tty
```

This will start the installer.  Please post all output.

3. if the 'HSF softmodem' installer fails, delete it from your desktop, then return to [this site]("http://www.linuxant.com/drivers/") and download the 'HCF modem' driver.  Repeat the steps from (2) to transfer the installer to your computer and run it.  The HCF installer may work if HSF fails.
> 
I wish some one was willing to drop me their IM .. so i could get more work done faster.

Sorry, I don't use any chat clients, but I try to respond in the forum as quickly as my real life permits.

---

### Post by forestwalkerjoe on 2009-01-29
ok.. i THINK i did this right.. and the only part i "think" is failing , is where the machine tries to get things from the online suppositories. so here is the out put with the PC Card "IN" and the complier output. 


------------------------------------------------------------------

rj@rj-laptop:~$ sudo apt-get update
[sudo] password for rj: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
rj@rj-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6203kB of archives.
After this operation, 21.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 99820 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
rj@rj-laptop:~$ cd ~/Desktop
rj@rj-laptop:~/Desktop$ sudo sh cnxinstall.run -- --tty
sh: Can't open cnxinstall.run
rj@rj-laptop:~/Desktop$ cd ~/Desktop
rj@rj-laptop:~/Desktop$ sudo sh cnxinstall .run
sh: Can't open cnxinstall
rj@rj-laptop:~/Desktop$ sudo sh cnxinstall.run -- --tty
sh: Can't open cnxinstall.run
rj@rj-laptop:~/Desktop$ sudo sh cnxinstall .run -- --tty
sh: Can't open cnxinstall
rj@rj-laptop:~/Desktop$ sudo sh  cnxinstall.run -- --tty
sh: Can't open cnxinstall.run
rj@rj-laptop:~/Desktop$ sudo sh cnxtinstall.run -- --tty
Verifying archive integrity... All good.
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.3

Please ensure that all modems are attached to the machine.
Press enter to continue.

Detecting devices in your system... please wait...
Done.

Supported Device Detected
=========================
Name: Communication controller: Rockwell International HCF 56k Data/Fax Modem
PCI ID: 127A:2005 104D:805A
Needed packages: hsfmodem or hcfpcimodem

System Information
==================
Distribution: Ubuntu 8.10
Kernel version: 2.6.27-7-generic
Kernel architecture: x86

Determining which package(s) to install or update, please wait...
Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:00:03--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:00:04--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)

Recommended Action
==================
The following packages should be installed: hsfmodem hcfpcimodem

Do you want to install these packages ([y]/n)? y


Conexant HSF softmodem driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:00:22--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)

Press enter to continue.


Conexant HCF PCI controllerless driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:00:28--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
rj@rj-laptop:~/Desktop$ 

------------------------------------------------------------------




Then the next output. 
---------------------------------------------------------------
rj@rj-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:09:a9:95:4b:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rj@rj-laptop:~$ dmesg | grep eth
[    8.705185] Driver 'sd' needs updating - please use bus_type methods
[    8.706069]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
rj@rj-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 FireWire (IEEE 1394) [0c00]: Sony Corporation CXD3222 i.LINK Controller [104d:8039] (rev 02)
00:09.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-744B [DS-1S Audio Controller] [1073:0010] (rev 02)
00:0a.0 Communication controller [0780]: Rockwell International HCF 56k Data/Fax Modem [127a:2005] (rev 01)
00:0c.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
00:0c.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 11)
rj@rj-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30708 (30.7 KB)  TX bytes:30708 (30.7 KB)

pan0      Link encap:Ethernet  HWaddr 66:09:a9:95:4b:f6  
          inet6 addr: fe80::6409:a9ff:fe95:4bf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1308 (1.3 KB)

rj@rj-laptop:~$ 



------------------------------------------------------------

IF i did this right .. then you have the data.. i am not sure how to read this stuff.. so if i need to get that other modem drver thing.. let me know.. i was told if one does work and one doesnt that i should find out for sure before i try Badly to install both. 
So, i'll wait for you to comment. 

Oh.. and much thanks again. IF WE "YOU" can get this lappy working on DSL and Standard Dial out modem.. i'll be reall thrilled. this OLD lap has been sitting arround rotting for a long while.. as the Windows 2k system was starting to become unstable and i could reinstall it. having Ubuntu on here is like LIFE from the DEAD for this older machine. 
 
FWJ

---

### Post by forestwalkerjoe on 2009-01-29
i did the part 2 as you suggested to download the Modem Driver thing and try that as install too.. here is the out put on that. 

------------------------------------------------------------


rj@rj-laptop:~$ cd ~/Desktop
rj@rj-laptop:~/Desktop$ sudo sh cnxtinstall.run -- --tty
[sudo] password for rj: 
Verifying archive integrity... All good.
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.3

Please ensure that all modems are attached to the machine.
Press enter to continue.

Detecting devices in your system... please wait...
Done.

Supported Device Detected
=========================
Name: Communication controller: Rockwell International HCF 56k Data/Fax Modem
PCI ID: 127A:2005 104D:805A
Needed packages: hsfmodem or hcfpcimodem

System Information
==================
Distribution: Ubuntu 8.10
Kernel version: 2.6.27-7-generic
Kernel architecture: x86

Determining which package(s) to install or update, please wait...
Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:52:20--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:52:20--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)

Recommended Action
==================
The following packages should be installed: hsfmodem hcfpcimodem

Do you want to install these packages ([y]/n)? y


Conexant HSF softmodem driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:52:29--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)

Press enter to continue.


Conexant HCF PCI controllerless driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 17:52:34--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
rj@rj-laptop:~/Desktop$ 

I hope all the code here is actually doing what you wanted.. so we can create the right drivers for the modem and or PCMCIA card ehtrnet . thanks again.. in hopes we can solve all that. 

FWJ

---

### Post by pytheas22 on 2009-01-29
The modem-driver installation failed because it wants to download files, but it obviously can't because there's no Internet connection.  So let's try downloading the two files that it wants manually.  Hopefully the installer will be able to auto-detect them and move past the point where it can't find the files.

Download [this file]("http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2") and [this file]("http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2") and save them to your Ubuntu machine on the desktop.  Then try running cnxinstall.run again, as you did before, and please post all output.

As for the PCMCIA card, do you know the exact model of it?  What information is printed on the outside of it?

---

### Post by forestwalkerjoe on 2009-01-29
when i do the downloads of the TWO files you linked.. they both come down as archive.bz2. So, I'll try it.. but i am not sure how these will install. 
As to the Pc Ether card.. i had posted the exact type on the earlier notes.. but here is again. 
Sohoware ND5120 - E. Ethernet card. 
as to the above installs.. i am not very good at installs.. but I'll see what i can do. 
 
here is the output of that attempt. 
--------------------------------------------------------------------------------------

rj@rj-laptop:~$ cd ~/Desktop
rj@rj-laptop:~/Desktop$ sudo sh cnxtinstall.run -- --tty
[sudo] password for rj: 
sh: Can't open cnxtinstall.run
rj@rj-laptop:~/Desktop$ sudo sh cnxtinstall.run -- --tty
Verifying archive integrity... All good.
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.3

Please ensure that all modems are attached to the machine.
Press enter to continue.
 
Detecting devices in your system... please wait...
Done.

Supported Device Detected
=========================
Name: Communication controller: Rockwell International HCF 56k Data/Fax Modem
PCI ID: 127A:2005 104D:805A
Needed packages: hsfmodem or hcfpcimodem

System Information
==================
Distribution: Ubuntu 8.10
Kernel version: 2.6.27-7-generic
Kernel architecture: x86

Determining which package(s) to install or update, please wait...
Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 20:28:12--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 20:28:12--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)

Recommended Action
==================
The following packages should be installed: hsfmodem hcfpcimodem

Do you want to install these packages ([y]/n)? y


Conexant HSF softmodem driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 20:28:19--  [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-latest/archive.bz2)

Press enter to continue.


Conexant HCF PCI controllerless driver Installer version 1.0.3
Copyright (c) 2004-2008 Linuxant inc.

Downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)...   0%


Unexpected output from the 'wget' command :

---
--2009-01-29 20:28:25--  [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
Resolving [www.linuxant.com](www.linuxant.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.linuxant.com](www.linuxant.com)'
---

WARNING: Downloading the file failed. Skipping downloading [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-latest/archive.bz2)
rj@rj-laptop:~/Desktop$ 
rj@rj-laptop:~/Desktop$ sudo sh archive.bz2
archive.bz2: 1: archive.bz2: 1: SY&#65533;&#452;*: not found
archive.bz2: 6: Syntax error: "(" unexpected
rj@rj-laptop:~/Desktop$ BZh91AY: not found
sudo sh archive.bz2 -- --tty
archive.bz2: 1: BZh91AY: not found
archive.bz2: 1: SY&#65533;&#452;*: not found
archive.bz2: 6: Syntax error: "(" unexpected
rj@rj-laptop:~/Desktop$ 


--------------------------------
I ,either , cant figure out how to install the BZ file.. or it doesn't like it. 
FWJ

---

### Post by pytheas22 on 2009-01-29
I don't know how to make the modem installation work without an Internet connection.  Let's hold off on that for the time being and work on the PCMCIA ethernet device instead.

Please post the output of these commands:
```

lsmod | grep pcm
sudo modprobe pcnet_cs
dmesg | tail -50
```

---

### Post by forestwalkerjoe on 2009-01-30
ok after putting in the code you requested.. here is the output. 
I hope we can get things going. 



---------------------------

rj@rj-laptop:~$ lsmod | grep pcm
pata_pcmcia            18944  0 
pcmcia                 43052  2 pata_pcmcia,pcnet_cs
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_hda_intel,snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  3 snd_hda_intel,snd_ymfpci,snd_pcm
snd_timer              29960  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd                    63268  20 snd_hda_intel,snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            43412  5 pata_pcmcia,pcnet_cs,pcmcia,yenta_socket,rsrc_nonstatic
libata                177312  4 pata_pcmcia,ata_piix,pata_acpi,ata_generic
rj@rj-laptop:~$ sudo modprobe pcnet_cs
[sudo] password for rj: 
rj@rj-laptop:~$ dmesg | tail -50
[  158.809074] type=1503 audit(1233288853.664:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5419 profile="/usr/sbin/cupsd"
[  158.835809] type=1503 audit(1233288853.688:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5419/net/dev" pid=5419 profile="/usr/sbin/cupsd"
[  275.664177] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  275.841455] usb 1-1: configuration #1 chosen from 1 choice
[  276.278845] usbcore: registered new interface driver libusual
[  276.450763] Initializing USB Mass Storage driver...
[  276.465483] scsi2 : SCSI emulation for USB Mass Storage devices
[  276.477387] usbcore: registered new interface driver usb-storage
[  276.478149] USB Mass Storage support registered.
[  276.479027] usb-storage: device found at 2
[  276.479044] usb-storage: waiting for device to settle before scanning
[  281.477441] usb-storage: device scan complete
[  281.481391] scsi 2:0:0:0: Direct-Access     ST68022C F                3.01 PQ: 0 ANSI: 0
[  281.500509] sd 2:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  281.506307] sd 2:0:0:0: [sdb] Write Protect is off
[  281.506334] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  281.506344] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  281.513276] sd 2:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  281.523279] sd 2:0:0:0: [sdb] Write Protect is off
[  281.523304] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  281.523312] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  281.534649]  sdb: sdb1
[  282.250355] sd 2:0:0:0: [sdb] Attached SCSI disk
[  282.251488] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  535.352134] usb 1-1: USB disconnect, address 2
[  855.544176] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  855.720933] usb 1-1: configuration #1 chosen from 1 choice
[  855.730744] scsi3 : SCSI emulation for USB Mass Storage devices
[  855.738178] usb-storage: device found at 3
[  855.738206] usb-storage: waiting for device to settle before scanning
[  860.737547] usb-storage: device scan complete
[  860.741493] scsi 3:0:0:0: Direct-Access     ST68022C F                3.01 PQ: 0 ANSI: 0
[  860.764383] sd 3:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  860.770383] sd 3:0:0:0: [sdb] Write Protect is off
[  860.770407] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  860.770416] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  860.777377] sd 3:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  860.787468] sd 3:0:0:0: [sdb] Write Protect is off
[  860.787489] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  860.787498] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  860.796217]  sdb: sdb1
[  861.524461] sd 3:0:0:0: [sdb] Attached SCSI disk
[  861.525845] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1167.008117] usb 1-1: USB disconnect, address 3
[ 1167.015917] Buffer I/O error on device sdb1, logical block 1
[ 1167.015956] lost page write due to I/O error on sdb1
[ 1167.015989] Buffer I/O error on device sdb1, logical block 6882698
[ 1167.015997] lost page write due to I/O error on sdb1
[ 1167.016010] Buffer I/O error on device sdb1, logical block 7052072
[ 1167.016018] lost page write due to I/O error on sdb1
rj@rj-laptop:~$

---

### Post by pytheas22 on 2009-01-30
Your system doesn't seem to want to detect the presence of the PCMCIA card at all, and I'm not sure why.  Stupid question, but are you sure it's fully inserted?  Could you please unplug and replug it a few times, then post the output of:
```

dmesg | tail -75
```

Unfortunately I need to go to bed soon and may not be able to reply till tomorrow.

---

### Post by forestwalkerjoe on 2009-01-30
rj@rj-laptop:~$ dmesg | tail -75
[  281.513276] sd 2:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  281.523279] sd 2:0:0:0: [sdb] Write Protect is off
[  281.523304] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  281.523312] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  281.534649]  sdb: sdb1
[  282.250355] sd 2:0:0:0: [sdb] Attached SCSI disk
[  282.251488] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  535.352134] usb 1-1: USB disconnect, address 2
[  855.544176] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  855.720933] usb 1-1: configuration #1 chosen from 1 choice
[  855.730744] scsi3 : SCSI emulation for USB Mass Storage devices
[  855.738178] usb-storage: device found at 3
[  855.738206] usb-storage: waiting for device to settle before scanning
[  860.737547] usb-storage: device scan complete
[  860.741493] scsi 3:0:0:0: Direct-Access     ST68022C F                3.01 PQ: 0 ANSI: 0
[  860.764383] sd 3:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  860.770383] sd 3:0:0:0: [sdb] Write Protect is off
[  860.770407] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  860.770416] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  860.777377] sd 3:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[  860.787468] sd 3:0:0:0: [sdb] Write Protect is off
[  860.787489] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  860.787498] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  860.796217]  sdb: sdb1
[  861.524461] sd 3:0:0:0: [sdb] Attached SCSI disk
[  861.525845] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1167.008117] usb 1-1: USB disconnect, address 3
[ 1167.015917] Buffer I/O error on device sdb1, logical block 1
[ 1167.015956] lost page write due to I/O error on sdb1
[ 1167.015989] Buffer I/O error on device sdb1, logical block 6882698
[ 1167.015997] lost page write due to I/O error on sdb1
[ 1167.016010] Buffer I/O error on device sdb1, logical block 7052072
[ 1167.016018] lost page write due to I/O error on sdb1
[ 3101.464063] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 3101.668068] usb 1-1: configuration #1 chosen from 1 choice
[ 3101.700873] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3101.705321] usb-storage: device found at 4
[ 3101.705349] usb-storage: waiting for device to settle before scanning
[ 3106.705520] usb-storage: device scan complete
[ 3106.709437] scsi 4:0:0:0: Direct-Access     ST68022C F                3.01 PQ: 0 ANSI: 0
[ 3106.734379] sd 4:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[ 3106.740724] sd 4:0:0:0: [sdb] Write Protect is off
[ 3106.740749] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3106.740758] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3106.747315] sd 4:0:0:0: [sdb] 15625008 512-byte hardware sectors (8000 MB)
[ 3106.758040] sd 4:0:0:0: [sdb] Write Protect is off
[ 3106.758067] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3106.758075] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3106.767468]  sdb: sdb1
[ 3107.493570] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3107.494963] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3189.200132] usb 1-1: USB disconnect, address 4
[ 3189.209538] Buffer I/O error on device sdb1, logical block 1
[ 3189.209577] lost page write due to I/O error on sdb1
[ 3189.209607] Buffer I/O error on device sdb1, logical block 30476
[ 3189.209615] lost page write due to I/O error on sdb1
[ 3189.209628] Buffer I/O error on device sdb1, logical block 44118
[ 3189.209636] lost page write due to I/O error on sdb1
[ 3189.209650] Buffer I/O error on device sdb1, logical block 485450
[ 3189.209657] lost page write due to I/O error on sdb1
[ 3189.224208] Buffer I/O error on device sdb1, logical block 6882696
[ 3189.224221] lost page write due to I/O error on sdb1
[ 3189.224231] Buffer I/O error on device sdb1, logical block 6882697
[ 3189.224239] lost page write due to I/O error on sdb1
[ 4290.697365] pccard: card ejected from slot 0
[ 4317.172149] pccard: PCMCIA card inserted into slot 1
[ 4317.174689] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa00fffff
[ 4317.186740] pcmcia: registering new device pcmcia1.0
[ 4317.190125] firmware: requesting NE2K.cis
[ 4317.682770] firmware: requesting NE2K.cis
[ 4336.514385] pccard: card ejected from slot 1
[ 4339.008140] pccard: PCMCIA card inserted into slot 1
[ 4339.010725] pcmcia: registering new device pcmcia1.0
[ 4339.014205] firmware: requesting NE2K.cis
[ 4339.037903] firmware: requesting NE2K.cis
rj@rj-laptop:~$

---

### Post by forestwalkerjoe on 2009-01-30
> **pytheas22 said:**
> I don't know how to make the modem installation work without an Internet connection.  Let's hold off on that for the time being and work on the PCMCIA ethernet device instead.

Please post the output of these commands:
```

lsmod | grep pcm
sudo modprobe pcnet_cs
dmesg | tail -50
```
Maybe these files need to be extracted and then installed. I havnt the first clue on how some thing like this could be done.. or if there is some thing i need to Terminal "TELL" the computer to do with these.. but it seems to me that these are " zip " files.. so they need to be opened and told what to do. 
If that is the case.. maybe you have ideas on how "THAT" is done? 
FWJ

---

### Post by pytheas22 on 2009-01-30
We're closer; dmesg is now mentioning the existence of the PCMCIA card.  However, it can't initialize it because it's missing firmware.  To solve that problem, please download [this file]("http://burnthesorbonne.com/files/NE2K.cis"), then transfer it to the Ubuntu machine and save it on the desktop there.  Then run these commands:
```

cd ~/Desktop
sudo cp NE2K.cis /lib/firmware
```

Then reboot your computer.  When it's done booting and you log into the desktop, unplug and replug the PCMCIA card, then post the output of these commands:
```

dmesg | tail -75
lshw -C Network
ifconfig
```

> Maybe these files need to be extracted and then installed. I havnt the first clue on how some thing like this could be done.. or if there is some thing i need to Terminal "TELL" the computer to do with these.. but it seems to me that these are " zip " files.. so they need to be opened and told what to do.
If that is the case.. maybe you have ideas on how "THAT" is done? 

These aren't files; these are just diagnostic commands.  For now, let's just see what happens with the firmware file, and take it from there.

---

### Post by forestwalkerjoe on 2009-01-30
ok.. success. 
kinda. 
i put that NIC cid on the desk top and ran the code. Immediately i noticed that the connection icon was working. the system was ready for an update. 
So i let it do a full update.. and over an hour later it finished. 
Trouble goes like this: 
it required a restart for things to take effect. 
Allowing the restart gives me a kernal panic at the start up after chosing which operating system. 
ACPI: DMI BIOS  year==0 assuming ACPI-Capabl machine
ACPI: Aborted because junk in gzipped archive. 
kernel panic - not syncing : VFS: unable to mount root fs on unknown-block (0,0)
Then it freezes.. cant get in. 
So.. thank you for the first solve.. i am confused as to what has just happened. 
I'll check with you tomorrow if you are able to help out. 
I would also like to know.. that the NIK that you had me put on the desk top to run that code.. should i put that in the trash now? or do i need to move that to some folder? 
I know i can not even get into the system now.. but i figured i'd ask for the time when we do get in. 

humm.. i just noticed some thing.. on the GRUB thing.. we used to have 3 types of start up choices and then one windows choice. now we have extra's that are seemingly the same.. but not. i chose a different one down the line and IT is allowing me in. can we edit that GRUB file.. so that the bad ones are not listed in the start up in grub? i assume it was a conflict of old kernel verse new or some thing like that. 
I now see desk top. 

thanks for the help .. once again. REALY. 


FWJ

---

### Post by forestwalkerjoe on 2009-01-30
humm.. i hate to be such a bother.. but i have also noticed that there is a nice LAG when using the browser or anything net related. the Video's i tested on youtube are behind the sounds.. the video is jocking and slow. 
sounds are slightly delayed or they are behind the video. 
Flash is giving me a hard time as well.. any pages that work with java or flash seem to take GODS own time to load. i had not noticed any Slowing or lagging before i was  connected to the net. 
is this a video card issue or a configuration issue? every thing running so slow doesnt help my case.. when i am trying to show HOW UBUNTU IS THE BOMB. 
i am sure this is some sort of small thing.. like a better set of drivers.. or some setting i am unaware of, being changed to allow the system to work in a better way. 
and before long i would like again to try the modem install for the dial out.. if i use this at a house that is not connected to the DSL or can not connect to me.. i can always connect with dial out.. arrg.. "IF" i can get the hard ware to see that and have the right drivers. 
thanks again. 
FWJ

---

### Post by pytheas22 on 2009-01-30
> humm.. i just noticed some thing.. on the GRUB thing.. we used to have 3 types of start up choices and then one windows choice. now we have extra's that are seemingly the same.. but not. i chose a different one down the line and IT is allowing me in. can we edit that GRUB file.. so that the bad ones are not listed in the start up in grub? i assume it was a conflict of old kernel verse new or some thing like that.
I now see desk top. 

Yes, to edit grub, open a terminal and type:
```

sudo gedit /boot/grub/menu.lst
```

Towards the bottom of the file you'll see several sections that look like this:
```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		83db7aca-d0db-4077-af6b-12f007d63db4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=83db7aca-d0db-4077-af6b-12f007d63db4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

Each of these corresponds to a different line in the boot menu.  To get rid of one, either delete it or put a # symbol in front of each of its lines to comment it out (commenting it out is preferable in case you need it back later).  Then save the file.

As for slow pages: flash embedded in web pages consumes a lot of bandwidth and memory, so it's going to be laggy on an older machine.  Unfortunately there's no good way to improve this.  You can try [installing the free flash players]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Free%20Software%20alternatives%20to%20Adobe%27s%20Flash%20Player") instead of Adobe's closed-source plugin, but I doubt they'll give much better performance.

If you want to make the modem work, run cnxinstall.run as you did yesterday.  It should work this time if you're already connected to the Internet via DSL, because it will be able to download the files it needs.

Also, keep in mind, in case you're not aware, that the modem is going to give you a very, very slow connection by modern standards--playing Youtube videos, for example, is pretty much out of the question on a dial-up connection.  Moreover, you can't just plug the modem into any house with a phone line and have it work.  The house would need to have service via a dial-up ISP, and not that many still have that.  Maybe you understand all this already, but I just want to make sure so that you don't have unrealistic hopes for what the modem can do.

Anyway, I'm glad the DSL finally works; I was worried last night that it might never come up.

---

### Post by donaldt on 2009-01-30
Your suggestion about the alternate install worked.  I now have Ubuntu up and running (more or less) on my external hard drive.  I changed the boot order to begin with the external hard disk, etc. and it boots up fine.  If I want my original Vista Sony portable, I just unplug the external USB hard drive and it works fine.  I am most grateful for your help!

I have the normal Ubuntu screen and many programs up and running, but the screen displays black space when selected in many windows.  I believe I need to follow your suggestions about entering files, but don't have a command line.

Also, I know what a URL is, but how do I start a new thread and what do you suggest we title the little devil...?

donaldt

---

### Post by pytheas22 on 2009-01-30
donaldt: to start a new thread, go to the '[General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")' section of the forums and click the 'New Thread' button.

To give me a better idea of your problems at this point, it would be helpful if you posted a screenshot of your whole desktop, with some examples of the 'black space', in your new thread.  You can take a screenshot by going to Applications>Accessories>Take Screenshot, and you can attach it to a forum post by following [these instructions]("http://ubuntuforums.org/showthread.php?p=4527031#post4527031").

Don't modify any files at this point because I'm no longer sure that the instructions I gave you a few days are going to help anymore, now that I have a better understanding of your issue.

---

### Post by forestwalkerjoe on 2009-01-30
ok.. another success. 
i WAS able to effect the grub edit. but it took a little bit.. as i was putting the pound on the wrong place. after 3 or 4 tries.. i was able to edit the parts i wanted out. 
 
Second part.. semi successful. 
I did the sudo code thing as before and it downloaded the tree and dependencies etc.. it gave me choices.. and I took the recommended ones. 
BUT.. i have now.. not the first clue on how to set up the dial out. i have hunted and hunted for where that would be.. as in System preferences network config and system admin network tools.. but it doesnt have a clear place for Dial out. is this one of those.. I have to MOUNT it and then using the mounted icon.. tell it what to do?
so.. this is where i am not sure if the thing worked or not.. i have no way to TEST it out. i get what you mean on slow.. it says. 14.4 unless i want to buy the faster driver. it will only be to connect for ubuntu Forum update etc. i will not be using the dial out for any thing else. also.. dial out is a small part of my own package.. i never use it.. but i can chose numbers from more than one dial out area code and it will work. but thanks for the heads up.. in my checking i did run into that only 14.4 thing. sucks.. and i remember when i had a 14.4 only dial out connection. as to the flash.. i am tempted to do the FREE FLASH player.. but i am  concerned i will mess with the wrong thing.. if i chose it in ADD REMOVE.. i am assuming that is where i would get that.. will it uninstall the older Adobe version and install the open sourced one.. on auto? or will i need code to tell it to uninstall Adobe and then code to install a Free player? 

OK then.. with all the little things.. big to me.. thank you for the help.. really. 
I would like to move to stage two. 

part of the reason i started my install on this lap.. is if i could get the support.. i could test what i want to do on the HOST Family's computer.. here first. then i would have some idea on how to do it for them. 

so.. i had been told that there is a way.. on a duel booted system.. to some how.. graft or integrate the SHELL of windows.. into the Ubuntu system. So that.. most if not all windows styled EXE files or disks will run inside Ubuntu. I could care less for myself.. but.. the family i have been helping out.. is worried that some of there software will not work. and they do have kids that are obsessed with some windows type games.
is this where i have to do a VM install of windows Inside ubuntu? or did the comment above about SHELL make sense? 
once i can find what works to accomplish the deed.. i will proceed first with installing or changes INSIDE my own lap top. IF i am not willing to risk it myself.. then i can not expect Them to RISK it either. 

once i am sure which choice or what choices i have.. and is best.. i will set it up here.. then take it to them. all their stuff is now backed up on my 200 gig exterior drive. " its only about 22 gig of stuff. i am sure that most of the music will corrupt because of if the windows DMR stuff. i warned them early.. but the rest will be fine. 

Hope this is not too much to think on. 

FWJ

---

### Post by pytheas22 on 2009-01-31
> BUT.. i have now.. not the first clue on how to set up the dial out. i have hunted and hunted for where that would be.. as in System preferences network config and system admin network tools.. but it doesnt have a clear place for Dial out. is this one of those.. I have to MOUNT it and then using the mounted icon.. tell it what to do?

Having never configured a dial-up connection in Linux personally, I'm not positive what to do here, but I think you want to install gnome-ppp by typing:
```

sudo apt-get install gnome-ppp
```

Then launch it from the Applications>Internet menu.  You will need to enter a username, password and phone number to dial, and it should connect you (if it doesn't work on the first try, click the 'Setup' button and try playing around with different settings first).  If you don't know the username, password or phone number, contact your ISP.

Unfortunately I don't know of a way to get past the 14.4kb/s limitation on the modem driver.

> 
so.. i had been told that there is a way.. on a duel booted system.. to some how.. graft or integrate the SHELL of windows.. into the Ubuntu system. So that.. most if not all windows styled EXE files or disks will run inside Ubuntu. I could care less for myself.. but.. the family i have been helping out.. is worried that some of there software will not work. and they do have kids that are obsessed with some windows type games.

You're thinking of 'wine', which allows you to run some Windows software on Linux.  You can install wine via Add/Remove programs or by typing:
```

sudo apt-get install wine
```

Then simply right-click on your .exe files and select 'Open with Wine Windows Program Loader' to run them as you would in Windows.  But remember that not all Windows software works through wine, and you might experience erratic behavior.

A virtual machine (VM) is another option for running Windows software on Ubuntu, but it probably won't work well if your computer is old, as virtual machines require a lot of memory.  I would stick to wine on your laptop.
> 
i am tempted to do the FREE FLASH player.. but i am concerned i will mess with the wrong thing.. if i chose it in ADD REMOVE.. i am assuming that is where i would get that.. will it uninstall the older Adobe version and install the open sourced one.. on auto? or will i need code to tell it to uninstall Adobe and then code to install a Free player?

If you want to install the free flash player ('gnash'), you will first need to remove the package 'flashplugin-nonfree' (Adobe's proprietary player), then install 'mozilla-plugin-gnash'.  You can do all this through Add/Remove programs.  You will need to restart Firefox for any changes to take effect.

As for the screensaver problems that you mention in your private message: your video card may not support 3D acceleration at all, which might be the problem.  To find out, please post the output of these commands:

```
cat /etc/X11/xorg.conf
glxinfo
lspci -nn
```

---

### Post by forestwalkerjoe on 2009-01-31
just so you remember.. before the connected to the net update.. the features i was talking about were working.. then after.. they were not. 
i am fairly sure i must have allowed some thing to download that shouldn't have and its conflicting. it's probably some thing like a xorg verse GL or some thing like that.. but here is the output.. this might tell you what is up in my system. 

rj@rj-laptop:~$ cat /etc/X11/xorg.conf
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
rj@rj-laptop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
rj@rj-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 FireWire (IEEE 1394) [0c00]: Sony Corporation CXD3222 i.LINK Controller [104d:8039] (rev 02)
00:09.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-744B [DS-1S Audio Controller] [1073:0010] (rev 02)
00:0a.0 Communication controller [0780]: Rockwell International HCF 56k Data/Fax Modem [127a:2005] (rev 01)
00:0c.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
00:0c.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c478 [1180:0478] (rev 80)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 11)
rj@rj-laptop:~$


i  also recall in my look around that it thinks it has an ATI video thing set up.. and i don't think i have ATI. maybe that is it?
if i hit applications accessories.. it has a ATI Catalyst control center there that i don't think was there before.

Going onto the flash player issue. I did as you suggested.. and uninstalled macromedia adobe flash.. and then installed Gnash.. it was terrible.. the screen just flickered and the buttons danced. So i went back to ADD REMOVE and it would not let me remove it from ADD remove. it said use synaptic package remover. it took some time to get it to even see it.. but i was finaly able to remove it. i also tried the other type of flash player.. SFS some such. not much better.. so i removed it and replaced the flash player from NON FREE. it's working with a bit of a lag.. and this on a high end DSL connection. i am sure there is some setting in here that would cashe it better or some thing. IF i go full screen it JOCKS and freezes.. even when the audio continues.. in small frame.. its better but still not quite in synch with the lips of the speaker. 
for now.. this is not my largest concern. 
the video issue.. i am sure is not just NO Hardware.. i am convinced this is a conflict i some how caused.

regarding my request for a page to learn Terminal code commands in Ubuntu.. i did find on my news page some linux dedicated News and such.. one had a full download of a Free Ereader book called Ubuntu Pocket Guide.. version1-1 in PDF. i have not read it all of course but after browsing it.. it seems to be some of what i want.  here is that link you might like that for giving to others who are learning:
[http://linuxhelp.blogspot.com/2009/01/free-ubuntu-pocket-guide-and-reference.html](http://linuxhelp.blogspot.com/2009/01/free-ubuntu-pocket-guide-and-reference.html)
and here is part of the page that set me on the seamless use of windows apps in ubuntu. Its going to have to be a duel boot and i dont think my lap or their pc will support VM for an install of windows inside ubuntu.. like you said. page link:
[http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/](http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/)
I dont want to over work you.. i hope these two links helps YOU with your work for us in here. Thanks again.
FWJ
FWJ

---

### Post by stunnedandconfused on 2009-01-31
> **pytheas22 said:**
> 
Also, some things I've read suggest that this card would work out-of-the-box with Fedora 10, so if you have time and feel like burning another live CD, you may want to give that a try.  The card should also be supported when Ubuntu 9.04 is released in April, but until then it's probably not going to be fun to use under Ubuntu.

pytheas, I realised that I had an old Acer Aspire 1300 that still worked, dragged itout and hey presto, UBUNTU is all up and running fine. I ma learning every minute of the day re linux and I am really enjoying getting to know it.
I look forward to April and hopefull having it n my bigger, newer, shiny desktop Thank again.

---

### Post by donaldt on 2009-01-31
I agree.  I downloaded 245 files that updated automatically and would be reluctant to now make the changes you suggested.  I'll open another thread (using your instructions, thank you!) and try to get you a screen shot.  I have internet, cable and phone installers coming today, but will try later.

The screen going black occurs when I click on a portion of a window and it turns dead black.  If I move up and down on a slider bar it will then (sometimes) slide the black like a window shade.  Most annoying!  ...especially since I was trying to download Firebird and get my e-mail up and running.  I've been using Firefox and Thunderbird for over a year on my windows machine.

Next step, using Open Office 3.0 and see if I can get my power point, word and other files to work on the Ubuntu hard drive.  I really like the clean, uncluttered Ubuntu GUI.  No extraneous and annoying programs trying to sell themselves to you.  Thanks again for your help.

djt

---

### Post by pytheas22 on 2009-01-31
**forestwalkerjoe**: it doesn't look like your card is currently supporting 3D acceleration at all, according to the output of 'glxinfo'.  An update could have broken it, or there may be some other problem.  If you install Planet Penguin Racer by typing:
```

sudo apt-get install planetpenguin-racer
```

then launch it from the Applications>Games Menu, can you run it?

According to this [bug report]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617") which is possibly related to your issue, you might solve the problem by doing this:

1. back up your xorg.conf by typing:
```

cp /etc/X11/xorg.conf ~/Desktop/xorg.conf-backup
```

2. open up xorg.conf for editing by typing:

```
sudo gedit /etc/X11/xorg.conf
```

#. erase everything in the file, and paste these lines in its place:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
Option "BusType" "PCI"
Option "DmaMode" "None"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Then save the file, log out of the desktop and log back in.  This might help, but I'm not sure.
[B]
stunnedandconfused[/B]: I'm glad you got Ubuntu running, albeit on an older computer.
[B]
donaldt[/B]: that does sound like an annoying problem, and I look forward to seeing your screenshots in your thread to get an exact picture of what's going on.  It would also be good if you posted the output of:
```

lspci -nn
```

---

### Post by forestwalkerjoe on 2009-01-31
i have done as you suggested and downloaded the game.. it does not open. 
i have backed up the config file which is on my desk top.. 
i edited the file to delete all and copy pasted the file you suggested.. logged out and back in.. and checked the plazma screen saver and others that were working before the update.. NO dice. 
I am still wondering about that ATI thing that shouldn't or should it be there? if that is trying to override other settings .. it could be it or part of it. 
ATI CATALYST CONTROL CENTER , I don't believe that was there before updating. 
if i could figure out how to do screen shots on this.. which i may have a clue now.. there is a camera icon on the tool bar above now.. i might be able to show you things that might help us/me. or you.. i am sure have code that can ask questions to the system and help find it that way. i leave for work in 2 hours.. in hopes you are able or willing.. to help further.. i know you are always helping helping helping.. I personally Do really feel grateful for that.. thanks
FWJ

---

### Post by pytheas22 on 2009-01-31
The ATI control center item is probably just a utility for configuring your video settings if you have an ATI graphics card.  I'm not sure how it would have gotten there--it's not installed with Ubuntu by default--but it's possible that you inadvertently installed it yourself before.  If you want to see which packages you installed recently, type:

```
sudo cat /var/log/apt/term.log
```

and it will display the log from your package manager.  You can also find similar information by opening Synaptic and going to File>History.

The fact that the ATI control center is installed, however, doesn't necessarily mean that the ATI driver is actually controlling your card (which would probably be impossible because it wouldn't work at all if it tried).  If you want to know for sure, though, type:
```

lsmod | grep -i -e ati -e fglrx -e radeon
```

If that command returns nothing, then no ATI driver is active.

I'm not actually sure which driver would be used for your video card, the Savage/IX-MV, but I think it's just called 'savage'.  What is the output of:
```

lsmod | grep savage
```

---

### Post by forestwalkerjoe on 2009-02-01
well here is the Out on the terminal commands you gave me. 
At first i thought i had got it wrong.. but apparently.. the lsmod savage
does nothing. 
as to the sudo cat log thing.. it was long.. and i did try and check it but i dont see anything related to ATI catalyst. It is still true that these were working.. and now they are not. 


rj@rj-laptop:~$ lsmod | grep savage
rj@rj-laptop:~$ lsmod | grep savage
rj@rj-laptop:~$ lsmod | grep -i -e ati -e fglrx -e radeon
cpufreq_conservative    14600  0 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  5 pcnet_cs,pata_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic
rj@rj-laptop:~$ lsmod | grep savage
rj@rj-laptop:~$ lsmod | greo savage
bash: greo: command not found
rj@rj-laptop:~$ lsmod | grep savage
rj@rj-laptop:~$ 

I have been reading that Book I sent you a link to. Its really quite good. I suppose i will learn a lot about how UBUNTU works in the next few days. 
conflicting drivers or software packages aside.. the system seems to be running faster than it was at the beginning.
a few of the games are no longer working.. and i have tried the screen savers again.. with no luck. 
I am very thankful you are helping me. 
I cant make anything out of the above Out Put.. but i am interested in what you can get out of that. 
OH! i tested the dialout pppoe modem thing tonight.. and it says.. " NO modem installed" 
so.. we have the software to do the deed.. but not the right driver i am assuming. 
Funny.. that book POCKET GUIDE TO UBUNTU.. says.. installing Ubuntu for the first time is best on older systems.. this lap top qualifies.. yet.. there is still trouble with hardware functions. 
I am sure with help like yours.. this thing will be working sweet.. soon. 
hey.. i was told there was a download / code that will release the DVD player to play movies. I have not used this lap in so long that i think its only a DVD player/CD rom.. not a burner.. but i cant tell. My last 3 were both. 
Have that release code? I hope so.. it would be nice to have it all working.. i bet it will even work better than it did when i got it. 

FWJ

---

### Post by pytheas22 on 2009-02-01
It's strange that you're not using the savage video driver.  I'm not sure which other one your system could use.  You can try to force it to use savage by opening up your xorg.conf file by typing:
```

sudo gedit /etc/X11/xorg.conf
```

Then paste in these lines:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
driver "savage"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Then reboot.  Does that fix anything?

To play DVDs on Ubuntu, you need to install the appropriate codecs.  You can get them (and a lot of other useful software that Ubuntu doesn't include by default) by typing:
```

sudo apt-get install ubuntu-restricted-extras
```

Once those are installed, you should be able to play almost any DVD.  By default, Linux will ignore region settings on your DVD player.

---

### Post by forestwalkerjoe on 2009-02-01
well, here is the news. 
the config edit you had me do.. unless i did that wrong.. " errase the old.. replace with the one you just gave me".. did nothing. 
I did notice in the ADD REMOVE there is that Catalyst and there is a ATI driver that seems to be installed. 
when i click on the ATI CATALYST it says there isnt an ATI or Driver is not installed. REMOVE this then try again.. type thing. 
SO i have to assume its conflicted.. and needs to be removed before other default drivers can be restored. 

As to the special update you had me do.. i am not sure what all those were but the first disk i put in was a black and white DVD of Abbot and Costello.. it played fine. 
I also have a language course on DVD that plays with an interactive screen.. program is called LINGO.. it froze and then the system would not let me eject it or unmount. IT SAYS CAN NOT MOUNT etc.. 
so it must be one of those.. Oddly only Microsoft DVD formats. 

I did check that screen saver again.. nothing. 

if there is another check up on system, type, Terminal command you wish me to try.. let me know. 
and as said.. the Dial out requires some sort of driver and the one it has.. if it has one is not working. 
outherwise.. the system is moving rather smoothly. They keyboard is a bit over touchy.. and will bounce to another line or add letters i am typing in the wrong place.. but i think that is sensitivity to the board. 
i am sure there is a setting in here to help me with that. 

FWJ

---

### Post by pytheas22 on 2009-02-02
Do your graphics work better if you boot into an older kernel?  You can do this by selecting one of the kernels at the bottom of the list in the grub boot menu (you may need to press 'escape' to load the grub menu after turning on your computer; if so, you'll see a message on your screen telling you that).  At this point, that's the only suggestion I can think of for solving the video issues.
> 
I also have a language course on DVD that plays with an interactive screen.. program is called LINGO.. it froze and then the system would not let me eject it or unmount. IT SAYS CAN NOT MOUNT etc..
so it must be one of those.. Oddly only Microsoft DVD formats. 

Certain DVDs may not play due to encryption that Linux can't decode (mostly for legal reasons).  But I'm also wondering if your 'Lingo' DVD is really just a normal DVD, or if it's something else--the fact that it's 'interactive' makes it sound like it may be running some kind of Windows executables in addition to playing videos.  Does it work if you put it into a normal DVD player attached to a TV, with no computer in the picture?
> 
They keyboard is a bit over touchy.. and will bounce to another line or add letters i am typing in the wrong place.. but i think that is sensitivity to the board.

Probably you want to disable the tap-to-click functionality of your touchpad mouse, or decrease its sensitivity.  In most cases you should be able to do that by going to System>Prefernces>Mouse.

---

### Post by TaskmasterC on 2009-02-02
If it is very new, you may have to check for proprietary drivers, or maybe search for restricted ones. Have you been able to run any updates at all? Sometimes they will help. Also, you can check your screen res. It may be out of sync with your monitor, and your refresh rate may be off. Just a thought. I had issues when I put in a new ATI card, and it took some time to get it working properly. But after several changes, all is well.

---

### Post by forestwalkerjoe on 2009-02-02
well, i have good news. 
Because we were having issues with figuring out What was wrong.. i chose to take a leap of faith. 
I had tried to ADD REMOVE the ATI CATALYST.. but it wouldn't allow it.. unless i uninstalled the ATI DRIVER.. too. 
I guessed that if i did do the uninstall of the two of them.. that the choice to use Savage might work or that the system my revert to what ever working driver was there before the Update. 
took some doing.. and when i had rebooted, it was to a BLACK SCREEN. 
So i rebooted to the recovery in Grub.. then chose it to look at the X server. i was guessing it would check the whole system.. or maybe it would be like windows and find the best last working config. 
after the check up.. booting into the Desktop.. i got  normal screen and after checking.. i had more than i had before. 3d is now working. ALL OF IT except one screen  saver Voronoi.. not sure what it needs but IT freezes the whole system if i even select it. Seemingly every thing else is working. NOT sure if that one screen saver is indicative of some lack in my system... not enough ram or what.. or if there is some other Graphic Card related issue that i might not see till later. SO far... i have not found any other type of malfunction.   i even tried the game you told me about. Planet Penguin.. it was black for a minute.. but found itself and then ON came the game. 
Some of the special features are now working too. NOT the cool ones. 
When i use the desktop background  clicking on the desktop 
and then choose to Enable effects it says.. "Looking for a driver" then fails.OF course i "am" at work.. and therefore not connected to the net when it's searching. Not sure if that is going to matter or not. 
ConpizConfig Settings Manager thing has some settings ON.. and i see one or two here and again. 
NOT sure what drivers this is looking for.. but at least the 3d is ON.
 
So.. i now have DVD.. MP3, 3d with Savage but missing SOME sort of Drivers.. at least now i know it's Savage.. and system is moving faster.
oh here is the OutPut :
rj@rj-laptop:~$ lsmod | grep savage
savage                 39424  2 
drm                    86056  3 savage
rj@rj-laptop:~$ 

ALL is well in Puter land for now..  
with the exception of the Dial out modem.. which would be nice for a few reasons. ALL seems to be working.
 
Still cant figure out how WINE works.. or what it would work with.. every disk i put in.. seems to just fail. 
BUT all else is working sweet. Was hoping that the interactive DVD language program i have would work if i tried to start it in this wine thing. I have NOT the first clue how to Config the WINE or even if i am reaching for the wrong thing. 
OPPS: PS. i have now arrived at home.. i HAVE found a troubling problem. 
I had to reboot 3 or 4 times to get into the Desktop. 
It gets to Grub.. i make my  choice.. then it Turns Black and then kinda seems to freeze. I tried the Recovery console thing.. chose the Fix X thing.. and this time it didnt work. I tried more than once.. Freezes with a black screen.. NO sounds.. nothing. after my 4th try.. i then chose to do a boot normal setting.. This time it DID let me in with sounds and visual desktop. i had moved many of my Desktop backgrounds from the HDA1 windows, into the photos for desktop area of Ubuntu.. but it took a very long time for them to show.. and desk top was just a colored background. 
IS there a way for there to be support of the Savage Graphics card or some thing.. so that in start up we dont get a black screen? or what do YOU think would cuase this? 
as to the kernel issue. when i did the UPDATE. it seemed to bring me to Kernel version some thing such point 11. that gave me a kernel Panic.. so i didnt use it.. i started using the earlier one.. some such point 7. that works. So after i figured that out.. i asked you to help me Edit the Grub menu.. so i didn't have to change the line up.. i could just let the default be the highest kernal on the list. That now being.. some such point 7.I have been messing with the sensitivity of the keyboard.. mouse and touch pad. Its a slight bit better.. but if i type too fast or hit too hard the cursor jumps to some place else and i am typing in the wrong place.. still. but i think i can get used to that.. I'll keep playing with it. DVD issue.. the LINGO DVD is one i can put into a standard TV.. it will then use the Next button or back button for QUE's to move onto the next level. not sure why this one wont work on Linux. Of course.. that maybe why.. it is asking windows to react a certain way.. and this is Just NOT windows. 
Someone said some thing about refresh rate.. i am wondering if that is part of it.. but i think maybe NOT. if the refresh rate were the trouble.. i would still Hear the sounds Ubuntu makes on start up.. but it just freezes. i would really like to see your OPINS on the black screen issue. i dont want to fight with the system to get it to boot each time. 
I will play  with the refresh rate and see if that solves anything. 



FWJ

---

### Post by forestwalkerjoe on 2009-02-02
OOOCH.. even bigger problem. 
i copied my message to you ON the laptop.. then suddenly realized the system wasnt working right.. it said.. Read only status.. and i noticed that the one hard drive was not mounted. there are normally two listed on the desktop. 
i wondered why this was happening.. and chose to log out.. log in. 
WHICH failed. i get this type of comment. 

: 
chcking drive / dev/sda5 
?dev/sda5: Inodes that were part of a corrupted orphan linked list found. 
/Dev/sda5: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY
(ie, without -a or -p options)
fsck died with exit status 4                        FAIL
* An automatic file system chek ( fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. 
FHe fsck should be proformed in maintenance mode with the root filesystem mounted in read-only mode.
* the root file system is currently mounted in read-only mode.
A maintenance shell will now be started. 
After performing system maintenance, press CONTROL -D 
to terminate the maintenance shell and restart the system. 
Bash: no job control in this shell
root@rj-laptop:~#

if i start again in grub and chose recovery mode.. it gives me this same comment.. no way to get into the recovery console. 
i have no clue what code needs to be run here.. to get it out of this strange loop. WHAT JUST HAPPENED HERE? i am guessing MANUAL means type fsck.. so i have now done that..and its asking to FIX the orphaned linked list.. i am going to say yes.. and let it fix what ever this is. I am assuming the hard drive is having some sort of FIT. 
please write back and let me know that my laptop just didnt give up the ghost. 


PPS: Ok.. i had to mess with it a lot.. i had to log back into windows 2k.. and i did a check on the system in that.. and then.. i tried again and again to reboot into LINUX. 
it consistently failed. i guess it was a dirty shut down or what ever it called it. 
and so it kept CHECKING itself.. and failing at about 93. some thing percent. 
i did get back into the console and i tried to get it to start X.. which also failed. FIX X was not much help. it showed me all these areas.. numbers.. that didnt match to the numbers it was giving. it see's that it thinks its 4 and should be 3.. what ever that means.. so it asks to FIX? Y or N. I finaly let it "FIX" things.. then console came back and asked if i wanted to boot normal. i chose it and i am back in.. the mounted drives are back up.. and apparently i am no longer in READ ONLY mode. 
i am typing ON the laptop now.. but i am worried if i try and reboot again.. that i will loose access to the Desktop again. so its a gonna stay here.. untill i get your code to run and tell it to fix the issues. I can reach terminal here as well.. so if you need me to ask it what is wrong with it.. i can do that from here. 
thanks. 

FWJ

---

### Post by pytheas22 on 2009-02-02
I'm glad the video issues are sorted out.  I guess it was the ATI stuff after all.  I have no idea how that could have happened, but presumably if you avoid installing the ATI Catalyst Center in the future, things should continue to work.

As for the modem not working: what happens when you try to connect?  Could you start gnome-ppp in a terminal by typing 'sudo gnome-ppp', try to connect and see if there's any output dumped to the terminal regarding what went wrong?

I suspect that all of your weird black screen issues were related to the hard-disk corruption (which is why you got the warnings about fsck and so on).  It sounds like you successfully fixed that on your own, and hopefully it will stay that way.  Usually hard-disk corruption occurs when you don't shut the system down cleanly, so always be sure to shut down by going to System>Shut Down...  If your system freezes for some reason, you should try to reboot using the [REISUB method]("http://www.definition-of.com/REISUB") rather than just cutting off the power, if possible (in extreme cases, REISUB might not work).

But the file-system corruption could also just have happened as a result of your hard disks being old or some other fluke.  It's happened to me before with no good reason other than that my computer was old.  But it only happened once, two years ago, and has been fine since then (I still use that same six-year-old computer every day, and haven't replaced any of the hardware since I bought it), so hopefully the problems with your system were just a one-time fluke that will not pop up again.

I'm not sure why your DVD won't work, but you might have better luck if you played it in mplayer rather than Totem (aka 'Movie Player').  You can install mplayer through Synaptic (or by typing 'sudo apt-get install mplayer'), and then find it in the Applications>Sound and Video menu.  mplayer is another video player that sometimes work better.  There are other alternatives as well, like [VLC]("http://www.videolan.org/vlc/download-ubuntu.html").

---

### Post by forestwalkerjoe on 2009-02-02
ok.. i did the sudo gnome thing.. and it gives me a popped up dial out thing. i put in my name password and i have a local phone number to call out on. 
when i hit connect i get this in a lOG: 
-> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

the Terminal reads out like this :
rj@rj-laptop:~$ sudo gnome-ppp

(gnome-ppp:7276): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnome-ppp:7276): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
WVCONF: /root/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory


I also did do the aptget of the mplayer. i have not had a chance to check it out. 
I am really concerned that my hard drive my have areas that are failed.. and that this might corrupt to the point that the lappy will be either needing to be whipped clean and start over.. or it could fail so bad that its a hung a junk. there is no way to check with in a Ubuntu system and fix any further errors to the hard drive?
kinda like a DISK CHECK in windows looks for cluster errors?
i am sure this is not a Defrag issue.. i was told LINUX's dont Need to be defraged.. ( another of those cool things i like about LINUX anything.. NO virus, rare to hack.. no defragging.. largely seems to be stable no matter what you do to it.. unless you break your install) cant beat it. 
its 9:45 am Pac time.. i'll be here most of the morning and on to 1pm.

PS: ok.. that was an afterthought.. i put in the LINGO disk.. i even preopened the Mplayer.. and it still does this thing where it clicks and doesnt read the disk. It cant mount it. this freezes the system.. cant eject because its not mounted.. eject button on ROM player will not respond.. so it forced a restart. i was nervous on the restart.. but even though when it starts up there is comments about some  areas.. as if the clusters are going bad.. it still got into the Desktop. i have now noticed that it doesnt auto mount the swap drive and so on. i went into Places and clicked on each and then the mounted. Why is that going on now? 
all the photos i had "MOVED" i found i had not moved i had just pointed Ubuntu to where they were.. so the large amount of photos for backgrounds that were in the desktop background field were gone. I just did a COPY and paste of them into Ubuntus photo folder. now i can see them again. but it seems odd.


PPS: the power just went out on the whole block for one hour. When the power came back on.. the laptop had been suddenly shut down.. the battery has been shot on this for a long time. it gave me trouble with black screens freezing again. i had to mess with it further.. recovery , fix X server thing.. and it finally DID let me back in. Your comment that it maybe fixed now.. seems true. BUT.. i am thinking maybe the hard drive is going sour. Is there a way in UBUNTU to check the hard drive for those kind of errors and fix them? in such a way that i wont run into the issue .. the same way as before?

---

### Post by pytheas22 on 2009-02-02
fsck should already have fixed any inconsistencies on your hard drive.  Of course, there's the possibility that more inconsistencies will arise if the disk is starting to fail.

There are plenty of ways to check hard-disk health in Ubuntu.  One tool with a nice graphical frontend is called gsmartcontrol.  You can install it by downloading [this package]("http://download.opensuse.org/repositories/home:/alex_sh/xUbuntu_8.04/i386/gsmartcontrol_0.8.3+nmu1_i386.deb") and double-clicking on it.  Then launch the program from the Applications>System Tools menu.

Your BIOS may also be able to monitor disk health.  Make sure that SMART is enabled on it.

gnome-ppp appears not to be working because it can't detect your modem.  Open gnome-ppp again, press the 'Setup' button, then click the 'Detect' button to have it auto-detect your modem settings.  If that doesn't work, please post the output of:
```

ls /dev
```

---

### Post by forestwalkerjoe on 2009-02-03
The screen issue has been getting worse. 
I dont think its related to the hard drive.. i think there is some comment on the Start up or Grub or some such that is not telling it to load the right stuff. i got home again.. late.. and then.. turned all on.. and found the black screen issue over and over.. i tried to get into the recovery mode.. i tried FIX x server.. i finaly tried the drop to promt and typed StartX. this did an odd thing.. it started up.. with a grey screen not the normal screen color or type.. and when Desktop loaded there was no support at all.. no mouse.. and an error that switcher had failed. I tried logging into windows 2k.. and it doesnt give me the option to try F2 to look over the bios or settings. F8 gives you a Safe mode option.. and such but the set up is seemingly not there. nothing responds after grub is up.. or before. 
every thing else is fine. So this should say.. some thing is not telling the computer to go into xorg or vesa or what ever thats called.. There must be an edit some place we can make that says.. USE THE VIDEO or use refresh or some thing. IN Desktop.. btw.. there is not changing the refresh rate. it has one.. and one only.. 60 mhtz.. 
when booting up.. successfully.. its ubuntus time bar.. then a short flash.. into a black screen.. and a flash again that shows the most in time mode.. X then circles.. when it fails.. it flashes.. stays black.. no second flash.. and no X marks the mouse. 
there really must be some thing here to fix. 


I have not had the chance to look over the other way of solving the problem. 
REISUB method . I am sure the link that was in the  note should explain it. 
I'll look into that later today when i am net connected. 
As to the PPPOE connection.. here below is the response in Terminal. 

rj@rj-laptop:~$ sudo gnome-ppp
[sudo] password for rj: 

(gnome-ppp:8447): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnome-ppp:8447): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
WVCONF: /root/.wvdial.conf

NOT SURE why a page setting is causing trouble.. but that seems to have some thing to do with it. the system seems to think there isn't a modem. I am goin to guess that when we chose a modem driver.. which did have more than one CHOICE.. i choice the recomended one.. it maybe the wrong one and or the hard ware may need some thing to be SEEN. when i hit the DETECT button.. it seems to see nothing.

I also think that the DVD thing is like said.. a codex issue. I was able to get just a bit more from the DVD this time. It says failed TO REPLY etc. SO that means its using a request that this DVD's codex is not responding to. OR it cant respond to it because this is not a windwos system. 
So i am going to give up on that part. Unless you have some amazing idea that solves it. 

the typing , keyboard/mouse issue: is slightly better when i turn off the touch pad. it appears that the whole board is very sensitive and there isnt a Sensitity setting that i can find. SPEED of mouse and so on.. but not for the keyboard. I played with it a bit and with the mouse on a lower setting it doesn't jump as much.. but it DOES still jump about. 
may just be a flaw of this lap top. Had some of that in Windows too. 


OH yeah.. the ls /dev Out put:
VERY LONG sorry. 

rj@rj-laptop:~$ ls /dev
adsp                ptyda  ptytc  ptyze       tty6   ttypa  ttyv8
agpgart             ptydb  ptytd  ptyzf       tty60  ttypb  ttyv9
audio               ptydc  ptyte  ram0        tty61  ttypc  ttyva
block               ptydd  ptytf  ram1        tty62  ttypd  ttyvb
bus                 ptyde  ptyu0  ram10       tty63  ttype  ttyvc
cdrom               ptydf  ptyu1  ram11       tty7   ttypf  ttyvd
char                ptye0  ptyu2  ram12       tty8   ttyq0  ttyve
console             ptye1  ptyu3  ram13       tty9   ttyq1  ttyvf
core                ptye2  ptyu4  ram14       ttya0  ttyq2  ttyw0
cpu_dma_latency     ptye3  ptyu5  ram15       ttya1  ttyq3  ttyw1
disk                ptye4  ptyu6  ram2        ttya2  ttyq4  ttyw2
dri                 ptye5  ptyu7  ram3        ttya3  ttyq5  ttyw3
dsp                 ptye6  ptyu8  ram4        ttya4  ttyq6  ttyw4
dvd                 ptye7  ptyu9  ram5        ttya5  ttyq7  ttyw5
fd                  ptye8  ptyua  ram6        ttya6  ttyq8  ttyw6
full                ptye9  ptyub  ram7        ttya7  ttyq9  ttyw7
fuse                ptyea  ptyuc  ram8        ttya8  ttyqa  ttyw8
hidraw0             ptyeb  ptyud  ram9        ttya9  ttyqb  ttyw9
hpet                ptyec  ptyue  random      ttyaa  ttyqc  ttywa
initctl             ptyed  ptyuf  rtc         ttyab  ttyqd  ttywb
input               ptyee  ptyv0  rtc0        ttyac  ttyqe  ttywc
kmem                ptyef  ptyv1  scd0        ttyad  ttyqf  ttywd
kmsg                ptyp0  ptyv2  sda         ttyae  ttyr0  ttywe
log                 ptyp1  ptyv3  sda1        ttyaf  ttyr1  ttywf
loop0               ptyp2  ptyv4  sda2        ttyb0  ttyr2  ttyx0
lp0                 ptyp3  ptyv5  sda5        ttyb1  ttyr3  ttyx1
MAKEDEV             ptyp4  ptyv6  sda6        ttyb2  ttyr4  ttyx2
mem                 ptyp5  ptyv7  sda7        ttyb3  ttyr5  ttyx3
mixer               ptyp6  ptyv8  sequencer   ttyb4  ttyr6  ttyx4
net                 ptyp7  ptyv9  sequencer2  ttyb5  ttyr7  ttyx5
network_latency     ptyp8  ptyva  sg0         ttyb6  ttyr8  ttyx6
network_throughput  ptyp9  ptyvb  sg1         ttyb7  ttyr9  ttyx7
null                ptypa  ptyvc  shm         ttyb8  ttyra  ttyx8
oldmem              ptypb  ptyvd  snapshot    ttyb9  ttyrb  ttyx9
parport0            ptypc  ptyve  snd         ttyba  ttyrc  ttyxa
port                ptypd  ptyvf  sndstat     ttybb  ttyrd  ttyxb
ppp                 ptype  ptyw0  sonypi      ttybc  ttyre  ttyxc
psaux               ptypf  ptyw1  sr0         ttybd  ttyrf  ttyxd
ptmx                ptyq0  ptyw2  stderr      ttybe  ttys0  ttyxe
pts                 ptyq1  ptyw3  stdin       ttybf  ttyS0  ttyxf
ptya0               ptyq2  ptyw4  stdout      ttyc0  ttys1  ttyy0
ptya1               ptyq3  ptyw5  tty         ttyc1  ttyS1  ttyy1
ptya2               ptyq4  ptyw6  tty0        ttyc2  ttys2  ttyy2
ptya3               ptyq5  ptyw7  tty1        ttyc3  ttyS2  ttyy3
ptya4               ptyq6  ptyw8  tty10       ttyc4  ttys3  ttyy4
ptya5               ptyq7  ptyw9  tty11       ttyc5  ttyS3  ttyy5
ptya6               ptyq8  ptywa  tty12       ttyc6  ttys4  ttyy6
ptya7               ptyq9  ptywb  tty13       ttyc7  ttys5  ttyy7
ptya8               ptyqa  ptywc  tty14       ttyc8  ttys6  ttyy8
ptya9               ptyqb  ptywd  tty15       ttyc9  ttys7  ttyy9
ptyaa               ptyqc  ptywe  tty16       ttyca  ttys8  ttyya
ptyab               ptyqd  ptywf  tty17       ttycb  ttys9  ttyyb
ptyac               ptyqe  ptyx0  tty18       ttycc  ttysa  ttyyc
ptyad               ptyqf  ptyx1  tty19       ttycd  ttysb  ttyyd
ptyae               ptyr0  ptyx2  tty2        ttyce  ttysc  ttyye
ptyaf               ptyr1  ptyx3  tty20       ttycf  ttysd  ttyyf
ptyb0               ptyr2  ptyx4  tty21       ttyd0  ttyse  ttyz0
ptyb1               ptyr3  ptyx5  tty22       ttyd1  ttysf  ttyz1
ptyb2               ptyr4  ptyx6  tty23       ttyd2  ttyt0  ttyz2
ptyb3               ptyr5  ptyx7  tty24       ttyd3  ttyt1  ttyz3
ptyb4               ptyr6  ptyx8  tty25       ttyd4  ttyt2  ttyz4
ptyb5               ptyr7  ptyx9  tty26       ttyd5  ttyt3  ttyz5
ptyb6               ptyr8  ptyxa  tty27       ttyd6  ttyt4  ttyz6
ptyb7               ptyr9  ptyxb  tty28       ttyd7  ttyt5  ttyz7
ptyb8               ptyra  ptyxc  tty29       ttyd8  ttyt6  ttyz8
ptyb9               ptyrb  ptyxd  tty3        ttyd9  ttyt7  ttyz9
ptyba               ptyrc  ptyxe  tty30       ttyda  ttyt8  ttyza
ptybb               ptyrd  ptyxf  tty31       ttydb  ttyt9  ttyzb
ptybc               ptyre  ptyy0  tty32       ttydc  ttyta  ttyzc
ptybd               ptyrf  ptyy1  tty33       ttydd  ttytb  ttyzd
ptybe               ptys0  ptyy2  tty34       ttyde  ttytc  ttyze
ptybf               ptys1  ptyy3  tty35       ttydf  ttytd  ttyzf
ptyc0               ptys2  ptyy4  tty36       ttye0  ttyte  urandom
ptyc1               ptys3  ptyy5  tty37       ttye1  ttytf  usbdev1.1_ep00
ptyc2               ptys4  ptyy6  tty38       ttye2  ttyu0  usbdev1.1_ep81
ptyc3               ptys5  ptyy7  tty39       ttye3  ttyu1  usbdev1.2_ep00
ptyc4               ptys6  ptyy8  tty4        ttye4  ttyu2  usbdev1.2_ep81
ptyc5               ptys7  ptyy9  tty40       ttye5  ttyu3  vcs
ptyc6               ptys8  ptyya  tty41       ttye6  ttyu4  vcs1
ptyc7               ptys9  ptyyb  tty42       ttye7  ttyu5  vcs2
ptyc8               ptysa  ptyyc  tty43       ttye8  ttyu6  vcs3
ptyc9               ptysb  ptyyd  tty44       ttye9  ttyu7  vcs4
ptyca               ptysc  ptyye  tty45       ttyea  ttyu8  vcs5
ptycb               ptysd  ptyyf  tty46       ttyeb  ttyu9  vcs6
ptycc               ptyse  ptyz0  tty47       ttyec  ttyua  vcs7
ptycd               ptysf  ptyz1  tty48       ttyed  ttyub  vcs8
ptyce               ptyt0  ptyz2  tty49       ttyee  ttyuc  vcsa
ptycf               ptyt1  ptyz3  tty5        ttyef  ttyud  vcsa1
ptyd0               ptyt2  ptyz4  tty50       ttyp0  ttyue  vcsa2
ptyd1               ptyt3  ptyz5  tty51       ttyp1  ttyuf  vcsa3
ptyd2               ptyt4  ptyz6  tty52       ttyp2  ttyv0  vcsa4
ptyd3               ptyt5  ptyz7  tty53       ttyp3  ttyv1  vcsa5
ptyd4               ptyt6  ptyz8  tty54       ttyp4  ttyv2  vcsa6
ptyd5               ptyt7  ptyz9  tty55       ttyp5  ttyv3  vcsa7
ptyd6               ptyt8  ptyza  tty56       ttyp6  ttyv4  vcsa8
ptyd7               ptyt9  ptyzb  tty57       ttyp7  ttyv5  xconsole
ptyd8               ptyta  ptyzc  tty58       ttyp8  ttyv6  zero
ptyd9               ptytb  ptyzd  tty59       ttyp9  ttyv7
rj@rj-laptop:~$

---

### Post by pytheas22 on 2009-02-03
Try running this command to fix the screen issues:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot.  Is it any better?

The modem won't work because it's trying to use /dev/modem as the modem device, and that doesn't exist.  Did you try opening gnome-ppp, pressing the 'Setup' button and then clicking 'Detect' in the window that pops up in order to have it auto-detect your modem?  If that doesn't work, try specifying '/dev/ttySL0' as the modem device.

Unfortunately, I'm out of ideas on the DVD.  You might have better luck if you start a new thread in the 'multimedia and video' section of the forums.

---

### Post by forestwalkerjoe on 2009-02-03
i am about to reboot after the dpkg thing.. and i did check the detect modem thing.. i can only find these possibles. the closest to your suggestion is : /dev/ttyS0  the others are /dev/ttyS1 S2 or S3. 
I'll test those upon reboot. 
As to the DVD thing.. i wont ask for that anymore. Its just the DVD.. and thats ok. 
BTW.. after that special update you had me do for DVD.. i did notice it also downloaded some sort of Java thing.. and so many things are working smoother. Some small effects work.. web page browsing is seemingly smoother.. i went into YOUTUBE.. and though the full screen is still jocky.. its not even close to as bad as it was.. but minor screen is near to perfect. 
IN HOPES that config change we just did works out the issue.. 
I'll talk to you .. in hopes to be, a few minutes. 

PS: ok.. success. the dpkg update thing did some thing. I rebooted 2 times. with full shut down not just reboot and it came up faster.. and cleaner.. and with out the black screen issue. i made sure to check the screen savers.. and all is again well in the world. 
As to the Modem: 
i changed it as you suggested.. but detect says no modem detected. 
when i just hit connect.. it fails to find a modem.. and this is the log report it gave:
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
IN hopes we can solve the modem issue.. 
I am greatful for all the time you have put into the rest of this mess.. once i am sure i have worked every thing i should , out on this system.. then i will have questions for you or whomever is going to be working with me on the install for the Family pc i was telling you about. 
I DO HAVE ONE more idea i would like to put by you... really a question:
when i did the install here on the lap top. i think i had bad information on how to go about that. i have the partitions set up in such a way that windows is first.. as it has to be.. then there are 3 areas. Swap, root and i cant recall what the last one is called , i think it maybe home. i was told by another person that my sizes on each are all wrong. that i have swap too large.. and this " HOME" File.. is also too large. if these are true.. then i would like to know HOW TO RESIZE these and just how big should they be? or if that one area is unneeded.. can we colapse that and then integrate that back into the root? or is this more trouble than its worth? 
that was only to maximize the amount of space IN this ubuntu system so that i am not wasting it. 
once i know what is best for the sizes.. i will not make that same mistake in the new install for that family. 
i was told i dont need to make any space for sharing between windows and linux.. as i can mount that at will.. I should have time soon.. to go to that families house and resize their drive.. partition it.. that is why i need this info.. then start a proper install of UBUNTU there. they only have 58 gigs.. divided between 4 persons. THUS i really want to make sure i utilize the best CONFIG. once they have it installed.. updated.. i can tweek every thing.. as we did here on the lappy.. so they are not going to have any troubles .. pretty much again. 
i will have them buy an exterior drive for holding all their MUST keeps.. like music.. and then.. they can use the burning software to burn the ones they want. 
IF i can pull this off.. i will have saved this whole family a lot of trouble. THEY WERE GOING TO BUY A NEW PC .. and were not sure if they wanted VISTA or MAC. my neck stings even hearing them say VISTA. IF we install properly and workabily onto their system A DUEL booted WIN / UBUNTU.. they will be forever impressed. their 15 and 14 year olds will probably become LINUX Geeks.. thanks for all the extra help. 


FWJ

---

### Post by pytheas22 on 2009-02-03
For partitioning: the rule-of-thumb for swap is that it should be double the size of your RAM--so if you have one gigabyte of RAM, make a two-gigabyte swap partition.

Keeping /home on a separate partition is not necessary, but can be a good idea because it makes it much easier to reinstall Ubuntu without losing user files and settings.  /home is where user files are stored--like videos, pictures and documents.  So size it accordingly--depending on how many personal files the family will have (keeping in mind that some may be left on their Windows partition), /home can be as small or as large as they need.

A / (root) partition is necessary, as it stores all applications, among other things.  I'd recommend that you give about 10 gigabytes to it.  This should be plenty (really you could go as low as 4 or 5 if you needed, but that wouldn't leave much space for installing extra applications).

I'm not sure why the modem won't work (it doesn't help that I have no experience in this area).  I have a modem in one of my computers and will try to take a look at what the settings would be there--I've never used that modem under Linux, but it may give me a better idea of how to help you.  Unfortunately, I leave that computer in the library and won't have a chance to get to it until tomorrow or Thursday.  But I'll get back to you.

You could also try starting a new thread dealing just with your modem issue; you might attract the attention of someone who knows more about Linux and modems than me.

---

### Post by forestwalkerjoe on 2009-02-04
You have been such a Trooper.. and even with no understanding of things like standard Dial out modems.. you sure showed me so much. 
I will go on to making a proper install on my own Desk top.. until i can set up a date to do the Families system as i have been saying. 
so.. at risk of wearing you out.. some time in the next couple days or so.. i'll be starting the INSTALL of UBUNTU on my own Desktop. 
Its a much newer system with a lot of great hard ware so.. should not be as much of a problem as the Lappy.. or the PC that the family has. Theirs is not a great PC.. not bad.. but alot of their hard ware is ON BOARD.. and Generic.. 
As soon as i can get there.. I'll do one of the codes you asked me to do.. and show you what they got. 
Theirs looks to not be very soon. 
I have to go back in.. and REINSTALL WINDOWS.. Factory install disk.. find any missing drivers.. etc.. ONCE i get it back to normal.. I'll partition in prep for the UBUNTU install. 
THEN we get to have the FUN stuff. 
LIKE setting up their printer and so forth. That part i can do .. with little help.. the INSTALL.. that is another story. 
I'll try and config as many HELPS as i can for them.. so they have the best UBUNTU LINUX experience I can think of.
I will consider telling them.. now is about the right time to buy an exterior drive.. they have very little real space for sharing with 4 persons. 
Thanks again. 
I'll post on the results OF reconfiging my lappys partitions and such in a day. 
FWJ

---

### Post by pytheas22 on 2009-02-04
One warning: you should install Windows before installing Ubuntu.  Otherwise Windows will overwrite the Linux bootloader, and it's difficult to fix.  So install Windows first, then Ubuntu.

---

### Post by forestwalkerjoe on 2009-02-15
2-14-09  

I was thinking.. You had asked if I had a burner or if I was willing to download a different type of Ubuntu and install fresh with  that. 
I am not sure why it loads as a server version.. from every thing I can see.. the 8.10 Ibex version I have is the standard one. 
But if this is some how the server version.. and the one you are asking me about is better, then I was thinking..  I installed a WUBI on my Desktop PC.. 
the WUBI I installed has an ISO creator/burner thing right? 
I have a Burner on my windows system.. which now has the WUBI.. I would assume IT has its own program for that. 
If you can resend the link you wish me to attempt to burn, I'd be willing to do all that. 

As to Ram.. for now.. I still have not had the time to find the right sized screw driver to open up the bottom of the Lap top. 
ONCE I have that open.. I can find more ram and soon.. pay for it. 
I would still like to start the install of the fresh version before the ram arrives. Mostly because I am so broke I wont be able to get that for at least a week or so. 

I am even considering doing a full back up of the Windows side of the lap top  and fresh installing that .. then doing a WUBI on it. 
I'll defer to your opinion of using a Wubi on a small system like this. 

If you really think that another style of Ubuntu Linux will have a better chance of fitting my hardware.. I am all about that. 
I will need help getting the Ether Card reset up.
 From what I could tell.. the SOHO WARE card.. ND5120-E is not standardly supported.
 It took some time and a lot of help to get it to run.
It "is" all I got though. 
The on-board modem is for dial-out.. and it only has a driver that will support 14.4 --which so far-  has not been able to function either. 

So.. the connection is a big deal on this reinstall. 
If I do accomplish the reinstall of Windows 2k and then install using the WUBI thing.. I wont have to worry about all the resizing of the system. 
I'll just have to find all the Install able stuff.. like DVD Codex and all that.. then get the right type of DVD player running.. I have been using the VLC thing and IT works and the standard Totem has major issues on this hardware. 

So  Ether card.. DVD player and codex's.. Sound support etc. 
Needs 3d for much of my needs.. and I can not just let it install the video as Vesa. The resolution is so bad it almost makes it not usable. 

If I can get the Savage card drivers working.. it would be the whole REASON I was willing to take this thing back to another Install. 

What do you think? 
I wont push on this but I really would prefer to have some one support my move here. 
As to my Desk Top I sent you a bunch of little questions to help me solve.. 
I am interested in becoming what ever the system needs me to be.. so I DON'T HAVE TO ASK permission every time I want to download some thing OR have to log in ever time I do a reboot. 
THEN I would like to change the , I think it's called Chain Loader in the Grub menu thing. I am nervous to try that myself.. because a few years ago.. I was given some stuff to do in Grub Menu.. and I locked myself out of my own system. 
There was a type of HD dance going on.. I put in the write code but some how it would not register correctly.. so it wouldn't let me into Linux. 
I had to load a LIVE CD.. and then with some one on GAIM instant messenger.. we opened a terminal and solved the problem. I don't have any access to a person who would walk through stuff ON Instant messenger now.. so I'll defer to your opinion on that too. 

PS: ok.. i was thinking about it.. I should NOT do a WUBI on this laptop. 
Wubi's don't work well with 3d or that kind of video support. I already have that kind of problem now. 
So, once i get the windows system reset.. I'll have you guide me into a better partitioning and we can go from there. 
For now.. i need to know how to do this ISO thing you were telling me about. 
ONCE i have a good set of instructions to what i should expect.. I'll test it on a disk.. and then we can start playing with the REBUILD you were talking about. thanks again. 



FWJ

---

### Post by pytheas22 on 2009-02-15
> 
I am not sure why it loads as a server version.. from every thing I can see.. the 8.10 Ibex version I have is the standard one.
But if this is some how the server version.. and the one you are asking me about is better, then I was thinking.. I installed a WUBI on my Desktop PC..

I could just be forgetting, but I don't remember talking about installing a different version of Ubuntu, so I'm not sure why I suggested it or which version I thought you should use.  Could you find the post where I mentioned that?
> 
If I can get the Savage card drivers working.. it would be the whole REASON I was willing to take this thing back to another Install.

It remains a mystery to me why your video card was working with 3D acceleration originally but then stopped.  Reinstalling would probably fix that.
> 
THEN I would like to change the , I think it's called Chain Loader in the Grub menu thing. I am nervous to try that myself.. because a few years ago.. I was given some stuff to do in Grub Menu.. and I locked myself out of my own system.
There was a type of HD dance going on.. I put in the write code but some how it would not register correctly.. so it wouldn't let me into Linux.

I presume you want to change this because you want Ubuntu to be the default boot option.  If so, you'll need to edit the boot menu *in Windows*, if you installed using wubi.  wubi doesn't actually use grub; it uses the Windows boot loader, which Linux can't edit.  If you install Ubuntu on its own partition using the live CD, it would be the default boot choice, and it would use grub.  That's one of the major differences between wubi and the traditional installation.
> 
I had to load a LIVE CD.. and then with some one on GAIM instant messenger.. we opened a terminal and solved the problem. I don't have any access to a person who would walk through stuff ON Instant messenger now.. so I'll defer to your opinion on that too.

I don't use any instant messaging services, but if you want instant help, you could try the Ubuntu IRC channel, where you can get live support.  I've never used IRC, but I believe Pidgin (formerly known as gaim) supports it.  More information [here]("http://www.ubuntu.com/support/community/chatirc").
> 
Wubi's don't work well with 3d or that kind of video support. I already have that kind of problem now. 

Actually wubi should support 3D acceleration just as well as a traditional system.  I think that if you reinstalled Ubuntu using either wubi or the live CD, your graphics would work again as you want.

---

### Post by forestwalkerjoe on 2009-02-17
i was reading over the note you left me.. and did some searching for the Person who asked me to do another install. I found the person. It was NOT you.. sorry.. i have only spoken to a few in here and you had helped the most.. i must have been tired. 
here is the link to the last of the [persons ideas]("http://ubuntuforums.org/showthread.php?t=1061015&page=2"). 

Sorry for the long letter after the link.. but i was thinking while at work tonight.. and figured i would write you what I was thinking about. 
It might help us get a grip on what to do next. 

------------------------------------------------------------------
(Letter)
 I am not sure , I guess maybe it was not you who suggested this was a server system. 
I have not had time to go back and read all the other posts to see who was the one.. yesterday I was going to hunt that down.. but the Main archive for Ubuntu was down. 

I'll see if I can find the who and the why of it.. but either way.. it was supposed to solve a problem in how I created the partitions. 
Also to solve the Black screen problem I have been having. 
If it was not you I spoke to.. here is the problem in brief. 

Some one.. I think it was you.. helped me get the Savage x driver set up in my system.. so that 3d and so on.. would work .. but.. every time I start up the lap top.. I have a 1 in 5 chance that it will load up Black screen.. no visuals at all. Some one said.. there is a Brightness issue with this form of Video driver. So, adding some thing to the kernel.. might be needed. 
I am thinking its not that hard.. as the home partition is having issues. 
Using Vesa is bad as it's highest Resolution is more like Donkey Kong. 
There is a possibility that the reason we can not get it up and stay up.. ( it works while I am using the Lap.. until I reboot)
is the fact that when I created the partitions I some how didn't set up the HOME file correctly. 
It wont mount. 
So if the details on how the system needs to load the video driver is in the HOME file.. then it cant reach it. 
Thus..  I was wanting to re designate the area that was to BE the HOME.. with a different tag.. I guess.
When I open the partition manager.. its there.. but I am not sure what I am supposed to tell it.. to BE the right kind of HOME file. 
So.. it was said.. it might be easier to just reinstall the system.. with the right divides. 
It was also suggested I buy more ram.. this system I guess can hold 1 gig.. but has only 2 sticks total of 256. 
I have not been able to find a Micro screw driver yet.. so I can take the darn screws off the back of the lap.. and look at the 
Ram type.. and so on.. and then order the right kind for the lap. I am willing to go forward with the install with out the Ram
till I can get the ram and install it. It shouldn't effect the install one way or the other. It will just move better once I get the Ram upgraded. 
While talking about that reinstall , I was told from some OUTPUT they read.. that this was Ubuntu  SERVER.. not Ubuntu Desk top.. and the Desktop one would be easier on setting up hardware than the one I have. 
I backed up most of my stuff.. I'd still have to do a little of that.. as I use this lappy every day.. but the next big deal was the person telling me WHICH version of Ubuntu I should use.. then HOW to down load.. and Burn an ISO.
I have had no success with that so far.  
In the past.. back in version 6.. I had Ubuntu on a disk that was sent to me.. every time I tried to BURN a disk or make a copy.. it would corrupt. Every time I tried to download a link to a Distro I wanted to look at.. I used to have 8 distros on one PC.. it would corrupt and then not load when I wanted to trial it. I am sure I am doing some thing wrong.. I can burn other things just fine. 
So since I have Ubuntu on my desk top.. Ibex 8.10.. same as this lap top.. I could always have some one show me.. how to download.. and I guess "compile"? An ISO.. then what program to use to burn it . And we could go onto the next step.. 
YOU.. or whom ever that was.. telling me exactly what I should do in the partition set up.. so I could get the best use out of this little 30 gig drive.. which is split between WINDOWS 2k and the impending Ubuntu install. 
My only real concern here.. was You helped me set up the SOHOWARE Ether Card.. and it really took a bit to get it set up.. so that I had an INTERNET connection to Update the little laptop. 
So the Needs here are : 
* How to properly download.. convert and burn an ISO, using a Ubuntu system .  ( Then , which is best ?)
* the Proper way to set up a partition for an Ubuntu Install / Duel boot. 
*  TALK about if WUBI might be best on this laptop?
* Is there a way to load the video driver into the kernel?
(we might not need this if the issue with the Home file is the problem with the Black Screen)
* I need to track down the procedure to install the right driver for this SO HO card. 
( I can get that all downloaded and put on a flash drive and the Terminal Code to install it , before I do the wipe of drive.)
Later on.. I am goin to look into buying  a larger hard drive. I have seen some on  E-bay with this Viao's Model number, but I have never replaced a hard drive on a lap top before. There is a 160 gig drive for 80 bucks. I am sure that with 1 gig Ram, might make this system a bit quicker. I hope that also gives me the Ubuntu Special Effects. It fails when I try to turn them on now. 
----------------------------------------------------------------
Again sorry for the long letter. 
I hope we can get the system up to snuff with your help. The guy who made the suggestions.. RED some thing.. has not been responding to my notes lately. 
So I am on your Mercy to help me out. 
thanks
FWJ

---

### Post by pytheas22 on 2009-02-18
Sorry for the slow response--I've been quite busy lately--but here are answers to your points:

> So if the details on how the system needs to load the video driver is in the HOME file.. then it cant reach it.
Thus.. I was wanting to re designate the area that was to BE the HOME.. with a different tag.. I guess.
When I open the partition manager.. its there.. but I am not sure what I am supposed to tell it.. to BE the right kind of HOME file.

The video driver is not under /home; these issues can't be related.  I'm not sure why you get a black screen at some boots, but the next time it happens, try doing this and tell me the results:

1. what happens if you press control-alt-F2?  Do you see a terminal where you can log in?
2. what if you press control-alt-backspace?
3. do you hear any sounds?
4. does the orange Ubuntu bar load completely and then you crash to the black screen, or does the screen come first?
> 
While talking about that reinstall , I was told from some OUTPUT they read.. that this was Ubuntu SERVER.. not Ubuntu Desk top.. and the Desktop one would be easier on setting up hardware than the one I have. 

I'm not sure who told you that, but if you have a graphical desktop, you're using normal Ubuntu.  Ubuntu server doesn't come with a desktop--i.e., no mouse, no Firefox, no graphics, just a command line.  You don't want to use Ubuntu server on your laptop.
> 
In the past.. back in version 6.. I had Ubuntu on a disk that was sent to me.. every time I tried to BURN a disk or make a copy.. it would corrupt. Every time I tried to download a link to a Distro I wanted to look at.. I used to have 8 distros on one PC.. it would corrupt and then not load when I wanted to trial it. I am sure I am doing some thing wrong.. I can burn other things just fine.

Maybe you're not burning the ISO file properly.  There's a good guide [here]("http://www.psychocats.net/ubuntu/iso") on how to burn Ubuntu CDs properly in Windows.  Also, when you burn, choose the lowest burn speed possible; this helps to avoid corruption.
> 
* the Proper way to set up a partition for an Ubuntu Install / Duel boot. 

There's an illustrated guide to partitioning [here]("http://www.psychocats.net/ubuntu/separatehome"), including the creation of a separate /home partition (which is not necessary, but is a good idea).  You will need an Ubuntu live CD to carry out these steps.  On a 30-gigabyte drive, I'd go with something like this:
```

| 10 GB Windows| 5 GB Ubuntu / | 1 GB swap | 14 GB Ubuntu /home |
```

But it depends on how much space you need for Windows, more than anything else.  I'm assuming ten gigabytes is sufficient, but I don't know what you have on Windows so it's hard to say.

Also, a cautionary note: make sure you back up all your important files (in both Windows and Ubuntu) before partitioning, because there's an inherent risk in editing your partition table.  Nothing should go wrong, but it's always a possibility when doing stuff like this.
> 
TALK about if WUBI might be best on this laptop?

wubi should work fine as well.  There are a few minor disadvantages, but it can also be more convenient because it saves you from having to burn an ISO and partition your hard disk.  Your video and other problems are going to be the same whether you reinstall using wubi or the live CD.

> 
I need to track down the procedure to install the right driver for this SO HO card.

Follow these steps to make the ethernet card work:

1. download [this file]("http://burnthesorbonne.com/files/NE2K.cis"), then transfer it to the Ubuntu machine and save it on the desktop there
2. run these commands:
```

cd ~/Desktop
sudo mv NE2K.cis /lib/firmware
```

Then reboot, and the ethernet should work.
> 
There is a 160 gig drive for 80 bucks. I am sure that with 1 gig Ram, might make this system a bit quicker. I hope that also gives me the Ubuntu Special Effects. It fails when I try to turn them on now.

Unfortunately, the special effects have to do with your graphics card, not your hard disk size or RAM.  If they didn't work originally, before you started having video problems, there's probably no way to make them work.  And unfortunately you can't really install a better graphics card into a laptop.

Also, if you do choose to buy a new hard drive and RAM, be careful to make sure they're compatible with your laptop.  RAM especially can be complicated because there are different kinds and different speeds, and older computers are often not compatible with newer RAM.  You should consult the manual that came with the computer to see what kind of RAM it will support (SDR, DDR, DDR-2...) and which speeds it supports.  This stuff can be very confusing, so just make sure that you double-check everything before buying.

---

### Post by forestwalkerjoe on 2009-02-19
wow.. that was a lot of information. I have read through it lightly. Thanks ! That helps answer a lot. 
I did already download the ISO on my Desktop Ubuntu side. 
I have been trying to use the Ubuntu DVD burning software and there are two. I put in a DVD-R and it seems to start up.. goes through all the stuff.. starts to burn.. or it seems to start.. and then it fails.. says has to abort. 
(DVD Creator and or BRASERO DISK BURNING)
I am also noticing that my keyboard is acting up.. Desk top not laptop. 
all the letters on the keyboard are fine as far as i can tell..with the exception of the left handed Shift letter c. i can HIT caps and then hit C but not just type c in  Caps. 
never had the problem before. 
Shift seems to work for every thing else.  JUST Not C. 
anyway.. going back.. 
what i need to understand is why is this ISO not burning in Ubuntu system. 
I am tempted.. but hate using Microsoft.. of downloading the software stuff you were telling me about..for XP windows. 
i would prefer to learn how to burn things ISO in Ubuntu. 
I dont know if the system is stopping it's dialog in burning.. and then aborting because of a failed response? or if there is some thing wrong with the burner. I dont think its the hardware itself. 
BUT these are NEW DVD-R's out of the package. I cant waste them. 
I have been reading here and again about burning.. and I did find a code that you write into Terminal that helps you burn things.. but it's set up to burn for REDHAT. i am nervous to try it on Ubuntu and get it all wrong. I want to make sure it gives the LIVE Cd thing. so i can boot into it as a demo for anyone i want to show this to. 
Would it be easier to take the disk i have of 8:10 and make a copy to copy? will it let me do that with all the LIVE CD stuff? 

FWJ

---

### Post by pytheas22 on 2009-02-20
What is the exact error message you get from Brasero or CD Creator when trying to burn?  It's hard to say what could be wrong without knowing exactly what Ubuntu thinks is wrong.

Also, check the md5 sum of your ISO file to make sure the download wasn't corrupted.  To get the md5 sum, open a terminal and type these commands (assuming the ISO file is on your desktop):
```

cd ~/Desktop
md5sum *iso
```

The md5sum for the 32-bit Ubuntu 8.10 live CD should be 24ea1163ea6c9f5dae77de8c49ee7c03.

As for the problems with your keyboard, does it happen in Windows too?  If so, it's probably just your keyboard going bad, and beyond taking the keys off and trying to clean the stuff, there's not much you can.  If it only happens in Ubuntu, we can look at possible solutions.

---

### Post by forestwalkerjoe on 2009-02-20
starting last one first.. I was able to get what ever that was to fix on the keyboard. A guy in a forum told me some things to get it to revert to default in GNOME.. i am not happy about that because i had to redo every saved issue in the desk top. 
And then with it.. came an issue i think "I" messed with the wrong thing and screwed up the sound in my system again. NOW i have it able to work.. but the settings down save and the Pulse audio keeps trying to find a server at reboot. 
I can mess with it again.. get the sounds back on.. but it reverts every time i reboot. 

i can give you code out put on that later. here is the ERRORS when i try and BURN in DVD format. 

it seems to fail as in.. stops working. but i'll put it in now and see if i can find the exact log or some thing to hand you.. as to what IS or IS NOT happening. 
**Error writing to disc**
[I]There was an error writing to the disc:
Unhandled error, aborting[/I]
that was in DVD Creator. 
here is Brasero:

it does check sum..starts up the timer for burning.. then
 begins the write.. and never gets past.. minute. 
THIS IS LONG>. but here is the LOG on it. 

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_REJDPU toc = nil
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_L7HDPU toc = nil
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_start_progress
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/rj/Desktop/ubuntu-8.10-desktop-i386.iso (size = 732766208)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage Called brasero_job_set_progress (0.021264)
BraseroChecksumImage Called brasero_job_set_progress (0.039165)
BraseroChecksumImage Called brasero_job_set_progress (0.063656)
BraseroChecksumImage Called brasero_job_set_progress (0.083810)
BraseroChecksumImage Called brasero_job_set_progress (0.108375)
BraseroChecksumImage Called brasero_job_set_progress (0.134848)
BraseroChecksumImage Called brasero_job_set_progress (0.160784)
BraseroChecksumImage Called brasero_job_set_progress (0.186936)
BraseroChecksumImage Called brasero_job_set_progress (0.209617)
BraseroChecksumImage Called brasero_job_set_progress (0.234030)
BraseroChecksumImage Called brasero_job_set_progress (0.262384)
BraseroChecksumImage Called brasero_job_set_progress (0.292435)
BraseroChecksumImage Called brasero_job_set_progress (0.321591)
BraseroChecksumImage Called brasero_job_set_progress (0.349478)
BraseroChecksumImage Called brasero_job_set_progress (0.374683)
BraseroChecksumImage Called brasero_job_set_progress (0.403688)
BraseroChecksumImage Called brasero_job_set_progress (0.431956)
BraseroChecksumImage Called brasero_job_set_progress (0.457713)
BraseroChecksumImage Called brasero_job_set_progress (0.481953)
BraseroChecksumImage Called brasero_job_set_progress (0.511146)
BraseroChecksumImage Called brasero_job_set_progress (0.534352)
BraseroChecksumImage Called brasero_job_set_progress (0.553930)
BraseroChecksumImage Called brasero_job_set_progress (0.581136)
BraseroChecksumImage Called brasero_job_set_progress (0.609213)
BraseroChecksumImage Called brasero_job_set_progress (0.621382)
BraseroChecksumImage Called brasero_job_set_progress (0.642131)
BraseroChecksumImage Called brasero_job_set_progress (0.669437)
BraseroChecksumImage Called brasero_job_set_progress (0.698406)
BraseroChecksumImage Called brasero_job_set_progress (0.722445)
BraseroChecksumImage Called brasero_job_set_progress (0.749455)
BraseroChecksumImage Called brasero_job_set_progress (0.771456)
BraseroChecksumImage Called brasero_job_set_progress (0.794889)
BraseroChecksumImage Called brasero_job_set_progress (0.818858)
BraseroChecksumImage Called brasero_job_set_progress (0.848014)
BraseroChecksumImage Called brasero_job_set_progress (0.873772)
BraseroChecksumImage Called brasero_job_set_progress (0.900035)
BraseroChecksumImage Called brasero_job_set_progress (0.928864)
BraseroChecksumImage Called brasero_job_set_progress (0.951836)
BraseroChecksumImage Called brasero_job_set_progress (0.966428)
BraseroChecksumImage Called brasero_job_set_progress (0.993681)
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage setting new checksum (type = 0) 24ea1163ea6c9f5dae77de8c49ee7c03 ( before)
BraseroChecksumImage finished track successfully
BraseroChecksumImage stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=4
	-use-the-force-luke=tracksize:357796
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/home/rj/Desktop/ubuntu-8.10-desktop-i386.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/rj/Desktop/ubuntu-8.10-desktop-i386.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: reserving 357796 blocks
BraseroGrowisofs stderr: , warning for short DAO recording
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 53:07 RBU 100.0% UBU   2.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 75:53 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 98:39 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 129:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 151:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:     1605632/732766208 ( 0.2%) @0.0x, remaining 174:33 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2524)


and here is the OUTPUT you asked for.

rj@ubuntu:~$ cd ~/Desktop
rj@ubuntu:~/Desktop$ md5sum *iso
24ea1163ea6c9f5dae77de8c49ee7c03  ubuntu-8.10-desktop-i386.iso
rj@ubuntu:~/Desktop$ cd ~/Desktop
rj@ubuntu:~/Desktop$ md5sum *iso
24ea1163ea6c9f5dae77de8c49ee7c03  ubuntu-8.10-desktop-i386.iso
rj@ubuntu:~/Desktop$

---

### Post by pytheas22 on 2009-02-21
I'm not able to find much on Google with those error messages, but some people do report issues burning CDs in Ubuntu 8.04 and 8.10.

The simplest solution might be just to burn it in Windows.  Otherwise, you can burn the disk image manually from the command line by typing:
```

sudo wodim -v dev=/dev/scd0 driveropts=burnfree ~/Desktop/ubuntu-8.10-desktop-i386.iso
```

Does that work?  If not, what output do you get?  That may provide some more useful bits for googling with.

---

### Post by forestwalkerjoe on 2009-02-22
I think i might know the trouble. 
I was able to get the CD burner to work for a CD in Ubuntu. NOT because of your code.. i have not had the chance to try that yet. 
My first try was not a CD.. it was a DVD.. which my windows system has the software to do burning. I am betting the failure was.. i dont have what ever is needed in Ubuntu to Burn DVD'S. So it goes through all the process.. till it comes time to actually burn and its not responding correctly.. because it doesnt have.. Driver, or permission or code to DO what the software burner wants. 
I'll try out your CD code.. and see if that was smoother.. the 2 CD burns i did.. were really a pain.. but i tested the burns.. and they are exactly LIVE CD burns like i wanted.

---

### Post by forestwalkerjoe on 2009-02-25
ok.. so we don't confuse the two.. i had two projects that i was working on.. one of the reasons i had to burn a copy was the laptop..the other was a desk top with wubi.. its the one with the sound issue. I have put that sound issue on the shelf for now.. as i can log in and out as someone suggested.. and it doesn't save the settings.
So, going back to the lap top... 
Laptop issue: the Black screen issue and corruption in 3d.. 
 i have whipped the drive.. reinstalled Win2k.. made a wubi in the system.. installed it pretty good i think..got the soho ware card to install and work for DSL ..thank you for the simple way to do that.. that worked..
   but now i have one little problem.
 i set it up to install some supported and i guess experimental stuff. So it did its update.. and installed generic kernel image 12.27 something version 12. the install off CD had versions 7 and 11. i chose to use version 11 .. which i thought had solved my screen black issue. but it came back after a few reboots. I DID find the solve for that. by gediting the xorg file.. you showed me how to do that once.. and added in the device area , an option [PCI statement we found]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617") a ways back. which solves the brightness issue. by asking it to work the device monitor in high brightness. it also had a comment to solve corrupting in xorg when 3d is working. So Yeah! we solved it.. so far as i can tell.. but.. here is the deal... 
MY issue now.. is in the Update manager it keeps telling me i have a security update for kernel image version 7...linux-image-2.6.27-7-generic which fails to install because it fails to back up the. boot record. but every time i reboot it tells me i have package manager updates.. and its JUST that one..as said above..  I am liking the way it's installed right now.. so i don't think  i want this update for version 7. everything else seems to be ok.. 
well that and i can not get DVD to work.. and there is some sort of glitch conflict with Flash player plug in.. if i want to use audio video on Youtube or other flash based Firefox websites. 
if you can help me resolve this.. it would be a success. 
I am sure these are easier to solve.. going back to the Desktop.. i am at a loss. it is coming down to.. if i can not solve it.. i may actually.. have to whip out that wubi on Desktop.. and Start all over again. 
NO one is responding to a absolutely beginner thread i put up on that issue. NO ONE View. 
thanks again for the help. 

FWJ

---

### Post by pytheas22 on 2009-02-26
Could you describe the audio glitch in the flash player in more detail, please?  I don't know much about these kinds of issues myself, but hopefully if you give me more to go on, I'll be able to find something relevant through Google.

Unfortunately, I'm not really sure that I have any more ideas on why your computer won't burn DVDs.  What kind of DVDs are you trying to create?  Are they from ISO files or some other kind?

---

### Post by forestwalkerjoe on 2009-02-27
is on the laptop again. I had to uninstall the wubi and reinstall. 
BUT.. that linux image issue i had above.. is back. 
it keeps trying to upgrade the linux 27-7 image. but that upgrade fails.. some thing to do with a .boot not being seen or some thing. 
when i looked over the update manager there is a tab for discriptions.. and it says THIS: 

 ```
This package contains the Linux kernel image for version 2.6.27 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 
```
I have no idea what a Meta package is.. nor if i want this Upgrade at all. IN my last wubi.. i went into the root terminal on boot up and did an autoremove of this package because it was failing to install. ALL was fine until i tried to do a code for installing restricted pacakges for DVD. some where in that add remove.. I used a code from the forums to add and remove some things and then used medibuntu's repository to install java and so on. .. it crashed the system and then i could not complete a boot. it would get all the way to the log in.. and screen would go all white.. funny.. how i had a black screen issue.. which we solved and then i have an ALL white one. after trying every thing i could.. i came to the conclusion that i had corrupted some thing and needed to reinstall. I am in that install now.. but have run into the linux image issue again. SO.. if i can find out why this linux image is trying to install.. and what kind of Install i should do.. it could solve this problem. i have already done the DVD upgrade again.. and installed VLC for the DVD player.. i have used most of the tricks you and the reddog guy showed me how to use. INCLUDING the fix to the xorg.conf that allows me to boot up without black screen. I would just like to get ON WITH IT.. so i can go back to my original plans. Get lap top up and running.. to be a support LAP for my installation on my friends PC. MY own DESK TOP issues.. will have to be looked at later. once the LAPPY is secured again.. I may have to do the same thing to it.. back it up and reinstall the WUBI.. then try and figure out what is wrong with the dern sounds.. i have been given a few ideas.. but what ever has been done on the DESKTOP.. has caused it to NOT save settings for the Pulse Audio. I am sure this is an easy fix once i reinstall. 
GOT any ideas on how to do the meta package install of this ABOVE Linux image? 
thanks for your long suffering help. 
FWJ

---

### Post by forestwalkerjoe on 2009-02-27
it was suggested i do the upgrade in terminal. so.. i did try. 
it finds the upgrade.. and requests an auto remove.. of the 27-7 image.. but fails in the upgrade. before i go on to the full upgrade.. which i am not sure if i just messed up the system or not.. i'll post what it says and its errors. 
 ```
rj@ubuntu:~$ sudo apt-get intall update
[sudo] password for rj: 
E: Invalid operation intall
rj@ubuntu:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com intrepid Release.gpg                         
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US              
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://packages.medibuntu.org intrepid Release.gpg
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Ign http://packages.medibuntu.org intrepid/free Translation-en_US
Hit http://us.archive.ubuntu.com intrepid/universe Sources                     
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Hit http://packages.medibuntu.org intrepid Release
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Reading package lists... Done
rj@ubuntu:~$ sudo apt-get intall linux-image meta-package
E: Invalid operation intall
rj@ubuntu:~$ sudo apt-get install linux-image meta-package
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package meta-package
rj@ubuntu:~$ sudo apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-image
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 2880B of archives.
After this operation, 32.8kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid-updates/main linux-image 2.6.27.11.14 [2880B]
Fetched 2880B in 0s (3556B/s)
Selecting previously deselected package linux-image.
(Reading database ... 152215 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.27.11.14_i386.deb) ...
Setting up linux-image (2.6.27.11.14) ...
rj@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
The following packages will be REMOVED:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 52.0MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
rj@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-7-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 152218 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rj@ubuntu:~$ 

```
I hate it when they are long like this. Sorry. maybe you can tell me what you SEE.. when i am trying this. I am tempted to reboot and see if there is a change.. but , after all the work i did today to get the laptop back up and running.. and concerned i just flubed this install. 

hope you have some good news for me. 

FWJ

---

### Post by unutbu on 2009-02-27
I see you've installed linux-image, but perhaps not linux-generic-* and linux-headers-*.

How about do the following:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-20090227
sudo apt-get install linux-generic linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-headers-generic linux-image-2.6.27-11-generic linux-image-generic
COLUMNS=200 dpkg --list linux*
```

Then post all the output.

You will be asked if you want to replace your current menu.lst with a new menu.lst.
It is completely safe to say yes, because the first command above made a backup copy of your current menu.lst. 

Reboot and select the new 2.6.27-11 kernel in the GRUB menu. See if your setup is working using this kernel. 

The error you are getting when doing "sudo apt-get upgrade" will be irrelevant if the 2.6.27-11 kernel works for you.

Here are some suggestions on how to upgrade. Not everyone may agree with the following, so, as always, use your own judgment it you think it makes sense for you:

[list]
[*]Backup your data before you do any upgrades. 
[*]Make a list of all the packages you install, take notes every time you alter your system. This way, if your system ever gets broken, at worst all you have to do is reinstall, copy your data from backup, and then follow your notes on reinstalling extra packages, and any other system alterations.
[*]Do upgrades in small bunches. It is better to upgrade slowly over time. Upgrade one package or a group of related packages, reboot, and see if your system still works.
[*]Never use sudo apt-get upgrade. In the event of trouble, installing dozens of upgrades at a time makes it very hard to isolate what package breaks your system. 
[*]Have a concrete idea about what you gain by doing an update. If you have no idea what good the upgrade does, or why you need it, don't do it. If it ain't broke, don't fix it :)
[/list]

---

### Post by forestwalkerjoe on 2009-02-27
before i do all that.. let me explain a bit. this is ubuntu 810 .. 
I am on an older lap top.. and 
the issue i have had.. started with the Update manager.. it choses a whole bunch of stuff to update, upgrade on the first install connection. 
once that was through.. as is required.. it had one failure. 
this linux image 27-7. When i boot up.. grub shows the version 7 and the version 11.. and i use 11 to get into the system. 
what this seems to be doing is requiring and Upgrade of that version 27-7 to version 27-14 generic. 
when you look at the Update manager.. it has tabs and notes on the packages that it wants to install.. this one.. has this note in it. 

description:
 ```
This package contains the Linux kernel image for version 2.6.27 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 
```
it's changes says this:
 ```
Version 2.6.27-7.16: 

  [ Tim Gardner ]

  * ndiswrapper remote buffer overflows on long ESSIDs (CVE 2008-4395)
    - LP: #275860

  [ Upstream Kernel Changes ]

  * ext[234]: Avoid printk floods in the face of directory corruption
    (CVE-2008-3528)


Version 2.6.27-7.15: 

  [ Upstream Kernel Changes ]

  * tcp: Restore ordering of TCP options for the sake of inter-operability
    - LP: #264019




```
the last time i looked it was versino 27-7 to 27-14.. now it says to 27-16.
when you try it .. it fails.. the part i posted earlier.. was my attempt at ITS suggestion.. to not install directly.. so i opened a terminal and tried it there.. but didnt chose YES.. i wanted to see what was going on.. it wants to UPGRADE.. but there is a Failure comment.. when i use the UPGRADE MANAGER.. and i am worried about a failure if i use the Terminal without knowing what i am doing. 
I just spent 2 days working with my system to get it back the last time i messed this up. So i am good at finding all the stuff i want to put back on the new install.. but I'd rather not.. because this is the 4th time i have had to reinstall a WUBI on this lap and i have had to do that 3 times on the Desktop.. which is due for another one .. because we can't solve its AUDIO save settings issue. 
here is the fail comment in Update Manager.. ie the icon that pops up near the Volume icon. 
 ```
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version
```
and this code if i can get the terminal to let me copy
arrg.. no it will not let me copy paste the Update managers terminal.. i can highlight.. but not copy paste. basically its saying it cant back up the boot record before starting install. 
Fails to recover.. 
Here is the link [IMG]http://i152.photobucket.com/albums/s196/forestwalkerjoe/linuximagefail.png[/IMG]to a screen capture i made of the fail code. 
what i need to know is what is this comment above that says " you maynot want to install this "DIRECTLY" use linux image meta package.. so that all dependencies are installed? 
i am going to assume that this is the problem. 

version 27-7 and 27-11.. are there.. its trying to install 14 and or 16. what i need to know is :" which one is the right one.. and why wont it install? grub says.. 27-7 and 27-11 are there.. I am hoping i didnt just mess it up by attempting the install again.. and i'll reboot to see if i have a drive left. 
hopefully you will respond.. or some one will know what to do.. soon. 
FWJ

---

### Post by unutbu on 2009-02-27
Regarding the message, "You likely do not want to install this package directly. Instead, install the linux-generic meta-package":

This is not a problem, just a helpful suggestion. A meta-package is an empty package which lists other packages as dependencies. When you install a meta-package, the package manager (apt-get, or Synaptic for example) will pull in all the required dependencies for you. 
This is more elegant than specifying you want linux-image-generic version 2.6.27.7.14 or whatever because asking for linux-generic will always install the latest kernel without you specifying the version.

Although this is nice, there is no harm in specifying the version yourself.

So this is not the source of the problem.

Regarding the error message: "unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version": By googling "unable to make backup link", I found

[http://www.mail-archive.com/debian-user@lists.debian.org/msg517434.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg517434.html)

which suggests running the command
```

lsattr /boot/vmlinuz-2.6.27-7-generic
```

You should get
```

------------------- /boot/vmlinuz-2.6.27-7-generic
```

If you get something funky (instead of all dashes) then it means this file's attributes are messed up, and most likely you have some filesystem corruption. That is surprising since your install is fresh.

But before I jump to conclusions, how about try the command

lsattr /boot/vmlinuz-2.6.27-7-generic

and report back with the output.

---

### Post by forestwalkerjoe on 2009-02-27
> **unutbu said:**
> Regarding the message, "You likely do not want to install this package directly. Instead, install the linux-generic meta-package":

This is not a problem, just a helpful suggestion. A meta-package is an empty package which lists other packages as dependencies. When you install a meta-package, the package manager (apt-get, or Synaptic for example) will pull in all the required dependencies for you. 
This is more elegant than specifying you want linux-image-generic version 2.6.27.7.14 or whatever because asking for linux-generic will always install the latest kernel without you specifying the version.

Although this is nice, there is no harm in specifying the version yourself.

So this is not the source of the problem.

Regarding the error message: "unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version": By googling "unable to make backup link", I found

[http://www.mail-archive.com/debian-user@lists.debian.org/msg517434.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg517434.html)

which suggests running the command
```

lsattr /boot/vmlinuz-2.6.27-7-generic
```

You should get
```

------------------- /boot/vmlinuz-2.6.27-7-generic
```

If you get something funky (instead of all dashes) then it means this file's attributes are messed up, and most likely you have some filesystem corruption. That is surprising since your install is fresh.

But before I jump to conclusions, how about try the command

lsattr /boot/vmlinuz-2.6.27-7-generic

and report back with the output.

 ```
rj@ubuntu:~$ lsattr /boot/vmlinuz-2.6.27-7-generic
lsattr: Inappropriate ioctl for device While reading flags on /boot/vmlinuz-2.6.27-7-generic
rj@ubuntu:~$ sudo lsattr /boot/vmlinuz-2.6.27-7-generic
[sudo] password for rj: 
lsattr: Inappropriate ioctl for device While reading flags on /boot/vmlinuz-2.6.27-7-generic
rj@ubuntu:~$ lsattr /boot/vmlinux-2.6.27-7-generic
lsattr: No such file or directory while trying to stat /boot/vmlinux-2.6.27-7-generic
rj@ubuntu:~$ sudo lsattr /boot/vmlinux-2.6.27-7-generic
lsattr: No such file or directory while trying to stat /boot/vmlinux-2.6.27-7-generic
rj@ubuntu:~$ 

```
Is what i got..  i was at first thinking it needed a SU to get there.. then i thought.. maybe its misspelled.. vmlinuz verses vmlinux.. none of the above works. however.. i am not getting an ODD line.. as much as a cant do that here line. 
this problem.. i would think.. cant be a defiled file.. i just finished the install last night, and the problem showed.. immediately after the reinstall of the wubi. I did the reinstall.. and then as i connected.. Update manager required updates.. a lot.. as it always does on the first run connected to the net. this was the ONLY one that would not install/upgrade. 
what ever this is.. when i did a auto remove.. and once a complete apt-get uninstall type thing.. it corrupted everything. i JUST NOW got all the flaws.. but this one cleared.. and if i can get THIS solved.. the poor old 10 year old lappy will be a success. 
you sure that code is made for Ubuntu 810? 
FWJ

---

### Post by unutbu on 2009-02-27
I've located a launchpad bugs report which discusses your exact problem:
[https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)

The easiest solution described on that page is to convert your FAT32 (also referred to as VFAT) filesystem to NTFS.

If you are using Windows XP, this is allegedly how one converts VFAT to NTFS:
[https://bugs.launchpad.net/wubi/+bug/252900/comments/9](https://bugs.launchpad.net/wubi/+bug/252900/comments/9)

Another solution would be to download the Ubuntu Alternate Installer CD, use it to repartition your hard drive and install Ubuntu into a partition of its own. The Alternate CD sometimes works with older hardware when the regular LiveCD does not.

---

### Post by forestwalkerjoe on 2009-02-27
since my laptop is a full reinstall.. i reinstalled the WIN os as well as putting in the Wubi.. I am actually not having a problem with doing a convert system into NTFS. 
BUT.. i need to make sure the procedure for changing is the same for windows 2k as it is for XP. the laptop is WIN 2k. 
then i can do the convert no trouble. 
There is very little on the Win2k yet.. as i was focusing on the WUBI reinstall. 
this is a very small drive.. 30 gig.. so i wanted to put more stuff on the Ubuntu side than on the Windows side. There is still a small desire to have the win2k for a couple of programs that will not run easily in Ubuntu. 
If i were to uninstall the wubi again.. and install to a full drive partition.. i might have the same troubles i had on my very first install.. which was HOME file could not be seen.. would not mount and a few other interesting problems which are now solved in the wubi. 
WIll converting the WINDOWS system corrupt the wubi too? I am really NOT looking forward to one more reinstall on the laptop. 

FWJ

---

### Post by unutbu on 2009-02-27
I know woefully little about Windows, but according to the launchpad page: [https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)
WubiNeophyte writes:> 
I've done as you suggested, and have converted Windows to NTFS, then reinstalled Wubi. Things seem to be working well now.
So it looks like you might need to be prepared to reinstall Wubi. :icon_frown:

This page confirms the covert command works for Win 2K:
[http://www.easeus.com/resource/convert-fat32-to-ntfs.htm](http://www.easeus.com/resource/convert-fat32-to-ntfs.htm)

I'm not sure about the "/NoSecurity" option though...

---

### Post by forestwalkerjoe on 2009-02-28
i was doing some reading on one of the links you put in.. and it sounds like there is a way to NOT have to reinstall the wubi.. but that its instable and unlikely to work out that way. I have not the first idea how to convert just a part of the drive to NTFS and move and remove the WUBI boot stuff.. i also have not the first idea how to start a convert of the win system to NTFS from FAT. 
I know there is a choice when you first do a install or back to OEM install.. which is what i have.. but as to where to tell it.. make this NTFS? no idea. it still looks like.. its a whip it and reinstall the whole lap top from scratch.. type deal. I AM Very much not looking forward to that. 
For now.. the lappy is working.. my next full day off is in a week.. i think i will .. possibly.. hold off till that day.. so i can dedicate to it. 
Unless there is some Easy way to convert a Part of the WIN system to NTFS.. or such so i can keep my wubi intact in the process. 
let me know what you can glean.. cause it sounds plausible.. but it requires a little bit of KNOW how.. that I DON'T KNOW HOW.. 
ONCE started.. i can take that from there.. i am not useless.. just hasn't had this one yet.. I WILL SAY.. thank you for finding all that.. it helps me feel better.. that i DIDN'T some how screw it up.. its a  known type glitch. 

FWJ

---

### Post by pytheas22 on 2009-03-01
I've never converted FAT to NTFS, but according to [Microsoft's instructions]("http://support.microsoft.com/kb/307881"), it doesn't seem that hard.  It looks like you would basically just boot to Windows, open a terminal and type:
```

convert c: /fs:ntfs
```

and it would schedule the conversion for the next reboot of the computer.

You could also follow any of the other conversion instructions that unutbu mentions.

Whatever you do, make sure you backup important files from Windows first, just in case.

---

### Post by forestwalkerjoe on 2009-03-06
well, Today is the day. 
I did the MSDOS prompt code and the conversion went very well. 20 minutes. 
At first I thought that Ubuntu was spared too.. but there is , I think, some corruption to the MBR or grub thing. IT went looking for the Fat file and couldn't resolve the issue. So.. i am now in process of reinstalling WUBI. I have backed up and can restore with a bit of time and downloads. 
After the wubi has installed and the first downloads are complete , I will know if the issue from above has then been resolved. 
FWJ

---

### Post by forestwalkerjoe on 2009-03-06
ok now in the NTFS system.. has attempted to install a wubi several times. 
it initiates the virtual disk thing.. and while its making preparations for files and so forth to be transfered, some thing kills the process. 
it just hangs there. Doesn't complete its installation from within the Windows 2k system. so i have Grub but nothing Under the grub. 
What is killing my install? 

FWJ

---

### Post by forestwalkerjoe on 2009-03-06
ok sorry for the drama. 
i went into the win2k process task manager found wubi.exe and set it to highest priority. It must have just dropped the CD movement and stopped coping. once it was set at high.. it finished the wubi install. 
Going onto the first things.. and then Update manager thing. 
FWJ

---

### Post by forestwalkerjoe on 2009-03-07
ok , no dice. 
once i had the NE2K.cis in.. and there was net connection.. we had a problem. the Update manager downloaded every thing.. but when it comes to installing every thing.. it freezes. no mouse , no tabs.. nothing. it did give a need to manual dpkg configure --a but when i tried that.. it also freezes. 
what the heck is going on here? i cant get this thing to just DO the update.. and be done with it. 
this is almost worse than having an update not installing.. now that i am in the NTFS.. is there some thing some one forgot to tell me? some setting in WIN2K that i was supposed to SET UP.. so that it could finish its install? 
please some one.. help me out here. 
FWJ

---

### Post by unutbu on 2009-03-07
I've been reading your posts and rooting for you... really was hoping the conversion to NTFS would solve all the problems. I don't have any idea why you are encountering so many obstacles. I'll continue to think about this, but at this point, I don't have any good suggestions for you. :/

---

### Post by forestwalkerjoe on 2009-03-07
it took me many tries.. i got the install up.. and i had some really BIG issues with the first Upgrades.. after anohter whole day.. i was able to get it stable.. I THOUGHT.. 
i started doing ADD's of things i wanted in the system. every thing seems stable. 
then one of the downloads.. just a study program.. froze. 
i had to finaly hold the button down and restart. 
what i came back with is disturbing. 
There IS NO GRUB. 
it gives the duel booted choice. Ubuntu or Windows.. but if you choose Ubuntu. it gives you a list like this. 
 ```
FIND /ubuntu/disks/boot/grub/menu.lst
Find /ubuntu/install/boot/grub/menu.lst
Find /menu.lst
Find /boot/grub/menu.lst
Find /grub/menu.lst
Commandline
reboot
Halt. 
```
Trying any of the above requires i KNOW what i am doing.. and in this case.. again.. i dont. 

OK.. what just happened.. which seems to be my mantra lately. 
Some how in that FREEZE.. the GRUB was deleted, or washed out.. or edited? i have nearly finished all the stuff i wanted for my lap top.. and then NO GRUB. Can some one show me how to get that back please? 

FWJ

---

### Post by pytheas22 on 2009-03-07
> it gives you a list like this.
Code:

FIND /ubuntu/disks/boot/grub/menu.lst
Find /ubuntu/install/boot/grub/menu.lst
Find /menu.lst
Find /boot/grub/menu.lst
Find /grub/menu.lst
Commandline
reboot
Halt.



I've never seen that before, but I assume it's pretty bad.  You could try playing with those options to see if any one will boot your system.  Beyond that, your only option may be to reinstall Ubuntu via wubi.  I know that's not convenient, and I have no idea why an update would have destroyed grub, but it's the only path I can think of.

You should also keep in mind that erratic behavior like this (grub disappearing and random system freezes) could be symptomatic of your hard disk failing, or some other hardware problem.  If I recall correctly, you were having similarly inexplicable problems about a month ago on this same machine (involving it booting to a black screen sometimes, or something like that), right?  You might have some hardware tests that you could run in BIOS (make sure for instance that SMART is enabled for the hard disk).

Finally, you may have better luck if you install Ubuntu to a dedicated partition, rather than using wubi.  The installer on the live CD will allow you to shrink your Windows partition in order to make room for an Ubuntu one.  It should go smoothly, but make sure you defragment the disk in Windows first.

---

### Post by forestwalkerjoe on 2009-03-08
ok.. well... i played a little game to see if i could fix this.
I was thinking.. i did edit a file once , this install.. that was not grub menu list.. and i wondered if i had some how messed some thing up that might have caused this. BUT.. what i think happend is that the newer linux image installed.. Failed in it's install and removed the version 7 from the list.. and had nothing to really put back. so it cruded my grub. 
What if i had put the menu.lst back? 
i used LIVE CD.. and could browse my hard drive.. i found ubuntu.. and even found my menu.lst. which was empty. 
I copied a menu list from my desk top wubi.. and made a page and transfered that via a flash drive to my LIVE CD laptop. 
I copy pasted.. when i rebooted.. there was a menu list.. but the errors are.. it can not find the actual linux image. none of them. So i think this is a matter of losing the image in the UPDATE and nothing to put it back. 
So i was taking your suggestion to remove Ubuntu wubi. which .. in CD within windows.. it WONT do. 
it doesnt see it, so it doesnt remove it.. it just tries to install again.. and says i dont have enough space to do a full install. it has some how orphaned the WUBI i have. its there.. but it cant be seen. SO it takes up the space and i can not figure out how to get that space back. 
its almost to the point that i would have to whipe the intire laptop clean to try again. UNLESS , some one has a bright idea to help me either.. reinstall the linux image.. or to fully UNINSTALL this very much failed wubi. 
any ideas? OH and the file i edited.. was the one related  to savage 3d. there was that 2 part comment i could put into the X11/xorg.conf that would get rid of the black screen issues. that does work btw. 
I just spent a whole day.. a day off from work to get this all back up and running and now i can not even remove it and start over. 
FWJ

---

### Post by pytheas22 on 2009-03-08
The Ubuntu live CD can't erase wubi because wubi is built into the NTFS partition.  If you want to erase wubi, boot to Windows, go to Add/Remove programs and there will be an option for uninstalling wubi.  After you've done that, boot to the live CD and you should have free space for installing Ubuntu.

---

### Post by forestwalkerjoe on 2009-03-09
> **pytheas22 said:**
> 

You should also keep in mind that erratic behavior like this (grub disappearing and random system freezes) could be symptomatic of your hard disk failing, or some other hardware problem.  If I recall correctly, you were having similarly inexplicable problems about a month ago on this same machine (involving it booting to a black screen sometimes, or something like that), right?  You might have some hardware tests that you could run in BIOS (make sure for instance that SMART is enabled for the hard disk). **_My hardware for the black screen issue was savage s3 card and we found a glitch and a solve for that. it was a common problem with this video driver and this version of Ubuntu.i had to add a fix to the etc/X11/xorg.conf to fix it. what seems to be true also is the freezes on the initial installs were related to me forgeting to allow the hard drive to stay ON.. it has a default shut down time for IDL of 5 minutes.i reset that to never in windows and the install went well.what i do have now is issues with it freezing on install of UPDATES in Ubuntu. it checks for SWAPFILE SWAP and checks securityFS every reboot.. it takes 5 to 10  minutes to do this. Then it allows the full boot.is this that Security thing you or ubuntu was telling me about?_** 

Finally, you may have better luck if you install Ubuntu to a dedicated partition, rather than using wubi.  The installer on the live CD will allow you to shrink your Windows partition in order to make room for an Ubuntu one.  It should go smoothly, but make sure you defragment the disk in Windows first.
as to doing a repart of my drive and fully installing onto dedicated part.. i have only just.. last night finished solving all the trouble i could with this wubi install. i had to format and reinstall the whole drive..  windows 2k is now in NTFS again..and working and so forth.. i spent hours trying to get it all back.. now.. it does freeze with most updates or apt-gets installs or ADD REMOVES after a few minutes. there has to be some place that tells either the hard drive to shut down? or some thing in the shell that is now not working right.. 
FWJ

---

### Post by pytheas22 on 2009-03-09
Where do you set your hard drive to turn on and off?  Is it in BIOS or someplace else?  I know Windows has some options to make the drive spin down if it's idle for a certain length of time, but spinning down should not cause the system to freeze; moreover, the drive shouldn't be spinning down when you're installing updates, because it shouldn't be idle at that point.

The only other place that would explain why the system freezes while installing updates is the log.  Take a look at syslog in System>Administration>System Log and see if there's anything relevant being recorded at the time of the crashes.

Also, when the system crashes, what happens if you press control-alt-backspace?  Do the capslock and numlock lights on your keyboard still light up if you press those keys?

Also, does the computer still crash if you apply updates manually by typing:

```
sudo apt-get update
sudo apt-get upgrade
```

rather than using the graphical utility?

---

### Post by forestwalkerjoe on 2009-03-09
what i was saying about drive shutting down. 
I reset the idl drive issue in windows 2k. I was having trouble with the wubi install freezing up. since this installed Inside the windows system.. i would assume their rules apply. 
I have nothing in my bios set up that tells me i can change that idl setting but i did find a power managment thing in windows that did. 
going back to THIS install of ubuntu. 
when i turn the lappy on.. and chose the ubuntu.. it starts up its echos of what its loading etc.. it gets to a place where its mounting files and says.. file check.. then 
mounting swapfile .. SWAP.. this has no visual.. it just says that and then.. seems to stop a long time. after 5 to 10 minutes it says mounting securityFS   .. OK. and goes on. 
there has to be something related to security in win2k that is doing this.. it has never done this before. 
once INSIDE the install.. 
i have done some apt-get ing.. and had no real trouble.. but ADD REMOVE has frozen and Update manager has frozen. 
it also says i have 2 things to remove if i check it.. its the linux version 7 image again. the last time i removed the linux 7 image.. i ended up with that strange grub load. 
or actually.. no grub really at all. 
So i am leaving that alone. 
when the freeze happends.. every thing is frozen.. it doesnt respond to control alt delete or escape.. i have never done control alt backspace before.. i was taught you could do a Right Control-SysRq then type REISUB and solve some problems.. but the config on this lap doesnt seem to support that. 
I am becoming convinced that there is some thing IN the windows 2k that is interfering with the wubi in a NTFS system. 
i have been searching for something that answers these questions. 

FWJ

---

### Post by pytheas22 on 2009-03-09
Nothing stands out to me as an explanation for those problems--I don't understand why apt-get works alright on the command line, but its graphical frontends freeze (do other applications freeze, or only Add/Remove and Synaptic?).  But I do think you'd have better luck if you installed Ubuntu onto its own dedicated partition, rather than using wubi.

---

### Post by forestwalkerjoe on 2009-03-10
i am not sure if this is realy related or not. 
BUT i had some time so i chose to update the Win2k system . it was using IE 5 and few other things.. and i figured.. one way or the other i need to secure it. it didnt have Java  or much of anything on the system installed. 
After the install, i still have this delay when chosing to boot into Ubuntu that says Mounting file systems, mounting FILESWAP... swap.. then it takes 5 minutes , showing nothing.. and then it loads securityfs and goes on with out trouble. 
BUT the issues with freezing on GUI downloads has some how stopped. 
I do know that the apt get showed me .. linux image 7 and Generic 7 are still there.. and linux image 11 is also there.. it is loading into 11 on boot up.. it tells me i should use auto remove to fix this. i did that last time and lost my install. 
So i guess i'll just have to deal with that. 
I am wondering if [this link](".tuxradar.com/content/how-fix-most-common-linux-problems") i found will help me on boot up. 
The stalling on boot..  adding noapic thing. i have not the first idea what that does or why that might help or how to install that command line. 
I was also able to find a [boot loader script]("http://ubuntuforums.org/showthread.php?p=6562877") program that allows me to read some of the info on boot up.. i have info on my desktop now. 
i was hoping some one would know if there is a line in here i can audit that will stop the incessant checking of securityfs or at least shorten the time it does it. 
FWJ

---

### Post by pytheas22 on 2009-03-10
Applying updates to Windows is not going to affect Ubuntu.  They're completely different systems, even though Ubuntu exists within the Windows partition.  So I don't know why you're no longer having issues with updates, but at least you're not.

Unfortunately I don't know how to make Ubuntu stop checking securityfs at boot, and I don't know why it's doing it in the first place.  The only explanations I can think of are that you're booting with an option that tells it to do that (not likely), or the file system is constantly being corrupted, so Ubuntu keeps checking it at each boot (plausible).  Could you post the contents of your /boot/grub/menu.lst file and the boot information that you have on your desktop?

---

### Post by forestwalkerjoe on 2009-03-12
ok.. just to sure.. this IS a windows 2k system. 
This log is also very long.. 
it doesnt have all the info i would have liked.. but it does show some things. 

here is the results of the output:

------------------------------------------------------------------

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedd3edd3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,589,054    58,588,992   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2CC4B4EAC4B4B802" TYPE="ntfs" 
/dev/loop0: UUID="d4f8e150-9c6c-4284-a460-e7f8b002101a" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rj)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2CC4B4EAC4B4B802 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2CC4B4EAC4B4B802 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2CC4B4EAC4B4B802 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2CC4B4EAC4B4B802 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2CC4B4EAC4B4B802 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

c:\wubildr.mbr="Ubuntu"


=================== sda1: Location of files loaded by Grub: ===================


   1.6GB: ubuntu/disks/boot/grub/menu.lst
   1.6GB: ubuntu/disks/boot/initrd.img-2.6.27-11-generic
   1.5GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
    .7GB: ubuntu/disks/boot/vmlinuz-2.6.27-11-generic
   1.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

---

### Post by pytheas22 on 2009-03-13
hmmm, unfortunately nothing stands out to me in the boot information you posted (I also don't have much experience with these kinds of things, however) as a problem.  The only other thing I can think to do is press control-alt-F1 immediately after your system starts booting next time.  This should give you a line-by-line feed of what it's doing as it boots, rather than merely showing you the Ubuntu logo.  Does it mention any errors?  Does it complain about any point about the file system being unclean?  This is the last place I can think to look...

---

### Post by forestwalkerjoe on 2009-03-13
I think your first assessment is more correct. The hard drive is failing. 
A friend of mine.. didn't show me HOW to do it.. but did tell me.. My hard drive for this Viao is CABBED in a hidden partition.. the disk i have is a restore disk which needs those cabs. So when i reinstalled and repartitioned.. it isn't a full format. What i would need to do to solve the issue is what he calls a Soft format.. and before that , a back up of all the files that are IN that hidden partition.. so that i can do a full reinstall.. after the soft format. The soft format will fix the damaged areas.. allow me to set those aside so they will not cause issues easily in the future. this lap top is 10 years old.. the bios is very old and no frills. Some of the newer bios will allow you to back up the HPartition and soft format right from the bios.. but not this one. So for now.. i guess the securityFS slow thing.. is the system trying to fix and check it self. After doing a fix files entry in the Generic 11 Grub.. it fixed.. and found dozens of IOS that were bad.. sectors that are no longer useful. SO this explains a lot. I think , if i have time to let MAT work on it.. i could save this lappy.. but the hard fact is.. time to save up for another laptop. 
For now.. the worst of it is a very slow boot to UBUNUTU. the windows side boots fine. 
I am going to direct my newer challenges to fixing the desktop issue.. which is a simple reinstall  of the wubi.. and then.. to the families PC issue.. which i never did get to do. at least not yet. 

thanks for the hard work and patience. 

FWJ

---

### Post by forestwalkerjoe on 2009-03-13
Additional note:
Just so you know.. i had a lot of little issues with my Desktop install.. as opposed to the recently failing laptop install. I had put most of my focus in the past few weeks on the laptop because i wanted to get it up , running and exampling for backup support for a friends of the families Desktop. 
After i left the above message i got a wind and decided to do a reinstall of the WUBI on My desktop.. it had issues with Pulse audio not saving settings and a few browser oddities.. nothing critical but i wanted them fixed. 
I have now just finished half a days work on it.. and the install is perfect. All the DVD codex , pulse audio settings.. wigets,Office software,compiz , Games and such are all back where they belong and all working.. and i finally got to download install the Thunderbird Mail client too. since i also have Thunderbird on the Windows.. I'll have to go look round for a way to migrate the mail there or copy it.. into this wubi of ubuntu. 
So.. now that lappy is on the shelf for a while.. and Desktop is now , as far as i can see.. fixed.. soon.. we'll hope I'll get to working on that families Desktop. 
thanks for the help and all the patience. 

FWJ

---

### Post by pytheas22 on 2009-03-13
I'm glad the desktop is working.  You might want to consider using something like [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to make a backup so that you could reinstall it later with all the custom settings if necessary.

As for the laptop, sorry to hear that the drive is failing, but that makes a lot of sense.  You might be able to buy a new hard disk, if you can find one for a model that old.  I would also say that you could boot it to a USB stick, but I doubt a machine that old has the option to boot to USB.

---

### Post by forestwalkerjoe on 2009-03-14
I take it you have used.. do use this remastersys thing? 
I got questions. As this is a fully new wubi install.. will it properly back up the wubi? So if i had to do another un install for what ever reason.. i could go through the wubi install then pop in this disk and replace all my settings? will it put back things like DVD codex's and other apt get items? ABI word, browser settings? compiz settings? or what Does this back up exactly? 
if i were to make a dist disk.. where i have the install set up just SO.. do i use IT for installing ubuntu? or do i do the ubuntu install.. and then ADD this to set up certain things? 
I will have to assume that it will not matter if i am using a full install.. a partition install or a wubi install to put these settings in? 
Anyway.. going on.. 
ever heard of KEEPASS? i downloaded it so i can save back up all my passwords. but i can not figure out for the the life of me HOW IT WORKS. do you have any ideas on a great Save all.. password minder? i tend to forget some of these passwords and constantly having to ask for reminders sent in Email to get them back. 

thanks Again. 
FWJ

---

### Post by pytheas22 on 2009-03-14
remastersys allows you to make a backup copy of your system in the form of an ISO file that you can either burn to CD/DVD in order to create a custom live CD, or use to make a bootable USB drive that also provides a live environment.  Then you would simply boot to the live CD/DVD/USB and use the built-in installer to recreate your custom system.  It's intended for doing real installations of Ubuntu in a dedicated partition, but you could probably use the ISO file with wubi in order to create a custom wubi system.  You just need to have the ISO file in the same directory as wubi.exe when you launch it, I believe.

I've never used keepass, but Ubuntu comes with a built-in password manager at Applications>Accessories>Passwords and Encryption Keys.

---

### Post by forestwalkerjoe on 2009-03-15
i followed that suggestion you made.. but this key manager..  i have not the first idea how to use it. I was just looking for some thing to manage my Firefox passwords.. so if i ever had to format.. i could use just one KEY to open them all up again.. not have to go looking for each and every one of them. some thing exterior to the OS itself. 
Some thing safe.. net based and secure. then i would only have to memorize maybe one password.. and all others would be kept in the KEY manager program.. what ever that maybe. 
FWJ

---

### Post by pytheas22 on 2009-03-16
Unfortunately I don't know of any other keyring managers than the one built into Ubuntu.  But if you google around, I suspect you'll find something.  Maybe a Firefox extension or something along those lines...

---

