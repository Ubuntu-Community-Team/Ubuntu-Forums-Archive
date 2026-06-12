---
title: "screen resolution"
date: 2008-11-13
forum: General Help
---

### Post by sean09 on 2008-11-13
So, I'm very new to Linux (8.04.1) , just got it last night.

Screen resolution is 800x600, very annoying considering I have a 1024x768 monitor. I do the obvious thing by going to System -> Preferences->Screen resolution, but it is not there.

Any way I can get it to 1024x768?

---

### Post by Vunutus on 2008-11-13
Sounds like you need to update your video driver. Try checking the official driver site for your card, some of them offer Linux drivers (nVidia does atleast, I imagine others do too).

---

### Post by sean09 on 2008-11-13
I run the update, and it says "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I select both codings from the menu and neither work.

Any help?

---

### Post by ITAndrew on 2008-11-13
What video card are you using? The reason that I ask is that some drivers are not open source and are proprietary restricted drivers I.e.. Nvidia's.
Go to System->Administration->Hardware Drivers and enable any proprietary drivers.


What you also may want to do to update is open a terminal and run:

sudo apt-get update && sudo apt-get upgrade

This will update and upgrade the packages that are installed on your system

---

### Post by Sisyphus48 on 2008-11-14
I had a similar problem and I followed this suggestion posted by Kellemora and it fixed me right up.

Screen Resolution Problems? Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
This document is to address Changing Screen Resolution using Preferences causes Screen to Roll horizontally, vertically or just mess up royally. Also, only 640 x 480 resolution available in Preferences. This fix may or may not allow you to select other available resolutions from the Preferences Option without changing MODE lines in /etc/X11/xorg.conf which I am not addressing here.
If this fix causes log-in screen obesity (HUGE SCREEN), see my other post titled Huge Log-in Screen? Easy fix! Which addresses that problem separately and easily.

To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open. From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items). Place a check mark in the box to the left of Screens and Graphics, this will automatically select 'Other' if it was NOT in your drop down list under Applications. Close this window.
You will have to REBOOT for the change to take affect.

Once you're up and running again, left click on Applications/Other/Screens and Graphics.
A log-in screen will appear, type your Normal log-in password. Why it don't ask for Root I don't know.

In the Screens and Graphics Preferences window select Graphics Card first just to check to make sure your correct graphics card is displayed. Normally these entries are correct, but check them anyhow!

OK, now select the Screen Tab and get things set up to run properly.

Click on the little Monitor icon to the right of Model: It may currently say Plug n Play. A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor. The screen on the right will change to the models that manufacturer makes. Scroll through the list to find your Monitors model name and number and/or identification.
If you have an .inf driver for your particular monitor and it is not listed, select add and follow the directions there. I've not found a monitor not already in the listing yet. Then I never have many new things either, that might not be listed long before I get it, hi hi......... IF a Test button comes up, just IGNORE IT, because your screen will mess up royally. After selecting your monitor, select OK! This will bring you back to the Screen and Graphics Preferences screen.
Here you will select the desired resolution you would like your DESKTOP to run in. The proper bandwidth should self-select, but check to make sure it's right for your monitor. A wrong setting could damage your monitor!
Select OK and it will change and ask you if you want to Keep this setting. If all looks OK, select YES.
This change, and all the default parameters for your selected monitor WILL be written to the /etc/X11/xorg.conf file. Also, the Screens and Graphics window may show UNKNOWN for your monitor. The result of this Unknown Monitor or sometimes even if the Monitor is KNOWN and displays correctly the resultant change to the xorg.conf file, may cause your log-in screen to become OBESE (HUGE) and you might not be able to see your log-in boxes.

---

