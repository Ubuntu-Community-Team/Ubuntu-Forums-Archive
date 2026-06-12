---
title: "Laptop/External Monitor - Resolution not detected."
date: 2008-11-10
forum: Hardware
---

### Post by mikeyfbi on 2008-11-10
Hey guys,

I just installed a fresh 8.10, and in my last install (gutsy) I had my external monitor displaying at 1280x1024 while the laptop screen mirrored it (but only displayed a portion at the same resolution I believe).


Right now Pref -> Screen Resolution only detects the laptop screen (shows "Laptop 15" on both screens when i detect) and only gives me the option for 1024x768

How can I get the 'Screen Resolution' to detect my monitor, and allow it to display at the correct resolution?
(I'm using an intel card, if that helps)

Thanks in advance!

Ps.
I believe I manually added it to the xorg.conf, but I don't remember how.:(

---

### Post by mikeyfbi on 2008-11-11
bump

---

### Post by davidgeeee on 2008-11-11
Mickey  This may be a fix for you...

 Re: Where is "Screens & Graphics" in 8.10
Just in case this helps someone that found this thread, here is how I fixed my screen resolution with 8.04.

First my graphics adapter and monitor were not detected. Tried all kinds of edits to xorf.conf with no success.

The Fix for me was this:

I used a 7.04 live CD to boot into Ubuntu (not install). The resolution was set to the highest my monitor could handle. Detected my graphics card correctly. Checked in "Screen Resolution" utility and all the resolutions were there. So, I copied xorg.conf to a USB drive. Restarted 8.04 and made a backup of the current(faulty) xorg.conf file. Then I copied the sections of xorg.conf (from 7.04) that were about the graphic card and monitor and modes to the xorg.conf of the 8.04 installation. Restarted X and everything was peachy!

I may try this with 8.10 today, but I am pretty sure it will work there too.

Hope this helps someone that has been banging their head like me!

---

### Post by mikeyfbi on 2008-11-12
That you for suggesting that.

I tried this with a live 7.10 DVD and it changed the resolution on the login screen, but didn't change anything for my desktop after log in:( :(

Why oh why would it work 100% on a live boot of a previous version, but not on the new version!!:confused::(

mike

---

### Post by Sisyphus48 on 2008-11-12
[B]I just had a problem with my resolution not going high enough and the solution below fix it for me.
[/B]
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

But don't worry, you KNOW they are there!
Just type in your log-in name, hit enter and type your password, hit enter and wait for the log-in to complete. Your xwindow (Gnome or others) should be at the desired resolution now.

---

### Post by davidgeeee on 2008-12-10
[QUOTE=coolethan]i stumbled across your thread on screens and graphics in 8.1 and i was wondering if you were able to succesfully do this on 8.1 and where do i find the xorg.conf file on the disc?[/QUOTE]
The xorg.conf file is on that get written during the LiveCD setup of version 7.10 of Ubuntu.  I'll try to list the step from memory:
1. Download and burn a copy of Ubuntu 7.10
2. Boot with that CD and do not install just use the Livecd to get to the desktop.
3. At that point check that you can get to all the screen resolutions that you expect.
4. If so, copy /etc/X11/xorg.conf to a USB drive.
5. Then go to your installation  of 8.10 and copy and/or replace then portions of xorg.conf from the USB drive into the one installed by 8.10

If this works for you, post the text above as a reply to the message in the forum.  This thing frustrated me for along time and now I have used the technique on four machines and they all came out perfect.

---

### Post by linux_tech on 2008-12-10
In terminal try
```
xrandr -s 1280x1024 
``` or whatever resolution
I havn't tried it on a laptop with external monitor attached 
so I am not sure on the results.  Typing in just xrandr will give you the available resolutions.  

The external monitor can be enabled and the laptops LCD disabled manually by using these commands:
 ```
  xrandr –output VGA-0 –auto
    xrandr –output LVDS –off
``` 
more on xrandr 

  ```
xrandr --help
``` 
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

