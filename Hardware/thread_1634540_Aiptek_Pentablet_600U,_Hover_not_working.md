---
title: "Aiptek Pentablet 600U, Hover not working"
date: 2010-11-30
forum: Hardware
---

### Post by jeevo on 2010-11-30
Hi every
I have tried searching the internet for a solution but without any luck. 

Now the tablet does respond to the pen being pressed down, and it works using absolute positions which is great, the only problem i have is that the hover is not working.

The hover used to work when i first plugged in the device, which was about a month ago, but i haven't had time to use it since then and now it's just stopped working, the hover that is.

This is my /usr/lib/X11/xorg.conf.d/70-wizardpen.conf file
> 
Section "InputClass"
   Identifier "WizardPen class"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse"
   MatchVendor "WALTOP|Waltop"
   Driver "wizardpen"
   Option "TPCButton" "off"
   Option "TopZ" "0"

EndSection

Section "InputClass"
   Identifier "WizardPen ignore mouse dev class"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-mouse"
   Driver "mouse"
   MatchVendor "WALTOP|Waltop"
   Option "Ignore" "true"
EndSection


I am running Ubuntu 10.04 but i am using Openbox instead of Gnome (Still using GDM as my Display Manager). Everything is updated to the latest version.

Anyone have any suggestions to what the problem might be and how i can try to fix it?

Also, I'm not actually sure if the driver is loaded, i am assuming it is, since the pen is working, but when i try the command lsmod to see what modules are loaded i do not see anything related to WizardPen or WalTop. But seeing as i am no linux nor ubuntu specialist, i have no idea what that actually means.

Also, the package xserver-xorg-input-wizardpen is installed, i have also followed the guide here: [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648) without any luck.

So any suggestions on how i can get the hover function working again would be most welcomed! =)

---

