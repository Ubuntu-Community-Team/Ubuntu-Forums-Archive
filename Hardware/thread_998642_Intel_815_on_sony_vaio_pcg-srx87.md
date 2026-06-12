---
title: "Intel 815 on sony vaio pcg-srx87"
date: 2008-12-01
forum: Hardware
---

### Post by mark_anon on 2008-12-01
Short story:  my laptop is stuck at 800x600 resolution, with no way out.

I have tried:

the change screen resolution option in system preferences... no options besides 800x600 and 640x480.

Looking for restricted drivers.  The restricted drivers menu doesn't list any options for my computer, even though Synaptic says that I have the proper Intel driver installed.

Editing the xorg.conf file to force the intel i815 driver.  Then the vesa driver.  then trying to add resolutions for the monitor.

reconfiguring xorg.

xfix from recovery mode.

Installing Ubuntu 8.04  (Gos 3)

and a bunch of other stuff... this is really driving me crazy.  I don't want to use Windows, but it's the only thing that works on this laptop.

Grrrrr!!!!!

Does anyone have any ideas?  I don't need any fancy effects, or anything.... I just want a functional computer.

Thanks in advance.

-Mark

---

### Post by blackened on 2008-12-01
First some info:
Type this in the terminal and post the output wrapped in code tags.
```
xrandr --prop
```

---

### Post by Jamhart88 on 2009-01-03
I had a problem with my laptop (Sony viao pcg-fx105K) stuck in a 800x600 res - it has an intel 815 chip in it too (with ubuntu 8.10). I remember having problems with ubuntu in the past with this laptop too.

I resolved the problem by installing zen linux, finding the xorg config that that used, and modified it for ubuntu. This is the xorg.conf that I now have that gives me 1024x768 res on my laptop:

[FONT="Courier New"]Section "Device"
        Identifier      "Configured Video Device"
        Option "RenderAccel" "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31.5 - 50.0
        VertRefresh 40-90
             Option "UseEdidFreqs" "1"
        Option "ReducedBlanking"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
   DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes  "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes  "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes  "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection

EndSection[/FONT]

I dont know why Ubuntu can never get the res correct, when other distros (like zen) can get it right without fiddling with xorg.conf's.

Hope this helps you out.

---

### Post by mark_anon on 2009-01-11
Here are the results of xrandr --prop:


Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0

---

### Post by mark_anon on 2009-01-11
PRAISE THE JEEBUS!!!!!

Thank you for posting the xorg.conf from your Zen distro.... it worked flawlessly.  Seriously, I can't thank you enough.  800x600 is a sad, sad world that I am happy to be leaving behind.

Also, I agree on the Ubuntu auto setup of the xorg.conf file... it seems to be totally messed up a pretty high percentage of the time.  And I don't really understand why so many other distros would be so much more successful.  Odd.  Anyway, it works now, and I am happy. 

Thanks!

-Mark

---

### Post by blackened on 2009-01-11
Glad you got it working.

I don't personally agree with the way they've implemented the whole auto-configuration of display properties. One of the main reasons many of us use linux in the first place is to avoid the untold layers of abstraction and obfuscation that other OSes (ahem Windows, and to a lesser extent Mac) use, thus robbing us of the ability to make granular changes. Whether I need to make changes such as these doesn't matter, it's the fact that if I want to, then I **should be able to**. It's always been my understanding that that is one of our basic tenets.

---

### Post by rapper97 on 2009-06-07
**[SIZE="7"]HALLELUJAH[/SIZE]**

<chrous plays>


What, you can't give thanx for posts no more it looks like? Well, you have my eternal gratitude, sir... and drive home the point that, YES! there is life/Linux beyond Ubuntu!

Thanks again!

---

### Post by mark_anon on 2009-06-07
I agree.  Three cheers for the response by Jamhart88.  You really saved me time, and preserved my sanity.  Thanks again.

---

### Post by jdictionary on 2009-06-08
Worked for me too, thanks.  I'm actually using Fedora 10 but had the exact same problem.  Much appreciated. :-)

---

### Post by yunone on 2009-09-24
fixed my sony issue! thanks!

---

### Post by zenthanian on 2010-02-12
this fix worked on a sony pcg-fx170k... 

it should be noted that /etc/X11/xorg.conf didn't exist.  There was a /etc/X11/xorg.conf.failsafe.  I created a xorg.conf and pasted the contents above and it worked like a charm.

Thanks.

---

### Post by blackened on 2010-02-12
xorg.conf has been deprecated entirely in recent releases. It will still be recognized if you create the file yourself though.

---

### Post by quickwitt on 2010-04-13
This also worked on a PCG-FX340. THANK YOU. THANK YOU. THANK YOU!

---

### Post by chris1379 on 2010-11-03
I have the same problem with a PCG-FX150. Did you add the lines to xorg.conf or replace it with the above lines?

---

### Post by Jamhart88 on 2010-11-15
My entire xorg.conf is set exactly as stated on "January 4th, 2009" post - so yes, I replaced it with the above lines. (still working perfectly with xubuntu 10.04).

---

### Post by chris1379 on 2010-11-15
Thanks, it works for me too. Does your LCD backlight turn off? Mine refuses to go off no matter what I do.

---

### Post by chris1379 on 2010-11-15
> **sunnynice said:**
> turn off?
By setting power management to put the display to sleep after a few minutes or by typing ```
xset dpms force off
``` My screen goes blank but the backlight is still on. It's easier to see in a dark room.

---

### Post by talvey on 2010-11-21
[Jamhart88]("http://ubuntuforums.org/member.php?u=157605") -- xorg.conf setup worked perfectly for a Sony PCG-FX140.  Thank you!  I spent several hours on this prior to finding your post.

---

