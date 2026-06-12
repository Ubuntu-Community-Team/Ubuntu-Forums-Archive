---
title: "Inspiron 5100 screen resolution"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by cragmonkey on 2007-04-03
So I have been running ubuntu on my Dell Inspiron 5100 with the infamous ATI Radeon Mobility 7500 for about a month now. I love it. The only thing that baffles me is that I cannot get the screen resolution to go beyond 1024x768. I have checked my xorg.conf and it indicates that higher ("1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480) should be available but they are not. I am a relative noob at linux so tell me what files/outputs you need to help me with this issue. 

BTW- I know my graphics card supports above 1024x768 because winblows displays them just fine.

---

### Post by amohanty on 2007-04-03
First off, statements like this:
> because winblows
really doesnt help the F/OSS community :) You have to agree that it sounds a bit juvenile.

Agreed, that windows has its faults, but the things it does it does fairly well. Also be ready to defend that statement if you are make it :) If you do the research you will be surprised. I would also suggest looking for an reading the 'Unix hater's handbook' (it was written before I was born), but here again you will be surprised the degree to which unix' inanities still survive.

Now to your problem, in a terminal type:
sudo dpkg-reconfigure xserver-xorg

select the defaults till you get to the screen where screen resolutions are specified and select the ones you want. Finish the process.

Having done that see if you can switch using System->Preferences->Screen Resolution.

HTH
AM

---

### Post by cragmonkey on 2007-04-03
> **amohanty said:**
> First off, statements like this:

really doesnt help the F/OSS community :) You have to agree that it sounds a bit juvenile.

Agreed, that windows has its faults, but the things it does it does fairly well. Also be ready to defend that statement if you are make it :) If you do the research you will be surprised. I would also suggest looking for an reading the 'Unix hater's handbook' (it was written before I was born), but here again you will be surprised the degree to which unix' inanities still survive.


Touche`, I am actually a windows IT Professional so Microsoft perverbially 'pays the bills'. I just get frustrated with unnecessary difficulties with some of the closed-source software I work with on a daily basis. My apologies to the Open Source Community.... I  want to be a good free-software denizen.

I am not at my Ubuntu machine ATM but will try your advice tonight.

---

### Post by jjordan on 2007-04-04
I would recommend you make a backup of your "working" xorg.conf file before you start.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.4-4-07 (I use the date for a bang in the head quick ref. that won't be overwritten by other processes) Don't worry about extensions in the Linux world, OK not true, but not as much.

A quick check of the Net indicates that the native resolution for this laptop is 1024 X 768.  If you are trying to run an external monitor at a higher resolution make sure it is hooked up before you start X windows.  

How are trying to change the resolution?

open a terminal and type
 **xrandr -q** 
to see what resolutions are available
if the resolution you want is listed note the number preceding it
then type
**sudo xrandr -s X**  X being the number you noted above.

- j

---

