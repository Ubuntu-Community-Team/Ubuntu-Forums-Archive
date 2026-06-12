---
title: "HP Laptop stuck at 1280x720"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by MrMusic on 2007-04-20
Hi,

I have been using ubuntu on a few machines, and never ran into this, but for some reason, on my HP Laptop with ATI video , the only choice available is 1024x720. This happened on both the beta and release version of feisty. Any idea of how to lower it to 800x600?

Thanks

---

### Post by MrMusic on 2007-04-20
Is there any other way to set the resolution or screen size in Ubuntu?

---

### Post by sarracenia88 on 2007-04-20
I am a geforce 7600 user and I didn't have a problem changing my resolution to 1280x1024. I just went into

sudo nano /etc/X11/xorg.conf

You just have to change all of the following so that they have your desired resolution

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation G70 [GeForce 7600 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1024x768" "832x624" [COLOR="Yellow"]"800x600"[/COLOR] "720x400" "640x480"
EndSubSection
EndSection


Then just restart you xserver.

The large screen section can be found at the bottom of your xorg file.

Hope this helps

I also use envy for installing my nvidia drivers. it works really well

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

This link also has ATI drivers on it too

Make sure that the 800x600 is in there.

---

### Post by MrMusic on 2007-04-22
Tried the script, but wouldn't install. Edited the xorg.conf file but would not do any other res. Tried changing the xorg.conf entries to "800x600" only but now shows an xorg error when it boots up, so can no longer boot.

Tried to sudo nano /etc/X11/xorg.conf to fix the problem, but looks like the file might be gone. Can't see why. Any ideas?

---

### Post by MrMusic on 2007-04-22
When I typed sudo nano /etc/X11/xorg.conf and made the needed changes, I used control write, then rebooted. Could that possibly have been wrong?

---

### Post by sarracenia88 on 2007-04-22
you should type in *sudo nano /etc/X11/xorg.conf* in to the terminal, then make the changes, then press control X. the program will tell you if you would like to make the changes, press y and you should be done. Then all you have to do is restart your xserver. to do that you press crtl, alt, backspace.

Hope this helps

---

### Post by MrMusic on 2007-04-22
Thanks, but looks like I will have to reinstall it. Can't get it to boot now. I get "failed to start the x server" now. If I type in sudo nano /etc/X11/xorg.conf  when the boot up fails, xorg.conf seems empty.

---

### Post by gpowell88 on 2007-04-22
Does your laptop use the Intel graphics accelerator?

I had this same exact problem when I updated yesterday.
See this thread:
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

---

### Post by MrMusic on 2007-04-22
Not sure, but don't think so, as it has built-in ATI graphics

---

### Post by MrMusic on 2007-04-22
Nothing has worked so far. The video adapter is an ati radeon igp 340m if that helps. Making the changes to xorg.conf  did not allow any changes. I have a feeling that  perhaps that fact that the laptop can send out video to a TV might be part of the problem. 2 Monitors show up.

Any other ideas? Freespire worked fine, so did Puppy Linux. Kubuntu has the same lack of other screen sizes.

---

### Post by MrMusic on 2007-04-22
Update: Ubuntu 6.60 has the correct screen size. Going to check out 6.10 and install it if the live cd shows that will work also. well, Ubuntu 6.10 can do 800x600 so installing it. Must be a bug in 7.04

---

### Post by sarracenia88 on 2007-04-23
sorry but I don't have a lot of experience with ATI cards, only nvidia. and also does it seem empty or is it actually empty. I know it stinks when the xorg fails and you can't boot up into the os anymore. When that happened, I just typed envy in again and reinstalled the drivers, then everything worked fine. Another thing that I like about that envy program.

---

### Post by MrMusic on 2007-04-23
Thanks for trying to help. I work with computers all the time, but still learning Linux, so unlike Windows where I know how to fix most problems, when linux acts up, I am at a loss. Now have 6.10 installed and 800x600 works fine. Anything larger is just too hard to see.

---

### Post by sarracenia88 on 2007-04-24
don't worry about it. I remember when I was in your situation. You will pick everything up real fast if you become a regular user of Ubuntu. I just started using Linux in October 2006, and I feel that I have come a long ways, including being the one helping instead of being helped all of the time, but I still need assistance from time to time. That is what is really cool about Ubuntu is since it is a community support oriented distro, people have actually been in your place at one point and can feel for you. a massive support center can't do that as well. I find Linux to be more friendly. Glad I could be of some help.

You will probably want to try out feisty now before you get a lot configured on your system because it has a lot better support for laptops. From what you said, you have 6.10 installed. You will like the features and stability found in 7.04 a lot better. If you screen gets stuck again, just do the same as above. the wireless features are great even though I don't use them because I only have a desktop.

---

