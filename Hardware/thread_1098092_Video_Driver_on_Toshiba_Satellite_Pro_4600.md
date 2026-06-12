---
title: "Video Driver on Toshiba Satellite Pro 4600"
date: 2009-03-16
forum: Hardware
---

### Post by -Dee- on 2009-03-16
Hi,

I'm a n00b concearning Linux but I always wanted to give it a go. So last weekend I got an old laptop from a friend and installed Xubuntu (because Ubuntu froze during install).
Anyway, I don't seem to get my resolution settings to 1024x768. It only allows me to get it at 800x600 so I can't use the full screen.

Video card: Trident Cyberblade XP

Can someone help me out on this isue?

Thanks.

D

---

### Post by -Dee- on 2009-03-16
For those that are interested.

The solution:

sudo gedit /ect/X11/xorg.conf

copy and paste the code below for the appropriate sections:

```
Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection 
```

Save, log out and log in again.

---

### Post by vizkoze on 2009-03-19
Thanx a lot, just what I was looking for.
works like a charm.

---

### Post by kostaras on 2009-04-07
Hi!

I have exactly the same problem with my old Toshiba laptop.

My laptop configuration in X-ubuntu 8.10

lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

I followed the above instructions, 
entered "sudo mousepad /ect/X11/xorg.conf" 
entered my password
then entered the above lines of code

But...when attempting to save the file, the system does not allow me to save the code as the warning message appears "Can't open file to write"

What am I doing wrong?

Thanks in advance

---

### Post by kfenton on 2009-04-07
> **kostaras said:**
> Hi!

I have exactly the same problem with my old Toshiba laptop.

My laptop configuration in X-ubuntu 8.10

lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

I followed the above instructions, 
entered "sudo mousepad /ect/X11/xorg.conf" 
entered my password
then entered the above lines of code

But...when attempting to save the file, the system does not allow me to save the code as the warning message appears "Can't open file to write"

What am I doing wrong?

Thanks in advance

it should read sudo mousepad /etc/X11/xorg.conf

just the ect in there should be etc!

---

### Post by kostaras on 2009-04-08
Are you sure about etc instead of ect?

Because all the scripts above refer to "ect"

Anyway, I tried it out and it does not work.

---

### Post by SedaliaSteve on 2009-04-12
Thanks Dee!

That fix was just what I needed. Yesterday I installed Xubuntu 8.10 on my junky old HP Pavilion N5415. It also has a Trident CyberBlade card. I also had the default values in xorg.conf with 800x600 since it hadn't foumd it. I just dropped your values in, logged out and had a full screen. I was really starting to dislike that big black border.

Steve

---

### Post by jhunterj on 2009-05-23
Thanks also; just fixed up my display of a new install of 9.04 on my Toshiba 1405-S151 with the Trident Microsystems CyberBlade XPAi1 VGA controller. Nice the find the answer waiting for me here when I needed it.

---

### Post by RoudoudouFather on 2009-07-04
Thanks a lot for this solution, it works well for me
Dom


> **-Dee- said:**
> For those that are interested.

The solution:

sudo gedit /ect/X11/xorg.conf

copy and paste the code below for the appropriate sections:

```
Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection 
```Save, log out and log in again.

---

### Post by Astounder on 2009-07-05
the correct spelling is etc (as below)
 
sudo gedit /etc/X11/xorg.conf

copy and paste the code below for the appropriate sections:


Code:
Section "Monitor"Identifier "Configured Monitor"Option "DPMS" "true"HorizSync 30.0-60.0VertRefresh 50.0-70.0EndSectionSection "Screen"Identifier "Default Screen"Monitor "Configured Monitor"Device "Configured Video Device"DefaultDepth 24SubSection "Display"Depth 24Modes "1024x768" "800x600"EndSubSectionEndSection
Save, log out and log in again.
 
 
It works 1024x768 in my old Toshiba Portege laptop now
 
Thanks a lot

---

### Post by Cams on 2009-07-08
Did not work for Tiny A440 with Trident Cyberblade i1

---

### Post by bmalbert22 on 2009-07-16
> **kostaras said:**
> Are you sure about etc instead of ect?

Because all the scripts above refer to "ect"

Anyway, I tried it out and it does not work.


You need to edit the permissions of the xorg.conf file.

In a terminal window navigate to /etc/X11 
Then, run chmod -R a+rw xorg.conf

That ought to fix the error that you are getting.

BrannDon

---

### Post by harce on 2009-08-16
xconf formated code

```

      Section "Device"
              Identifier      "Configured Video Device"
      EndSection

      Section "Monitor"
      Identifier "Configured Monitor"
      Option "DPMS" "true"
      HorizSync 30.0-60.0
      VertRefresh 50.0-70.0
      EndSection

      Section "Screen"
              Identifier      "Default Screen"
              Monitor         "Configured Monitor"
              Device          "Configured Video Device"
      DefaultDepth 24

      SubSection "Display"
      Depth 24
      Modes "1024x768" "800x600"
      EndSubSection
      EndSection

      Section "ServerFlags"
              Option  "DontZap"       "False"
      EndSection

```

u have to install dontzap to get it working - it brings back the backspace keyboard shortcut to restart X

---

### Post by einfeldt on 2009-08-24
I was able to use the settings below to successfully expand the available screen resolution to include 1024 x 768, and to expand the used view screen area.  The Toshiba Satellite Pro 4600 that I was using would only offer 800 x 600 screen resolution settings.  harce's fix given below solved that problem.

The other problem that I was having involved a large unused margin of black space around the edges of the view screen.  As much as 25% of the view screen was not being used by Xubuntu Intrepid.  In other words, the effective usable view space on the Toshiba Satellite Pro 4600 was reduced by 25%.  Using harce's recommendations below, I was able to once again make use of the full view space on this old Toshiba from 1998.  

Due to harce's recommendations, the public school for which I volunteer is now going to have a working notebook for a student to use during classtime.  Microsoft Windows 98 had long ceased to be useful on this machine, but now Xubuntu is working just fine.  Many thanks to harce for his / her recommendations. 

Christian Einfeldt 

> **harce said:**
> xconf formated code

```

      Section "Device"
              Identifier      "Configured Video Device"
      EndSection

      Section "Monitor"
      Identifier "Configured Monitor"
      Option "DPMS" "true"
      HorizSync 30.0-60.0
      VertRefresh 50.0-70.0
      EndSection

      Section "Screen"
              Identifier      "Default Screen"
              Monitor         "Configured Monitor"
              Device          "Configured Video Device"
      DefaultDepth 24

      SubSection "Display"
      Depth 24
      Modes "1024x768" "800x600"
      EndSubSection
      EndSection

      Section "ServerFlags"
              Option  "DontZap"       "False"
      EndSection

```

u have to install dontzap to get it working - it brings back the backspace keyboard shortcut to restart X

---

### Post by buddhaPIMP on 2009-09-23
I'm having the same problem with my 4600 only willing to display 800x600, i am pretty new to Linux and i have done the above recommendations and after a restart a full 1024x768 screen appeared which was great BUT after giving my username and pword it reverts back to 800x600....

---

### Post by buddhaPIMP on 2009-09-23
Just got it working thanks for the help guys, after doing the suggestions posted it was still not working but went to display and the 1024x768 option was there as it was not before. Works great now. Thx again.

---

### Post by euphro on 2010-06-30
This solution worked for me on my SP4600 (8.04.4 LTS) on the second attempt - I didn't spot the "endsubsection" at the end of "screen", which resulted in a gobbledygook display on hard reboot. Recovery mode from GRUB worked well, however and I was able to restore X to its former 800x600 state before starting again.

---

### Post by woody1 on 2011-03-05
Thanks for doing all the work, my old Toshiba Portege 7100 is now useful again with a full screen display,

Many thanks to all,
                   Colin

---

