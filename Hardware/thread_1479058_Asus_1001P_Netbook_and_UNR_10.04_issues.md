---
title: "Asus 1001P Netbook and UNR 10.04 issues"
date: 2010-05-10
forum: Hardware
---

### Post by Mathieup75 on 2010-05-10
Hi, I have a netbook (Asus 1001P) and I used UNR 9.10 and 10.04 and I have the same following issues:

1) Wireless did not work until I used ndiswrapper and installed Windows XP drivers.
2) Found scripts to enable 2 finger scrolling, but none of them worked.
3) Integrated microphone does not work.
4) Brightness controls jumps to non-sequential steps when using brightness buttons.

There's one new thing with UNR 10.04 that I did not have with 9.10.  With 9.10, when messing with the brightness controls, I could achieve full brightness of the screen.  Now, with 10.04, I can only get it to 85% (estimated) by messing with the same controls.

Any help for items 2 to 4 would be appreciated.  I searched the forums and only found correct answers for issue #1.

Thank you

---

### Post by Mathieup75 on 2010-05-10
...I have been searching and found another thread that talked about brightness on UNR 9.10. Used it and solved my brightness issues in UNR 10.04.  Control buttons no longer works, but screen is now 100% bright.

--------------------------------------------------------------------------------
On Karmic press Alt-F2 and enter: gksudo gedit /etc/default/grub
then change the line with GRUB_CMDLINE_LINUX_DEFAULT to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
save the file and run in terminal: sudo update-grub

boot and enjoy!

Does not improve the Power Manager Brightness Applet :sad:

btw: it seems to me the 1001P and the 1005PE share identical hardware.
--------------------------------------------------------------------------------

Thank you noiv!

---

### Post by Mathieup75 on 2010-05-10
FYI, I had a different procedure to enable wireless on UNR 10.04 than the multiple threads talking about UNR 9.04-9.10.

1) Blacklisted generic wireless drivers:
(Or just edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx,  blacklist b43, blacklist b43legacy and blacklist ssb  to the end of the file.) Note:  This only effects what is loaded at startup, so you will have to reboot  to have the bcm43xx drivers disabled. If you have an atheros based  card, remember to blacklist not only ath_pci, but also ath_hal, since  ndiswrapper won't work if ath_hal is still loaded.

2) Installed ndiswrapper using "Ubuntu Software Center"

3) Downloaded "Wlan_NE785H_GE112H-V7_7_0_377_XP.zip" from the Asus website, and extracted the content.

4) Ran ndiswrapper and added netathw.inf driver.  Got an error message, ignored it!

5) Rebooted, and it worked!

---

### Post by Mathieup75 on 2010-05-10
Now for the microphone...

First of all it was muted in the sound controls :(, tested with sound recorder and it worked fine.  However, it did not work with Skype.

Found a thread by ironring1, used the following to have microphone work with Skype.

-----------------------------------------------------------------
sudo apt-get install pavucontrol, unlocked stereo channels on  input, dropped right channel to 0%, now I can see the mic response in  pavucontrol, confidence is high!
          -Skype now works!  
-----------------------------------------------------------------

---

### Post by Mathieup75 on 2010-05-21
Got this from Sudaniel....


-----------------------------------------------------------------------------
 				 				**About 2 finges Scrolling** 			
 			 			 		   		 		 		Dear Mathieup75,

I have an ASUS 1001p.

About the 2 fingers scrolling. 
You can save the following scripts as a file and source the script  file  after X-windows.

# Beginning of Script
#!/bin/sh
#
#  Synaptics TouchPad 2 finger Scrolling
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger  Pressure" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger  Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8  1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger  Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge  Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the  touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor  Threshold" 32 110

# End of Script


sudaniel
-----------------------------------------------------------------------------

I will try it and report back.

---

### Post by johntkucz on 2011-02-13
Hi there,
I am having this same problem.  I want to get wireless working on my 1001p asus netbook, running ubuntu 10.  I am having some snags with a couple of the downloads, as suggested from the myriad forum threads I've scoured to find this information.

Wondered if someone could help with these.

I could not find the driver with this procedural step:

```
3) Go to http://support.asus.com/download/download.aspx and get the WinXP wireless LAN drivers for the 1001P (NE785H_GE112H). Unzip that file to a folder.
```


```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

returned could not find package ndiswrapper

Basically most the download procedures I haven't been able to get to work.  Highly frustrating.  Appreciate help with that.  Thansk.

I downloaded ndiswrapper via Uubuntu Software Center in Admin system prefs, but am having trouble downloading hte asus driver. Why couldn't someone just post the direct URL to the .zip? cheers.

---

### Post by johntkucz on 2011-02-13
I got it to work!! Victory!! Yippee!!

Downloaded ndiswrapper (what is that, btw?) via ubuntu software center.  Why didn't apt-get install work?  (I did sudo).  

Anyways, works awesome.  Thanks to the bits and pieces pieces together from this thread and others.  Cheers.  Exciting.  Great receptivity, too!

Anyone know how and where ubuntu passwords are stored?  Like the ubuntu equivalent of mac osx keychain.app?? Thanks!  these forums are really helpful but have discovered that usually I can never follow directly the sequential steps but have to jigsaw-piece together whatever works from the smorgasbord of tips and procedures that worked for some people.  I guess this is because of the dynamic nature of open source updates, normal driver updates, OS changes (does apt-get install commands work anymore?  I liked those back when I tweaked around with Fiesty Fawn), and slight variations in hardware (although I think most all people commenting on this thread had the same 1001p hardware).  Anyways, thanks.  Will check back to these forums if want to adjust or update any other drivers/features/hardware/software.

One side project is getting Garmin Mapsource to work in ubunut?  Will that work with WINE?  Thanks.

---

