---
title: "Acer TravelMate 8104"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by SpookyET on 2006-06-02
After it takes a rather long time booting the LiveCD, the screen goes blank and freezes.  I suspected that it failed to detect some hardware, so I rebooted and selected graphics safe mode.  It did the same thing, but instead of going blank, I got X Server configuration errors.  I think it fails to detect the ATI Mobile graphics card.

---

### Post by heffo_j on 2006-06-03
Seen this thread; it might help [http://www.ubuntuforums.org/showthread.php?t=186219](http://www.ubuntuforums.org/showthread.php?t=186219)

Regards
John

---

### Post by SpookyET on 2006-06-04
> **heffo_j]Seen this thread said:**
> http://www.ubuntuforums.org/showthread.php?t=186219[/url]

Regards
John


Thank you.

---

### Post by Ben Alex on 2006-07-07
I had the same problem on my Acer TravelMate 8104. The solution is:

1. Boot the live CD with the default options, and allow the screen to go blank.

2. CTRL ALT F1 to a different console.

3. sudo vim /etc/X11/xorg.conf
   Find the Device section. Add a new line inside it:
   Option    "MonitorLayout" "LVDS, AUTO"

4. CTRL ALT F7 back to the X11 window.

5. CTRL ALT BACKSPACE to shutdown and restart. It will work.

Good luck

Ben

---

### Post by SpookyET on 2006-07-07
Have you had problems with other hardware, like wireless?

Thank you.

---

### Post by Bob Murphy on 2006-07-19
Boy, this tip worked like a champ on my Acer Travelmate 8104. It had the stock Windows config from Acer (C and D drives), and I'd tried to set it up for dual boot about a month ago using the desktop CD, and hit a brick wall with the black screen. I used the alternate install CD today, and applied this tip, and voila! The only tricky bit was that although I told the installer to zap the D partition and install there, it didn't do so, and gave me a 2 GB partition instead. So I had to go into Windows to delete the partition, then re-installed, and all was fine.

---

### Post by SpookyET on 2006-07-19
The normal CD gives you access to GParted, and you can mess with the partitions however you want.

---

### Post by reka on 2006-07-20
> **Ben Alex said:**
> I had the same problem on my Acer TravelMate 8104. The solution is:

1. Boot the live CD with the default options, and allow the screen to go blank.

2. CTRL ALT F1 to a different console.

3. sudo vim /etc/X11/xorg.conf
   Find the Device section. Add a new line inside it:
   Option    "MonitorLayout" "LVDS, AUTO"

4. CTRL ALT F7 back to the X11 window.

5. CTRL ALT BACKSPACE to shutdown and restart. It will work.

Good luck

Ben


Thank you so much for this explanation, this display-"error" had me ripping my hair off ;)

../reka

---

### Post by SpookyET on 2006-07-22
Yes, that worked.  Thank you very much.

Things that I noticed.
It drains battery.  On Ubuntu, at 100%, it says 1 hour 40 minutes remaining.   On Windows, I get 3 hours and 40 minutes.
WiFI led is not working.
Media keys are not working.
Touchpad scroll buttons is behaving weird.  It does right click instead of scroll down.  Up, left, and right do not work.

---

### Post by Anaki on 2006-08-03
I was able to get the wifi led working properly with this modification (found in the forum):
add the file 'ipw2200' in '/etc/modprobe.d/'
with the line:
options ipw2200 led=1


reboot and the led is working properly

---

### Post by SpookyET on 2006-08-03
Thank you.

---

### Post by SpookyET on 2006-09-23
It still won't run.  I decided to actually install it today.  It installs fine, but it won't boot.  It boots a little; then it says that critical temperature of 101 degrees has been reached and shuts down.  I can put it in the refrigerator, and it still says the same thing.

---

### Post by SpookyET on 2006-09-23
I found out about the acpi=off flag, which is bad since Linux won't shut down the laptop when it actually overheats.  It boots with the flag off, but it gets stuck at the login window.  It freezes, sound goes into infinite loop.

As much as I hate Windows, I have to go back to it.  I just don't have the time to mess with it.  It either it works or it doesn't, and it looks like it doesn't.  Thus far, I have not had any luck with any linux distro outside of VMWARE.  Linux is not ready for the desktop, at least not the installers.

---

### Post by Bob Murphy on 2006-09-30
Has anyone had any luck getting the 8104's wifi to work with WPA under Dapper Drake? And doing it so it's easy to switch to other wifi networks, including WEP and open?

I started doing the things in the wifi and WPA how-to's, but it appears network-manager doesn't natively support the 8104's wifi hardware (Intel PRO/Wireless 2915ABG).

It looks like a lot of approaches might work, including installing extra software, alternative network managers, updating the ipw2200 driver and rebuilding the kernel, etc. - but this would all be experimental and might be blind alleys.

So before marching off into this uncharted territory, I wanted to see if someone else has been there and is willing to share a map.

---

### Post by Jim Link on 2006-11-22
I am curious if the anyone has tried to get the pcmcia or smart card reader to work...

---

### Post by danielfm123 on 2006-11-24
battery least only 1:40 on windows it least a least 3:00
the fan is always on and cpu temperature never less than 49º
i tried everithing

list of what i did
configure ati powerplay with aticonfig (using fglrx)
configure acpi tables with the DDST
configure cpu thrtling for powersaving
turned of wifi and bluetoot (buttons working)

oyher probles is that gnome batery level shows only wrong data i have to use acpi -t

now im using windows xp.... i really miss my loved amarok and gnome please help

i just cant find help on web about his
i need mi long live battery

---

### Post by danielfm123 on 2006-12-05
seems like no fix....
i got so angry that now all my computers has windows full of games and double clicks and folders
linux is not enaught for the home user

---

### Post by hfdragon on 2007-04-02
> **SpookyET said:**
> 
Touchpad scroll buttons is behaving weird.  It does right click instead of scroll down.  Up, left, and right do not work.

I just installed Ubuntu on my new 8215 and also had a few problems with the display.. but I also have this weird behavior with the central touchpad button. 

Has anyone managed to make it work fine ?

---

### Post by danielfm123 on 2007-05-04
ad the following to xorg.conf
Section "InputDevice"
   Identifier   "Synaptics Touchpad"
   Driver      "synaptics"
   Option      "SendCoreEvents"   "true"
   Option      "Device"      "/dev/psaux"
   Option      "Protocol"      "auto-dev"
EndSection

and and it to the layour
mine looks like this

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        InputDevice   "Synaptics Touchpad"
EndSection

you see synaptics on last line

any one knos how to make battery least more?

---

### Post by Bob Murphy on 2007-06-08
Anyone had any luck getting the DVI connector to work with this under Edgy Eft?

I'd like to use an external monitor with the 8104 and Ubuntu, but no luck. I've attached a Samsung SyncMaster 930B via DVI and rebooted, but only the laptop screen is active.

If I attach the same monitor via VGA, it's active. But I want to reserve the VGA connector for a Windows box. Also, Edgy didn't auto-recognize the monitor resolution that way.

Any help would be appreciated.

---

### Post by cyberazi on 2007-11-25
i'm a noob with linux .. so far everything works well with my 8104 but i cant get my wireless to work.... so can anyone help me with a step by step instruction

---

