---
title: "GUI Will not load when installing Ubuntu Studio on a Compaq Presario Desktop"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by Matrix7 on 2009-03-24
Greetings,

After listening to the "Going Linux" podcast for a week or so I am ready to start running a dual boot system on my main home PC (I also have a home theater PC w/ my DVD backups on it, but it is Windows XP SP2 (for now)).  My system is a Compaq Presario SR 1033WM [(Click for product specs)]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=pe&dlc=es&product=415186") and has been upgraded to 2GB of RAM and I had to install a nVidia GeForce 6200 OC 256MB PCI Express card (BFG Tech).  I got it from my parents when they upgraded to another system and got it back in good working order.  Long story short I do a lot of multimedia projects (graphics, 3D rendering, and such) and am very interested in "Ubuntu Studio".  Looks like it has everything I would want so I tried to install it from a live DVD I burned (said the ISO was too big for a CD).  Install went through a rather ugly looking set of screens (think pre Windows 95 type graphics) and got a blank 40GB hard drive I had laying around partitioned to run Ubuntu Studio (I am installing on a second drive instead of another partition) and installed all the packages I wanted through their menu.  It told me to take out CD as usual and reboot.  Dual boot loader came up fine and I selected Ubuntu.  It went through a black screen with a LOT of white text saying it was basically loading the guts of Linux.  

Next screen that comes up is still the black background but asks for my username and password which I enter.  Next it appears I am logged in but no GUI, only the terminal style screen.  I have a feeling that it is something to do with my hardware, but I am not entirely convinced that it is the video card because my first course of action was to go into the BIOS, disable the PCI card and use the onboard video.  Same result :-(  Any ideas?  Is there some terminal command I could run once I log in to load the appropriate drivers or to run a compatability test on my system?

I should also mention that I had tried to run about three different Live CDs of various Linux Distros (Ubuntu, Suse Live, GIS Linux) and none of them would load properly as a Live CD and SuseLinux would not even let me begin a setup - it got part of the way through install and seemed to freeze.  Help would be appreciated.  I will reboot again in a few and write down any error messages I see to help ascertain the problem.

Thanks much,
::[Matrix7]::
[http://matrix7.deviantart.com](http://matrix7.deviantart.com)

---

### Post by irv on 2009-03-24
Try typing startx and see what it does.

---

### Post by Matrix7 on 2009-03-24
Okay tried that and it said the command was not found and it gave me a sudo command I could run to load it.  I ran the command (I believe it had something to do with xinit) and even after it downloaded and installed I would try to run it and no dice.  Did I get a borked up install here?  I will try to post exact error codes first thing tomorrow (The computer that I am trying to load it on is the one we use a lot so I can't keep rebooting it to write stuff down unfortunately).  Thanks much for the help, I will Google any error codes I get and report back tomorrow.  Thanks!

---

### Post by Matrix7 on 2009-03-25
Okay have some more info now.  One of the first errors I got was "APCI: Unable to load the System Description Tables" when trying to load Ubuntu Studio as well as run any of the Live CD's I have tried so far (just tried the latest Kubuntu, which I REALLY would love to install but no dice).  With Kubuntu I get the screen where I select English, then select the option to try Kubuntu without making any changes to my system.  The load screen comes up, the bar goes back and forth for a few minutes then it gets to approximately 10% (just guessing by bar position - no percentage shows) and freezes.  

I used Google's Linux site ([http://www.google.com/linux](http://www.google.com/linux)) to search for that particular error messages and found a few articles that seemed to suggest that it may be a kernel issue, but no solutions unfortunately.  I noticed at the menu where I could select what I wanted to do with the Live CD (Load with no changes, Install, check memory, etc) under Modes (F4) they had a graphics safe mode that I tried and didn't work.  Also under Other Options (F6) they had an APCI=Off (I believe, it is the second option down) and tried that one as well with no luck.

Hope this is detailed enough guys.  Not sure how to do a screen dump of the errors I am getting from the terminal or I would do that.  Thanks for the help and please let me know if this issue needs moved to another section of the forums.

Thanks

::[Matrix7]::
[http://matrix7.deviantart.com](http://matrix7.deviantart.com)

---

### Post by Matrix7 on 2009-03-31
Okay solution found.  Normally I wouldn't bump this but I have seen this question around a few times and wanted to post what i did:

1) Linux apparently has problems with my PCI Express nVidia GeForce 6200 OC video card.  I had to go into the BIOS and set the video to Onboard - totally disabling my vid card and running from the motherboard alone.  After that I reformatted my drive and did a full install of Ubuntu Studio, being very careful at each screen to follow the directions thoroughly.  At one of the last screens there was an option on what packages I wanted to install (Video, Audio, etc) - make SURE that the option to install the Desktop (may be called GUI) is Checked (I believe it has a * next to it and says necessary).  After that is done reboot and it should work.  

Even once I got linux working I tried to update my video card drivers and switch back and no go.  This Compaq is the only one I have had a problem installing Linux on so far so for now I will survive with onboard memory.  Hopefully someday I can figure out how to do the PCI as well.

---

