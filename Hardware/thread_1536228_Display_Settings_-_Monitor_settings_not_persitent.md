---
title: "Display Settings - Monitor settings not persitent"
date: 2010-07-21
forum: Hardware
---

### Post by lubu-jim on 2010-07-21
I installed Lubuntu 10.04 on pc with WinXp Pro. Install worked great.  it seemed to hang during install but the install screens warned me about that.  It actually runs great.  Really fast.  Much faster than XP pro.  I can access my XP documents and open them in Lubuntu and the performance is great.  Pentium 4 2.0Ghz, 1Gb Ram.

Everything works fine.  However my monitor settings are not persistent.  My display is set at 1024x768 @ 60Hz.  Works great. Not kept.

Installed software is persistent as well as my wireless and ethernet settings.

I downloaded the iso, checked the checksum, tested from USB and live CD then installed from live CD.  I noticed this was also an issue from USB and obviously the CD. 

Does anyone have any suggestions?

Thank you!

---

### Post by cavalier911 on 2010-07-22
The gui tool for xrandr doesn't save the configuration. We'll add xrandr  to the autostart file so it starts at bootup before you login.
We begin by opening lxterminal and test the command you will be entering to make sure it gives the resolution you want.
Reboot so resolution is not what you desire,open lxterminal at the prompt type:```
xrandr -s 1024x768
``` 
_Add entry to autostart:_
```
sudo nano -B /etc/xdg/lxsession/Lubuntu/autostart
```
_Add whats in bold,ctrl+x,y,enter to save._
```
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@gnome-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
**@xrandr -s 1024x768**
```

Reopen nano to verify:up key,enter,verify,ctrl+x to close.

Reboot

If you make an error,restore the backup:
```
sudo cp /etc/xdg/lxsession/Lubuntu/autostart~ /etc/xdg/lxsession/Lubuntu/autostart
```

---

### Post by lubu-jim on 2010-07-22
Cavalier911
Thank you very much.  I tried

xrandr -s 1024x768and the screen went blank and did not recover.  I confirmed that I am using 1024x768 @60hz. It works great.

I did xrandr and got a list of resolutions.  Should I use:
xrandr -s "1024x768_60.0" ?

I'll keep researching.  But If you can help that will be great!

Thanks!

---

### Post by lubu-jim on 2010-07-22
I've done some testing.

I can type as I suggest with the quotes an underscore and the refresh rate and it works to adjust the screen resolution. however it does not work for the resolution I want....and the resolution I am using after selecting with the GUI. The screen goes blank.

After selecting the "1024x768_60.0" with the gui and then attempting to "change" to the same resolution via the command line, the screen does not go blank.  Obviously the screen does not change. But it does not even blink.

Thanks!

---

### Post by cavalier911 on 2010-07-22
Menu/Preferences/Monitor settings

Set lxrandr gui tool to what you want.

Then query xrandr:
```
xrandr -q
```

Look for the * which is the current setting.

> mojo@lubuntu:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   **1024x768**       75.0     70.0     **60.0* **
   896x672        60.0  
   832x624        75.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   840x525        75.0     70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0  


I have mine set 1024x768 refresh 60


I add this to autostart:
```
xrandr -s 1024x768 -r 60
```

---

### Post by lubu-jim on 2010-07-22
Cavalier911:
It worked!  I added the line to autostart and it worked great.  And I'm still quite the newbie. I appreciate your help.

Thanks

---

