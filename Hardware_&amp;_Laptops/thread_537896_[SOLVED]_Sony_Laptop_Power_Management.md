---
title: "[SOLVED] Sony Laptop Power Management"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by chrisolof on 2007-08-29
Hello - I have a Sony Vaio laptop (PCG-V505AX) with an almost worthless battery.  Under Windows, Sony included a program called PowerPanel by Phoenix Technologies that allows me to set up fairly aggressive power management settings.  Using this program I am able to get almost two hours of battery life.  The settings of interest (that allow for such a long run out of such an old battery) are:
[LIST]
[*]CPU:  Battery Life (Processor Frequency Scaling)
[*]Thermal Control Strategy:  Quiet (This slows the fans down)
[*]Lid Close Action: LCD Off
[*]LCD Brightness:  Level 1 (dark)
[*]Turn LCD Off (LCD Standby):  15 Seconds
[*]LCD Power Saving Mode:  On
[*]Hard Disk Standby Timer:  1 Minute
[*]Optical Drive Power Saving:  On (this one cuts power to the optical drive)
[/LIST]

When using Ubuntu 7.04 on this laptop, I am only able to get about 35 minutes of uptime.  Part of the problem seems to be that Ubuntu does not actually turn off my screen - just projects black to it instead - which is still consuming battery life - and doesn't have an option I am aware of to turn the LCD off after 15 seconds.  I think the lowest it went was 1 minute (or something close to that).  It also doesn't seem to dim the screen when I select that option in Ubuntu's power settings.  The only way I can dim the screen is to use a combination of Function+F5 to dim and Function F6 to brighten.

My question is:  Is there any way to get basic power management settings such as LCD dimming and LCD off power management settings working?

And if so, is there then a way to get the advanced power management settings referenced above working?

Thanks in advance for any help- this is the only thing keeping me from using Ubuntu as the primary operating system on my laptop (I'm so sick of Windows!).

--
Chris

---

### Post by spier on 2007-08-29
What about  Gnome's Power Management? It let you set brightness, liid behavior, suspend & hibernate actions. You will find it in System > Preferences.

Another helpful applet is  Gnome CPU Scaling Monitor. It`ll let you select cpu  frequency while running on AC or battery. You`d find it byright-clicking on a panel, then:
Add to Panel > CPU Frequency Scaling Monitor.

Both applet were installed out of the box in my vaio FS. Not sure about your model, though.

Good luck!

---

### Post by benhagerty on 2007-08-29
I have the same problem. It is such a pain

---

### Post by chrisolof on 2007-08-29
Thanks spier,

The problem isn't so much finding where the out-of-the-box settings are in Ubuntu - it's that the one's provided are very limited compared to the PowerPanel app, and that they don't seem to control my laptop.

For instance, when I slide the "Set display brightness to:" bar all the way down to 0%, or make any change to it whatsoever, nothing changes physically on my LCD.  Things are still just as bright as ever.

And another tough one is the slider "Put display to sleep when inactive for:" - which only goes down to 11 minutes (I'd really prefer 15 seconds here).  The worst part of this one is that it doesn't actually put the display to sleep - just projects a black image to it with full power.

So, I'm thinking maybe Ubuntu isn't interfacing correctly with my laptop's LCD.  Does anyone know a fix for that?

Also - is there a way to tell the hard-drive to suspend after a period of inactivity - or a way to shut off the optical drive?

One thing is working right now - and that's processor frequency scaling (spier's suggestion of the "CPU Frequency Scaling Monitor" panel applet confirms it) - so that's a start.

Anyway - if anyone has any more suggestions I'm all ears!

Thanks,

---

### Post by jackhynes on 2007-08-31
> **chrisolof said:**
> 
For instance, when I slide the "Set display brightness to:" bar all the way down to 0%, or make any change to it whatsoever, nothing changes physically on my LCD.  Things are still just as bright as ever.

[..]

So, I'm thinking maybe Ubuntu isn't interfacing correctly with my laptop's LCD.  Does anyone know a fix for that?


Same problems here. My battery doesn't last for an episode of Heroes! Plus my fan always runs, and there's still a lot of overheating.

---

### Post by ddinsdale on 2007-09-04
Aha!  I was searching for a problem with my Vaio GRX series and found this.  I upgraded from Edgy to Feisty and the control panel applet that allows you to control power settings is gone!   My previous settings still work, but I can't see them anymore.   

From reading this, it looks like there  is no more power settings applet.  There used to be a dedicated sony vaio screen in the control center.  Anyone else notice this?  

Thanks.

---

### Post by chrisolof on 2007-09-12
Ok- After more searching I was able to get a working solution.  Believe it or not, the Ubuntu built-in help file led me to the solution.

If you go to System -> Preferences -> Power Management
Click the "Help" Button.

In there is some valuable information that explains everything I asked about in this post.  More specifically, I found the FAQ section of that help area to be the most informative.

The answer to my specific problems were solved by opening up a terminal and typing:

```
gconf-editor
```

Once in there I needed to change some values in "gnome-power-manager" and "gnome-screensaver," which are both found under "apps."

Using the help file mentioned above I was able to get my system's power management settings fine tuned.  I'm now achieving better battery life in Ubuntu than Windows, which is great!

There isn't a hard-drive power-off feature in the power management settings, and that's because, as the help-file explains:
"After numerous debates, the consensus was that is was not a good idea to add this functionality to HAL.  It's was decided user-configurable power management was not really required when modern hard disks have really intelligent power management."

More details on that and much, much more in the help file.

---

### Post by chrisolof on 2007-10-17
To update this with yet another fix / solution:

I also got the LCD dimming slider to work correctly (finally!).  So now I don't have to manually adjust the display brightness with the Fn keys anymore.  When I unplug the power adapter, the screen now dims to the level I've set in the Power Management settings.  Seems there were two typos in the dimming scripts.  Anyway, here's what did the trick:

```

cd /usr/lib/hal/scripts/linux
sudo gedit hal-system-lcd-get-brightness-linux
```

Then change the first line from "#!/bin/sh" into "#!/bin/bash"
Save and close it.

```

sudo gedit hal-system-lcd-set-brightness-linux
```

As with the former file, change the first line from "#!/bin/sh" into "#!/bin/bash"
Save and close it.

And that's it- try unplugging the power adapter - your screen should dim (if you've set it to under the power management settings).

Note:  I found this procedure within another Ubuntu Forums thread:
[Problems with lcd brightness with Feisty and sony vaio pcg-k315s]("http://ubuntuforums.org/showthread.php?p=3181402")

Hope this all helps-

---

### Post by jonnyalpha on 2007-12-04
> **chrisolof said:**
> To update this with yet another fix / solution:

I also got the LCD dimming slider to work correctly (finally!).  So now I don't have to manually adjust the display brightness with the Fn keys anymore.  When I unplug the power adapter, the screen now dims to the level I've set in the Power Management settings.  Seems there were two typos in the dimming scripts.  Anyway, here's what did the trick:

```

cd /usr/lib/hal/scripts/linux
sudo gedit hal-system-lcd-get-brightness-linux
```

Then change the first line from "#!/bin/sh" into "#!/bin/bash"
Save and close it.

```

sudo gedit hal-system-lcd-set-brightness-linux
```

As with the former file, change the first line from "#!/bin/sh" into "#!/bin/bash"
Save and close it.

And that's it- try unplugging the power adapter - your screen should dim (if you've set it to under the power management settings).

Note:  I found this procedure within another Ubuntu Forums thread:
[Problems with lcd brightness with Feisty and sony vaio pcg-k315s]("http://ubuntuforums.org/showthread.php?p=3181402")

Hope this all helps-

Thanks Chris 
Works on my sony vaio VGN-FS285M. Been looking for a solution for ages. Again many thanks.

---

