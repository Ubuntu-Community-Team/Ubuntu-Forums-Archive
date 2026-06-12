---
title: "Latitude D505 stuck in 1400x1050 resolution"
date: 2011-09-11
forum: Hardware
---

### Post by travlemon on 2011-09-11
Hello Everyone,

I have a Dell Latitude D505 with the Intel 855 graphics chipset.   I hear there is some negative energy attached to the relationship between the 855 chipset and Linux.

**The Problem:**
I have tried installing a few different Ubuntu based distributions on this laptop in the past, including regular Ubuntu.  Everything seems to work, except that the only screen resolution available on the machine is 1400x1050.  This is the native resolution on this model laptop, but it simply makes things too small and I'd prefer switching it to 1024x768.  I've tried installing the OS and running full system updates, in hopes of something updating to fix the issue, but no luck.

Google searches on the problem usually return results of the opposite problem for users, they have every other resolution but 1400x1050.

Does anyone know how to fix this problem?  This particular issue is a deal breaker for me, as the person I got this computer for has trouble seeing the small fonts and such.

As always, a huge thank you in advance to the people who take the time to help with problems!

---

### Post by whatthefunk on 2011-09-11
You could modify your xorg.conf file in /etc/X11/.

---

### Post by travlemon on 2011-09-11
> **whatthefunk said:**
> You could modify your xorg.conf file in /etc/X11/.

Hello, thanks for your response!

What type of modification do you think I should make to the file?  I've only been using Linux for a year and a half now, and there's still a lot I don't know.  

I know how to open the xorg.conf file in an editor, but I'm not sure what lines to add/modify.

---

### Post by whatthefunk on 2011-09-11
I suppose before you try to manually edit your xorg.conf you could try to force a change with xrandr.  First see if 1024x768 is already enabled by typing this in a terminal:
```
xrandr
```

Post the outputs here.

---

### Post by travlemon on 2011-09-12
> **whatthefunk said:**
> I suppose before you try to manually edit your xorg.conf you could try to force a change with xrandr.  First see if 1024x768 is already enabled by typing this in a terminal:
```
xrandr
```

Post the outputs here.

Thanks again for responding.  I actually ran this before posting, but I didn't think to post the output.  Here is the output of the **xrandr** command:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1400 x 1050, current 1400 x 1050, maximum 1400 x 1050
default connected 1400x1050+0+0 0mm x 0mm
   1400x1050       0.0* 
```

One other important thing I must mention is that the laptop is currently running a Fedora based OS, and it does let me use 1024x768 and the other available resolutions for this card.  But I'd really like to get the Lubuntu OS on here if I fix the problem.

---

### Post by whatthefunk on 2011-09-12
Try this:

```
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
```
xrandr --addmode VGA 1024x768
```
```
xrandr --output VGA --mode 1024x768
```

---

### Post by travlemon on 2011-09-12
> **whatthefunk said:**
> Try this:

```
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
``````
xrandr --addmode VGA 1024x768
``````
xrandr --output VGA --mode 1024x768
```

Thanks again for your suggestion!

I tried running those commands, and I get an error that says **Failed to get size of gamma for output default**.  Fro the commands that reference VGA,  I get the gamma error plus this error:  **warning: output VGA not found; ignoring**.

Do you have any suggestions?  While I'm awaiting a response, I'm going to generate a xorg.conf file with **sudo Xorg -configure** and try to see if the xorg.conf file gives me any clues on what VGA might need to be replaced with.

EDIT:  I would also like to point out that after running the above commands, 1024x768 shows up in the Monitors section to change the resolution, but does not do anything when I try to change it.  I generated the xorg.conf file and looked at it, but I'm not savvy enough to get any ideas from it.

EDIT 2:  I noticed that in xrandr's output, it says that **default** is connected.  So I replaced VGA with **default** in the commands you gave me.  This appears to be a step in the right direction.  It still tells me it's failing to get the gamma size.  After the gamma error, it shows the error **"Configure crtc 0 failed"**.
I am looking into these errors now. Also, when trying to change the resolution to 1024x768, it actually flickers the screen like it's going to work. If you have anymore suggestions, I'd greatly appreciate them.  Thanks!

---

### Post by travlemon on 2011-09-12
Ok,

I feel really dumb...I got it working with a very simple solution.  I generated a xorg.conf file via this command:

```
sudo Xorg -configure
```

If you're familiar with this, you know that the xorg.conf file is genereated in your home directory for you to review, before copying it to the **/etc/X11** folder. 

So...I moved the **xorg.conf** to **/etc/X11** and restarted X...and get all of the resolutions that I want/need.   I was able to flawlessly change the resolution to 1024x768.


Sorry for your wasted time, WhatTheFunk :-\

Anyway, thanks so much!!! I will be printing this thread to PDF and filing it away!

---

### Post by whatthefunk on 2011-09-12
Glad you figured it out.  Im also glad that you told me how to do it...I had to deal with this a long time ago and couldnt remember exactly how to do it.

---

### Post by travlemon on 2011-09-13
> **whatthefunk said:**
> Glad you figured it out.  Im also glad that you told me how to do it...I had to deal with this a long time ago and couldnt remember exactly how to do it.


Ah, glad I could help!  Though I have another issue with it now.  Those Intel 855 drivers are pretty rough.  With xorg.conf present in the /etc/X11 directory, the graphics buggy to the point that the computer is almost unusual.

I get the feeling that I won't be able to solve that one, and it's more of a wait-for-a-new-driver thing.

---

### Post by travlemon on 2011-09-13
I am going to mark this thread as solved, as I figured out how to open up the other resolution options for the computer.  I will start a new thread on issue with the Intel 855gm graphics driver, and the heading will reflect the new problem.

---

