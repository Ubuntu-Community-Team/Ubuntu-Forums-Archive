---
title: "Laptop starts in wrong resolution"
date: 2009-07-22
forum: Hardware
---

### Post by Bizzako on 2009-07-22
Hello all,

I recently purchased a Dell Studio 1555 laptop and immediately formatted the Windows partition and installed Ubuntu 9.04.  There were a few minor issues, all but one of which I have been able to fix.  When I start the computer the resolution sets itself to 1024 by 768 instead of the correct resolution (1366 by 768 ).  I am able to correct the resolution in Display Preferences, which is fairly easy, but it is annoying to do so after every other reboot.  (This seems to imply that it isn't a driver problem, but a default settings problem) Is there a way to force the X server to start at a specific resolution, or does anyone else have a solution?

Thanks,
Daniel

---

### Post by prshah on 2009-07-22
> **Bizzako said:**
> Is there a way to force the X server to start at a specific resolution, 

Jaunty did not correctly detect the native resolution of my laptop screen. I set it manually by adding the required lines (in red) to /etc/X11/xorg.conf> ```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[color=red]        DefaultDepth    24
        SubSection      "Display"
                Modes   "1280x768@60"
        EndSubSection[/color]
EndSection

```

In your case, you will probably need one of these (in order of preference)```

                Modes   "1366x768"
#or
                Modes   "1366x768@60"
```

You will have to know the native resolution / refresh rate of your laptop screen; don't blindly add these lines.

Also, please check if Ubuntu treats it as 1360 instead of 1366; If 1366 does not give you a proper screen (coloured garbage) try 1360.

---

### Post by Bizzako on 2009-07-22
Worked like a charm.

Thanks,
Daniel

---

### Post by edwardLS on 2009-07-29
Dell Studio 1555 running Ubuntu 9.04.  Having the same problem, so I applied the suggested fixes.  Those fixes work approximately half the time.  That is, some times Ubuntu starts in the proper resolution, and then other times it starts with the incorrect resolution leaving a dark strip at each side of the display.
The video card is shown as Mobile 4 Series Chipset Integrated Graphics Controller by Intel.

Has anyone determine a solution to make this work consistently?

---

### Post by jamesreilly on 2009-07-29
I have a similar problem with my desktop, and when trying to edit xorg.conf i get "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." I'm a bit of a newbie, what am I doing wrong?

---

### Post by edwardLS on 2009-07-29
In order to save changes made to xorg.conf, you must edit the file as superuser.  
I edit with " sudo gedit xorg.conf"

---

### Post by prshah on 2009-07-30
> **edwardLS said:**
> 
Has anyone determine a solution to make this work consistently?

This solution should be consistent; if it is not, then something is being ignored in your xorg.conf.

To give a more specific solution, can you post your /var/log/Xorg.0.log file, both with the correct resolution as well as without the correct resolution?

Or, you can just post the diff(erences) by using the terminal (Applications-Accessories-Terminal). To do this, boot your laptop. Whatever resolution you get (assume correct), make a copy of the log file```
cp /var/log/Xorg.0.log ~/correct.log && sudo rm /var/log/Xorg.0.log
``` Then reboot until you get the unwanted resolution (delete the log file _before_ each reboot / X restart), and make a copy of that log```
cp /var/log/Xorg.0.log ~/wrong.log
``` then, post back the output of the differences between the two; you can get this with the command```
diff correct.log wrong.log
```

btw: When using sudo for a GUI application (X application) use gksudo / kdesudo instead of sudo.

---

### Post by edwardLS on 2009-07-31
Thanks for the advice.  Sorry for the delay in coming back; however, my situation has changed.  I was a bit concerned about loading Ubuntu on this "new-to-me" studio 1555.  So, I reloaded the Ubuntu 9.04 i386 Desktop.  
Upon my first logon I still have the incorrect resolution, and I had approximately 2 inch wide black area on either side of the screen.  
I then went to System -> Preferences -> Display and selected 1366 x 768(16:9) and "Applied" that.  The screen has been working perfectly since then.  A check of my /etc/X11/xorg.conf shows the following: (partial)  I did not add the Subsection; I wouldn't pretend to know enough to do that.  But, it is working.

```
Section "Screen"
      Identifier       "Default Screen"
      Monitor          "Configured Monitor"
      Device           "Configured Video Device"
      Subsection  "Display"
            Virtual  1366 768
      EndSubSection
EndSection
```

---

