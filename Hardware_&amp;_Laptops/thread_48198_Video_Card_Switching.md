---
title: "Video Card Switching"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by Quatre on 2005-07-11
Right now Ubuntu is using my onboard graphics card, whichisn't working, and I want to get it to use my extra nVidia  GeForceFX 5200 card instead.  How would I get this done?

---

### Post by brim4brim on 2005-07-11
[QUOTE=Quatre]Right now Ubuntu is using my onboard graphics card, whichisn't working, and I want to get it to use my extra nVidia  GeForceFX 5200 card instead.  How would I get this done?[/QUOTE]

There's a driver at nVidia's site for that card.  Just download the .run and follow the instructions for install and modify your xorg.conf file in /etc/X11/

Everything you need should be in the readmes by nVidia and if you follow the links in my sig you should get an Ubuntu specific how to if your still stuck.

---

### Post by Quatre on 2005-07-11
[QUOTE=brim4brim]There's a driver at nVidia's site for that card.  Just download the .run and follow the instructions for install and modify your xorg.conf file in /etc/X11/

Everything you need should be in the readmes by nVidia and if you follow the links in my sig you should get an Ubuntu specific how to if your still stuck.[/QUOTE]
 I don't know how to do that.  I can't even get into the GUI because of the first video card.  I don't know how to run the .run file.

Also, how do you get a copy of you xorg.conf file?  I don't know how to get to that or copy it out so I can get a solution to my problem.

---

### Post by varunus on 2005-07-11
There's a howto in the "tips and tricks section" on howto set up nvidia cards in ubuntu.  I think you can also just type 

```
sudo apt-get install nvidia-glx nvidia-settings
```

at a console prompt.

You could also try turning off your onboard card in your BIOS.  What card is it?  Maybe we can get it working, and then you can do something like dual monitors... :)   At the very least we can get you into a GUI off that card temporarily.

---

### Post by Quatre on 2005-07-11
[QUOTE=varunus]There's a howto in the "tips and tricks section" on howto set up nvidia cards in ubuntu.  I think you can also just type 

```
sudo apt-get install nvidia-glx nvidia-settings
```

at a console prompt.

You could also try turning off your onboard card in your BIOS.  What card is it?  Maybe we can get it working, and then you can do something like dual monitors... :)   At the very least we can get you into a GUI off that card temporarily.[/QUOTE]
 I accually think the card is broken.  It doesn't seem to work in Windows.  Also, it's an Intel(R) 82845G/GL/GE/PE/GV Graphics Controler.(That's what the device manager says it is.)

---

### Post by varunus on 2005-07-11
Heh, I have that card on my system too, and it worked out of the box for me...Also, if it won't work in Windows either, then it probably is broken.

Can you disable the card in your BIOS?  If you do this, then just boot in recovery mode and do a "sudo dpkg-reconfigure xserver-xorg", or, if you want, reinstall.  You should install the nvidia drivers once you're able to get a basic GUI running.

---

### Post by Quatre on 2005-07-11
I don't know if this is bad, but the BIOS says that my video card it's using is my nvidia and not the onboard one.  Is there a way to disable the oboards graphics in the BIOS?

---

### Post by varunus on 2005-07-11
Every BIOS is different in how onboard video is handled.  Check and see if there's an "Onboard Video Enabled" option or not.

If the NVIDIA card is the one being used, and the other card is disabled, then there's something wrong with your xorg.conf.  Can you post it here?  Also your /var/log/Xorg.0.log

If you want to take a crack at configuring it, run sudo dpkg-reconfigure xserver-xorg

---

### Post by Quatre on 2005-07-11
Like I said before I don't know how to get my copy of that so I can post it.  Is there a drive where I can get it from?

---

