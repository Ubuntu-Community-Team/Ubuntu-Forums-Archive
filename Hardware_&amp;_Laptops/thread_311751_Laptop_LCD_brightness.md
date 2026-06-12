---
title: "Laptop LCD brightness"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by numbers1thru9 on 2006-12-03
On my laptop when ubuntu is loading, it likes to cut my brightness down on my laptop lcd, how can i fix this?

---

### Post by strabes on 2006-12-03
fn + up/down?

---

### Post by mikerduffy on 2006-12-11
I noticed this as well. (Kubuntu 6.10, amd64)

I've been readjusting my screen brightness every time I boot, and it's irritating as all get-up.  Is there a way to fix this?

---

### Post by anak_design on 2006-12-11
Me too. I need a solution to this problem. My eyes hurt from looking at my laptop for too long. Is there anyway we could set a keyboard shortcut that dims the backlight? Cheers.

p/s: I just moved to Ubuntu and loving it so far. I'll love it more once I've figured out how I did more things on linux (list is on my side bar at my blog.. designbyindra.blogspot.com)

---

### Post by David Corrales on 2006-12-11
The next version of gnome will probably include a cool applet to adjust brightness from the panel.
For now, I use the vendor hot keys.

---

### Post by mikerduffy on 2006-12-11
> **David Corrales said:**
> The next version of gnome will probably include a cool applet to adjust brightness from the panel.
For now, I use the vendor hot keys.

I would like to know the mechanism that is resetting the brightness level at boot.

---

### Post by David Corrales on 2006-12-12
Most probably an acpi script.

---

### Post by crono141 on 2007-11-03
This topic is useless.  When I turn on the laptop, the screen is at full brightness.  As soon as Gutsy starts booting, it turns the brightness down so low its hard to see, and I have to manually adjust the brightness with the function keys.

What is causing the brightness to be reset from the default at boot, and how do we fix it?  Is nobody "in the know" experiencing this issue?

---

### Post by rosegarden78 on 2008-01-19
Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by hvacr on 2008-01-19
rosegarden78

Your fix does not help. My shortcut keys work, but the screen is very dim when I boot up. i have to set the screen brightness manually each time. Becoming a pain.

---

### Post by Yellow Pasque on 2008-01-19
When does your screen dim, upon entering GNOME? Type sudo gconf-editor in a terminal and look under /apps/gnome-power-manager/ for backlight settings.

---

### Post by rosegarden78 on 2008-01-19
Sorry to hear that ... can you make it a shell script or add the program you launch to Session Manager - Startup Programs?  You might not have to type or launch the activation each time.  Or maybe even a keyboard shortcut or macro?  I hope your LCD screen isn't burnt out or loose connection or something ... you can also make boot scripts by changing runlevels and init.d but I don't think they're necessary.  You may consider obtaining a Macro program ...

... by the way I updated the article to make it more clear to read.

---

### Post by p1977p on 2008-01-22
I have an AMD 64 laptop (Compaq) with nVidia graphics card. I'm unable to use my brightness function keys (they don't work). However, I find that one can set the brightness to a predetermined level by using '**nvidia-settings**' (you need to install it via Synaptic). Once installed, run "nvidia-settings" in Terminal. A window pops up. Go to the appropriate screen section ("XScreen 0" in my case) -> X Server Color correction.

Choose "all channels" as the active channel and lower the brightness and contrast to your desired level. You now need to save these values. 

Go to "nVidia settings Configuration" tab, and **uncheck **the "Include X display names in the config file" option.

Now quit the program. The brightness remains constant.

In fact, the current settings are restored the next time you run "nvidia-settings". Alternatively you can type "**nvidia-settings -l**"
 at the terminal prompt to load the settings only. Hope this solves the problem for most of you!


However I have not yet figured out to trap my special (br up/down) function keys to use them for this. I am not well versed in writing scripts; perhaps someone can incorporate this in a nice script that can be added to the standard keyboard shortcuts.

---

