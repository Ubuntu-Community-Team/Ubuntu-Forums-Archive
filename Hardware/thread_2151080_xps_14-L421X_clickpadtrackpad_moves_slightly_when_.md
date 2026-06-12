---
title: "xps 14-L421X clickpad/trackpad moves slightly when I click"
date: 2013-06-03
forum: Hardware
---

### Post by alexalexalex on 2013-06-03
Every time I click by pushing down on my clickpad, the cursor moves slightly, especially when i release the click. It makes a small jump. This is very annoying since precise actions like selecting text are close to impossible! It works ok if i tap as opposed to pressing down on the clickpad.

Anything I can do? I have tried changing the parameters in synclient but they don't help.

Thank you!

---

### Post by racie on 2013-06-03
I know it isn&#8217;t the answer you&#8217;re looking for, but have you tried turning off "tap to click?"

---

### Post by mcoaky on 2013-10-07
That's not it...
I have a XPS 14 (ultrabook) and this is driving me insane. I have tried everything that could be found on google, but not a single one works properly.

Every time I click, either with "touch to click" or by pressing the hard button, the pointer moves (sometimes a lot).

---

### Post by royer10r on 2013-10-27
same here... i have tried many different drivers and nothing works. 

xps ultrabook - 12.04/12.10/13.04 - all the same. even tried the newest kernel to no avail.

---

### Post by dom134 on 2013-11-09
I also have a Dell XPS 14-L421X running 64-bit 13.10 and also have this problem.

---

### Post by aeronutt on 2013-11-22
I'm having this problem on a lenovo. I'm pretty sure it's a problem with the synaptics driver in 'ClickPad' mode (where the R and L mouse buttons are integrated into the trackpad). I've tried a few dozen different synaptics settings (via xinput and/or synclient), and cannot get it to work properly. Very dissapointing. I even set the bottom edge of the trackpad up above the button area, and under some circumstacnes the driver STILL detected my finger on the buttons as a mouse movement.

---

### Post by dom134 on 2013-12-02
Hello again, further to my last, I tried the Synclient tweaks here:
[http://ubuntuforums.org/showthread.php?t=2127448](http://ubuntuforums.org/showthread.php?t=2127448)

I used 48 rather than the 72 he used.  The touchpad feels slightly sluggish, but the movement when clicking has diminished.

---

### Post by K3N8 on 2014-01-27
> **dom134 said:**
> Hello again, further to my last, I tried the Synclient tweaks here:
[http://ubuntuforums.org/showthread.php?t=2127448](http://ubuntuforums.org/showthread.php?t=2127448)

I used 48 rather than the 72 he used.  The touchpad feels slightly sluggish, but the movement when clicking has diminished.
Thankx! This was a big help. I agree that 48 feels better.

---

