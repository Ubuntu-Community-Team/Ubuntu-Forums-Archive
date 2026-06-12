---
title: "nVidia Driver Not Working"
date: 2008-09-03
forum: General Help
---

### Post by Thecoolguru on 2008-09-03
I installed the driver, and the hardware drivers thing says has enabled checked, but it also says not in use. When i hover over it, the info thing says "The driver is necessary to support the hardware, and there is no free/open alternative. If the driver is not enabled, the ahrdware will not function."

What do I do??

---

### Post by werries on 2008-09-03
Did you restart?

---

### Post by ntbutler on 2008-09-03
Does it appear that the graphics driver is active? If everything is working as it should, then it shouldn't really matter. If not, try going to the nvidia website and downloading the newest driver from there.
If you try it this way, follow the instructions in this thread [http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")

I should caution you though, i have been battling to get my machine working with this friggin graphics card (mine is an 8800GT). I am not sure what the problem is, i am not getting much help on the subject, but i think there may be conflictions between nvidia cards, compiz and/or Xorg. Just make sure you back up everything first, because in my experience a lot of reinstaalling the os follows when updating stuff in hardy...

Hope that helps!

---

### Post by Thecoolguru on 2008-09-03
Well, the main reason I wanted my graphics card to work was so I could use purtiful desktop effects. I installed Compiz Fusion, messed around with settings, and the cube rotating effect isn't working. Do you think it has to do with my lack of usable graphics card? Sorry about having to ask all these questions- I should be a pro at this, because I've spent more time installing and configuring Linux distros than i've spent using them... it's always the same process- install, re-get familiar with the OS, download drivers, etc., work out themes/purtiness, get Wine HQ and start getting all my apps back, blah blah blah. I should be good at this! This is my 5th time installing Ubuntu in the past year and a half.

---

### Post by ntbutler on 2008-09-03
Believe me mate, i feel your pain.
The only thing i can suggest at the moment is to make sure you have all you want/need backed up, grit your teeth and have a go, trying your hardest not to throw your machine out the window if it goes down.
If you are trying to get the cube effect working, is it saying something like you don't have a graphics card installed for it, or it just isn't working?

---

### Post by Thecoolguru on 2008-09-04
When I went to try to enable Extra in the visual effects tab of Appearance, I got an error message saying that it couldn't enable desktop effects. Also, when I tried to use my graphics card driver, instead of getting a bright 'n cheery login screen when I booted up, I got a suspicious flickering dark blue screen. I managed to fix it super easily in only a few minutes using recovery mode, but that definitely isn't what you want to happen when you enable your graphics card :p. One thing that also isn't working for me is Emerald themes. None of the desktop purtification things are working! >:[

---

### Post by ntbutler on 2008-09-04
Hmm, not sure what is happening anymore. I just had a crash on my system and now all of a sudden all my effects are disabled (not something i did...)
I am going to keep trying to tackle this, and i'll let you knom if i get anything working. If worst comes to worst i am going to wait for 8.10 to be released and see if that helps at all...
Sorry man, but i am completely stumped, this is the worst distro i have tried yet :(

---

### Post by falcon61102 on 2008-09-04
You could reinstall the drivers.  Since you're having all this trouble, I'd recommend using Envyng to install the new ones after you uninstall what you have now.  To get envy, run:
```
sudo apt-get install envyng-gtk
```

And to use:
```
sudo envyng-gtk
```

Envy will automatically download and install the drivers for you.  They don't use the most current but they use a newer version that is very stable.

Once you reboot, you should see the nVidia welcome screen if you haven't disabled it in xorg.conf.  And if you need to make any adjustments, you can use nvidia-settings:
```
sudo apt-get install nvidia-settings
sudo nvidia-settings
```

---

