---
title: "Is Ubuntu for Samsung Q1 Ultra &amp; Sony Viao UX380N ok..?"
date: 2010-04-28
forum: Hardware
---

### Post by liviococcia on 2010-04-28
Hello Members
I've been using Ubuntu 9.10 for a few weeks now on my Dell Inspiron 1720 and Fujitsu Amilo laptops, and i can say they're the fastest that they've ever been, I use a T-Mobile mobile broadband dongle on an 'Unlimited' tariff with both, and where the connection was slow, and a bit hit & miss under Windows XP or Vista, it's not with Ubuntu, also the general pace and running of both laptops is astounding.

Ubuntu has changed alot since i last gave it a go, it's much more user friendly for the newbie layman, and all the applications run well and do everything i need.

Now I'd like to give my other two computers mentioned in this thread's title a go, both have touch screens and generally both are not fast, the Sony particular, so while doing my searches through other threads posted, did notice users had problems trying to get around the issues of the touch-screen input device.

That's why I'm asking if anyone with the two same devices, or any members found a way around the problems, or knows if they've been ironed out in the up-and-coming 10.04 version.

Any feedback, or help from members would be grateful

Kind regards
Livio

---

### Post by Cka3o4nik on 2010-06-05
Hello!

You can have Ubuntu 10.04 set up for Samsung Q1 Ultra 
But touchscreen won't work by default. Follow the [http://ubuntuforums.org/showpost.php?p=9406477&postcount=9](http://ubuntuforums.org/showpost.php?p=9406477&postcount=9) instructions. Keyboard also have some minor issues.

As for the Vaio - sorry, I don't know.

---

### Post by liviococcia on 2010-06-07
A big thanks Cka3o4nik for your reply and help, I must apologise for this delayed posting it was a massive help from yourself, and the link you provided, I managed to sort out the touch-screen for the Samsung Q1 Ultra, I mainly followed the instructions from the link, and some of the way below:- 

1: I first installed 'xserver-xorg-input-evtouch' package  by going to the main Ubuntu desktop menu, clicking onto 'System' then onto 'synaptic package manager, in the search box type EVTOUCH, this should bring up the package, then mark it for installation, and install.

2: I then opened the 'File manager' in administrator mode by using the 'Run Applications' box, to do this hold the 'Alt' button and while held down press the 'F2' button, in the box that appears type    ' gksudo nautilus '   file manager will open, click onto 'File system' and follow the folder path below:

/usr/lib/X11/xorg,conf.d

3:Open any file with it's name ending in '.conf' contained in the 'xorg.conf.d' folder, and without making any changes to the contents of the file you have opened, go to 'File' then 'Save as..', a window will now open, in the 'name' box rename the file to   11-touchkit.conf   then click onto the '+' sign next to 'Browse for other folders' and navigate again by clicking first onto 'File System' then 'usr' > 'lib' > 'X11' > 'xorg,conf.d', you will see this folders contents, making sure you have followed all the above click the 'Save' button.

4: While the 'File Manager' window remains open in 'administrator' mode (if not follow step 2 of these instructions to reopen), double click onto your newly created '11-touchkit.conf' file, be aware that the contents of this new file now need to be changed, in the Gedit app that has open the file, click onto 'Edit' then 'Select All' of which the contents should now be highlighted, then click onto 'Edit' then 'Delete', the file's contents should now be gone, copy and paste the instructions below into the blank page of file:-

Section "InputClass"
Identifier "Touchkit Touch"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event*"
Driver "evtouch"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emultate3Timeout" "50"
Option "SendCoreEvents" "On"
Option "TapTimer" "200"
Option "LongTouchTimer" "400"
Option "MinX" "145"
Option "MinY" "193"
Option "MaxX" "3973"
Option "MaxY" "3898"
EndSection

5: Click onto 'File' then 'Save', and now close your new document, if the 'File Manager' window is still open you should notice your new '11-touchkit.conf' file in the 'xorg.conf.d' folder

6: Close the 'File Manager' window, (I notice whenever i open 'File Manager' using the gksudo nautilus instruction and then finish with it, it seems to make my desktop go blank, and I have to shut the Q1 Ultra down by holding the off/on switch in the 'off' position, it doesn't seem to do any permanent harm though) 

Also... if you were using the Samsung USB integrated keyboard & mouse, or any USB dual keyboard and mouse while following the above instructions, make sure you unplug this before turning the Q1 Ultra back on, in my case I've found that I couldn't have the keyboard plugged in, as the touch-screen would not work correctly, once the Q1 Ultra was started up without it, the touch-screen worked no problems, following this does seem to be the only way it will work.

When you do restart with no USB integrated mouse & keyboard, remember to follow 'step 1' below to first open the 'Onboard' screen keyboard' so allowing you to login, if it doesn't first show, verify you've chosen to turn it on and just restart the Q1 again.


I got the 'onboard' assistive technologies touch keyboard to pop-up at Ubuntu's start-up for loging in, to do this:-

1:At the initial login screen i clicked onto the man in a circle icon, then preferences, and in the box that appears, put a check mark next to the item regarding the use of the Onboard screen keyboard.

I also now have it load apon the desktop opening,to do this:-

2: Go to the main Ubuntu Netbook Edition 10.04 menu bar, click on 'System' then 'Assistive Technologies', a window will open put a check against 'Enable Assistive Technologies' click onto the 'Prefered Applications'button , click onto the 'Mobility'section drop-down arrow, and choose 'Onboard' and put a check against 'Run at Start' and close.

There's also settings in the 'Onboard' screen keyboard when you click in the puple area within the keyboard to the bottom right, doing this will show a 'Settings' button, this will allow you to have the 'Onboard' screen keyboard start when the desktop loads up minimised to the application bar, or as a small floating icon on the desktop.

Also within the 'Onboard' keyboard settings section, there is an option to have it always appear when a password window activates i.e when the screen saver locks the desktop, or it's logged off. I would suggest this related item has a check mark against it. 

Just a note, if there's a graphical way to screen calibrate the Q1 Ultra under Ubuntu Netbook Edition 10.04, i'd be grateful for the information on how to go about doing this, and also how i can get the front Webcam to work, at the moment only the rear one works using the program 'Cheese'.

Also. i've had some success with installing Ubuntu Netbook Edition 10.04 on my Sony Viao UX390N, the installation had no real problems, i managed to find out how to get the frount Webcam working, and also found information on rectifying the bug with the sensitivity of the thumb pad, please find the link below:-
[http://www.micropctalk.com/forums/showthread.php?p=53207#post53207](http://www.micropctalk.com/forums/showthread.php?p=53207#post53207)


Thanks again to everyone, 

Kind regards
Livio

---

### Post by border on 2010-06-10
I see you found my directions already, but I've created a new thread for the samsung q1 ultra
[http://ubuntuforums.org/showthread.php?p=9439415](http://ubuntuforums.org/showthread.php?p=9439415)

---

