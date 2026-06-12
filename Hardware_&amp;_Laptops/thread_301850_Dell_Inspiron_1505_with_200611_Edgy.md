---
title: "Dell Inspiron 1505 with 2006/11 Edgy"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by jalexstark on 2006-11-17
Summary of installation so far on Dell Inspiron 1505.

The main upgrade from the base system was 802.11n Netgear/Broadcom internal wireless.

I'm not on the laptop now, but the installation was with the desktop CD Edgy 2006/11/14 (ish).

The notes are not meant to be complete, just pointers with specific terms like "blacklist pcspkr" that you can search for.

Immediate problems:
[LIST=1][*]Muting on this machine is quite spectacularly bad.  Don't think about tweaking the install in a library as I did, or be prepared to be ashamed of the random noises.  Pressing the mute button just makes a loud beep.
[*]Widescreen didn't work out of the box.  I recommend disabling screen expansion in the BIOS since it is less distorted, and the black border tells you what mode you are in.
[*]Wireless didn't work out of the box.
[/LIST]

Possible solutions:
[LIST=1][*]A threefold solution is required.  Blacklist pcspkr to silence the terminal beep.  Go to Administration->Login Window and to the accessibility tab to silence the noise on GDM startup.  Go to Preferences->Sound to mute sound once logged in.
[*]Widescreen requires the 915resolution package.  Try just installing it in Synaptic.  A lot of the instructions on internet help pages are no longer required.  This had 945G Intel.
[*]Download the wireless driver from Dell (netgear/broadcom).  I used unzip and then unshield to extract the bcmwl5 sys and inf files.  Confirm these match those in c:/windows/drivers/ or whatever.  Try using whatever ndiswrapper is installed already, since less is likely required than on internet help pages.  If wireless doesn't seem to work, it may be doing better than you think.  Mine was jammed and unable to find any access points.  Fiddling might have made matters worse.  Use iwconfig and avoid the networking GUI, since they fail for the usual reasons.  (GUIs have to interact with the hardware in a more predefined manner.)  ifconfig and iwconfig showed the hardware (MAC) address reliably. I was at a point where iwconfig was not setting the ESSID to a string when asked, but something like "key off" released the problem and everything became nicely automatic.
[/LIST]
Note: We were having problems with wireless under WinXP media.  It was being stupid about a "changed driver" even though the driver matches.  Ideas?

BUGS revealed:
[LIST]
[*]Users admin GUI is buggy and misdesigned wrt specifying the group for a user.  While the user number can be specified, the user's dedicated group cannot.  The obvious workaround is to create a group and select it.  This, however, then breaks the GUI, because you cannot readily go back to automatic group creation for subsequent user creations.  Further, users created with dedicated groups created separately do not appear in the list of users.  BTW: Why specify the user and group numbers?  So the user numbers match those used previously and hence used when writing files to HDD, CDROM, etc.  This is an important function.
[*]Personal recommendation: when installing make sure that you setup whatever account you want to be uid=1000, gid=1000.  If you don't care, then set up a dummy account.  Having ids other than 1000 is handy for future installations.
[*]Xorg i810 server breaks slightly wrt switching between terminal (Ctl-Alt-F1) and windowing (Clt-Alt-F7).  Reproduction: login, and change resolution from 1280x800 to 1024x768.  Then switch to a text terminal and then switch back.  The screen is corrupted, and 1024x768 has disappeared as a resolution option, even though the current screen is 1024x768.  Temp fix: rotate screen left to force the server to change screen configuration.
[*]Network tools: The first tab is basically ifconfig output, but it couldn't even display the network hardware address correctly.
[/LIST]

/Alex

---

### Post by depace on 2007-05-22
Hello 

I'm not sure if i'm in the right place to post this problem. 

I recently bought a dell inspiron 1505 and tried with ubuntu 7.04... 

ubuntu didn't install driver for my display and wifi... 

intel 945 chipset

Intel(R) Media Accelerator 950 Graphics

Thank you...

---

