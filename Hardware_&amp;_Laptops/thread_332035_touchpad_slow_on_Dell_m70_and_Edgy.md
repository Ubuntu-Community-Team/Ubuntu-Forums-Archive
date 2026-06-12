---
title: "touchpad slow on Dell m70 and Edgy"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by ozp on 2007-01-05
My touchpad was ok. 
Then I think after Ive installed imwheel and make modifications told on ubuntuguide to enable 5 bottons the touchpad got slow

I dont have a clue on how to fix this. I dont use it a lot, but sometimes I need to use.
Like it is now, the computer will have no use without a mouse

This thread is about dapper, I dont know if it will work on edgy
[http://ubuntuforums.org/showthread.php?t=140825](http://ubuntuforums.org/showthread.php?t=140825)

how to accelerate the touchpad?

---

### Post by mojoman on 2007-01-05
You can probably fix this by editing the settings in your xorg.conf-file (/etc/X11/xorg.conf).

There should be a "section input device" with identifier "synaptics touchpad" (or something like that). In that section you should have MinSpeed and MaxSpeed. Increase these numbers (try doubling them to start with) and then restart x-server and try it out. You'll probably have to try a couple of different values before finding something you like. I had this problem when I changed from Xubuntu 6.06 to Debian Etch on my laptop and it took some tweaking but now it's working just fine. 

You can also install a package called gsynaptics, which is a graphical configuration tool. However, you still need to tweek xorg.conf in order to sewt min and max speed (and use gsynaptics to finetune it). The graphical tool also requires the option "SHMConfig" "on" in order to function but should show up on the gnome menu.

To edit xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```

To install gsynaptics:
```
sudo apt-get install gsynaptics
```

To restart x-server, log out and hit ctrl+alt+backspace

Hope this helps
/Mojoman

---

### Post by ozp on 2007-01-05
ok! thanks!! Its working now.

Now I´try the gui

---

### Post by mojoman on 2007-01-06
Glad to help. I think that the GUI allows you to tweak the speed between the min-max values set in the xorg.conf but I only ran Debian Etch with Gnome for a short while before ditching Gnome in favour of Fluxbox. Now I have min and max value (same as before) but I have no idea which value x-server actually uses and on my lean, mean laptop machine I have no graphic configuration tools at all. But hey, it works, what more could I possible want? 

/Mojoman

---

### Post by ozp on 2007-01-06
The Gui worked fine!!!

They should include those laptop tools in a all-in-one pack 

now I`m almost completed my ubuntu installation

---

