---
title: "Cant Change Screen Resolution"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by richlewt on 2009-06-03
Hi All
This is my first post on this forum (sorry if its a bit basic) This is my first dabble into Linux. I have built this machine from a load of bits I had lying around. My video card is an Nvidia Geforce 2mx 32 Mb. I have loaded the latest version of Ubuntu and it came up with an 800x600 res. I had a dabble around and found the Hardware Drivers screen and it offered me a Nvidia accelerated graphics driver (version 96) which I loaded (thought I was doing well at this stage :D)
Anyway, try I as I might I can not get the card to display anything but 800x600. Under X Server displays it just gives me Auto, everything else appears greyed out. The monitor I am using is a Sony Multiscan 200GS CRT if thats any help?
Any help would be greatly appreciated.

---

### Post by dstew on 2009-06-03
What Ubuntu flavor do you have? If it is 8.04, there is a display configuration manager that you can access this way: Press alt-F2 to get a command line. Enter```
gksudo displayconfig-gtk
```Then you can pick your monitor type, change resolution etc. I think newer Ubuntu flavors have a Screen Resolution menu item that does this.

---

### Post by richlewt on 2009-06-04
Hi
I have downloaded the latest version. The only way I can see to change it is through System- Preference- Display which gives me the dialogue box I described in my first post, everything is locked out.

---

### Post by dstew on 2009-06-04
What do you mean "locked out"? You cannot access the menu item?

---

### Post by Steelmourne on 2009-06-04
That card is not officially supported by nvidia anymore:

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

If it isn't listed drivers won't work properly (or at all)

---

### Post by richlewt on 2009-06-05
Hi
Thanks for that, so I guess its a new card then eh?

---

### Post by richlewt on 2009-06-13
Hi
I now have a maxigamer xentor 32 (which I think is an nvidia riva chipest) Does anyone know where i can get a driver for this card?

---

### Post by richlewt on 2009-06-20
Hi
I have gone back to square one. I have had a look at the ADD/REMOVE application section of this software. Under System Tools there is a list of Nvidia drivers, I have installed the Nvidia binary x-org version '96 driver and it says it supports my Gforce MX 100/200 which is my card. I installed the card, ran the driver installation but when I try and change the screen resolution it is locked on the auto setting and I cant see anyway of changing it.
Can someone give me some indication what to do, this is driving me mad :p

---

### Post by mhgsys on 2009-06-21
you might wanna try setting it with :
System > Preferences > Display.

If you get;
It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

Just click NO, and set the resolution.

I don't know why exactly, but it works for my GeForce4 Ti 4200.
Everytime I used nvidia-settings (even as root and saving the file to xorg.conf) my resolution kept changing back to 800 x 600 as well.
This way it keeps my display 1280x1024 all the time.

---

### Post by Tews on 2009-06-21
Here's how I solved this exact problem with the same video card ... 

1. Open Nautilus as root

   ```
gksudo nautilus
```

2. Open xorg.config .. ~etc/X11/xorg.config

3. Try a screen section that looks something like (replace 1440 and 900 with your preferred resolution):

```

   Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes      "1440x900"
		Virtual	1440 900
	EndSubSection
EndSection
```

save, then reboot, and  use the Display tool to change screen res.

---

### Post by richlewt on 2009-06-22
> **mhgsys said:**
> you might wanna try setting it with :
System > Preferences > Display.
 
If you get;
It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?
 
Just click NO, and set the resolution.
 
I don't know why exactly, but it works for my GeForce4 Ti 4200.
Everytime I used nvidia-settings (even as root and saving the file to xorg.conf) my resolution kept changing back to 800 x 600 as well.
This way it keeps my display 1280x1024 all the time.
Hi
Thanks for the reply. I tried this but when I go to set the resolution it only offers me 800x600, 640x480, 400x300 and 320x240?

---

### Post by richlewt on 2009-06-22
> **Tews said:**
> Here's how I solved this exact problem with the same video card ... 
 
1. Open Nautilus as root
 
```
gksudo nautilus
```
 
2. Open xorg.config .. ~etc/X11/xorg.config
 
3. Try a screen section that looks something like (replace 1440 and 900 with your preferred resolution):
 
```

   Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes      "1440x900"
        Virtual    1440 900
    EndSubSection
EndSection
```
 
save, then reboot, and use the Display tool to change screen res.
 Hi
Thanks for replying. I tried this, all went ok until the reboot, then I had a dialogue box saying the machine wanted to start in low-graphics mode. I could not see a way of getting the machine up to allow be to get to the display to change it. Went back in and the xorg.config had been overwritten. So edited it again and when it came up and said "It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?" I selected no (as suggested in previous post) this time I was offered a higher res of 1024x768 what I entered in the config file, I thought I had it sussed, but although the res has been set the fonts are just as big but it seems the screen has got larger and scrolled off to the right?
Any clues?

---

### Post by mhgsys on 2009-06-22
You might want to edit your xorg.conf and add HorizSyn and VertRefresh to the monitor section :

HorizSync	30-57
VertRefresh	43-72
In the monitor section.

But these ranges can variate, depending on your monitor.

---

### Post by richlewt on 2009-07-01
> **mhgsys said:**
> You might want to edit your xorg.conf and add HorizSyn and VertRefresh to the monitor section :
 
HorizSync    30-57
VertRefresh    43-72
In the monitor section.
 
But these ranges can variate, depending on your monitor.
Hi
Just got back from a weeks holiday.
Ok, added above values to my config file, rebooted and it all went wrong!!
When machine starts it hangs and says "kernel panic- not syncing: Attempted to kill init!"
and it wont budge.
Any clues?

---

### Post by richlewt on 2009-07-10
Hi
Reinstalled Ubuntu.
Dug through my desk and found monitor manual.
Went back through above procedure and my xorg.conf looks like this
 
  Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes      "1280x1024"
        Virtual    1280 1024
        HorizSynch 80
        VertRefresh 75
    EndSubSection
EndSection
 
I got the HorizSynch and VertRefresh values from my manual.
I rebooted and am now presented with a screen with 4 options as follows:
1) Run ubuntu in low graphics mode for one session.
2) Reconfigure graphics
3) Troubleshoot error
4) Exit to consule log in
 
Any help please.

---

### Post by richlewt on 2009-07-10
Yehaah!!
Managed to sort it. I checked my error logs and put the horizsync in the wrong place in the config file. I now have my old card running at 1280x1024.
Phew, that was a struggle but I learnt something.

---

### Post by elvisem on 2009-07-10
I have the same problem and was just wondering if you could post your xorg.conf file to compare. Thanks.

---

### Post by richlewt on 2009-07-11
> **elvisem said:**
> I have the same problem and was just wondering if you could post your xorg.conf file to compare. Thanks.
Hi
No problem, file pasted below
 
================================
Section "Device"
Identifier "Configured Video Device"
EndSection
Section "Monitor"
HorizSync 80
VertRefresh 75
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Modes "1280x1024"
Virtual 1280 1024
 EndSubSection
EndSection
 
=========================================

---

