---
title: "ASUS N61Jv / N71Jv / N82Jv / UL50Vf anyone?"
date: 2010-03-03
forum: Hardware
---

### Post by avilella on 2010-03-03
Hi,

Has anyone tried the switchable graphics features in the linux kernel with a nvidia optimus graphics laptop like the ASUS N61Jv / N71Jv / N82Jv / UL50Vf?

For more info on what is switchable graphics: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

Cheers

---

### Post by danaur on 2010-03-03
Just got an ASUS N71J today (from my work) and tried to install Ubuntu 9.10. How disappointing, only a black screen. Searched for drivers (ASUS.com, nVidia.com) or any hints, nothing. I finally got it installed by choosing safe graphics mode before the install. For now I'm stuck with 1024x768 ... or ... what's almost worse, back to Windows (7). :/

Anyone who knows what to do, PLEASE respond. And how about waiting for 10.04? Will that presumably work with nVidia's Optimus? I sure hope so.

---

### Post by CrowBelgrade on 2010-03-04
> **danaur said:**
> 

Anyone who knows what to do, PLEASE respond. And how about waiting for 10.04? Will that presumably work with nVidia's Optimus? I sure hope so.

well you can waith but I cant start ubuntu 10.04 with new kernel 2.320-15 on my Asus K50IN with nv 102m. For now

---

### Post by avilella on 2010-03-06
airlied thinks these models will probably also have the _DSM method for hot switching at gdm level with vga_switcheroo (currently in linux-next):

[http://linux-hybrid-graphics.blogspot.com/2010/02/switchable-graphics-in-linux-now-as.html](http://linux-hybrid-graphics.blogspot.com/2010/02/switchable-graphics-in-linux-now-as.html)

Can you try and install the latest nouveau and see if the _DSM method works?
There is a good howto here:
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

> **danaur said:**
> Just got an ASUS N71J today (from my work) and tried to install Ubuntu 9.10. How disappointing, only a black screen. Searched for drivers (ASUS.com, nVidia.com) or any hints, nothing. I finally got it installed by choosing safe graphics mode before the install. For now I'm stuck with 1024x768 ... or ... what's almost worse, back to Windows (7). :/

Anyone who knows what to do, PLEASE respond. And how about waiting for 10.04? Will that presumably work with nVidia's Optimus? I sure hope so.

---

### Post by fdmille on 2010-03-23
NVIDIA Tech Support says no drivers are available for Linux.

[http://forums.nvidia.com/index.php?showtopic=163683](http://forums.nvidia.com/index.php?showtopic=163683)

Was going to buy a new ASUS N61JQ laptop, but have to keep looking!

---

### Post by AllRob on 2010-06-07
[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

**GeForce 300M series:**
GT 330M, GTS 250M, 310M, 305M, _**GT 325M**_,  GT 335M, GTS 350M, GTS 360M

did you try it out already? please provide some feedback, i'm considering ...

---

### Post by spinnekoppeke on 2010-06-11
Last week I bought the n61jv-jx laptop. I tried Asus x64j, which is n61jv, with ubuntu 10.04. This laptop is provided with I3-processor 350M, 500 gig hd, provided with 
* the Nvidia GeForce GT 325M. Here is a bit a problem : apparently Nvidia or Asus, doesn't want or doesn't have the needed drivers. Caused by this, the kernel falls back on the graphic drivers linked to the cpu-board, which is Intel. According to ubuntu the proprieratty drivers need to be installed, but if you do that, you get a nice black screen. I installed the 32-bit-kernel (2.6.32), and upgraded the kernel a few days later, because I read thhat dear Linus had done some kernel-based work on graphic drivers, certainly the Nvidia-drivers. Nevertheless, the new kernel didn't give any solution either. So as far as I can say, I am afraid to wait on decent testing and graphic Nvidia drivers. Till that time, I will cope with the Intel-graphical card, which is not that bad. (as long your coresbusiness isn't gaming)  the maxiumum resolution of 1366 x 768 pixels is handled without problem.
* Another problem are the function keys : apparently there are some problems with the function keys (f9 for disabling touchpad, and some others) : there is workaround for this.
* the high cpu generates a lot of power/heating : i sea the temperature is around 61°C, which is quite high if I compare it to an Asus 70m-laptop.

general : It is a decent laptop, with good cpu,  good led- screen ( too bad it is only 1366 x 768 pixels) , great sound. I use it more as a working laptop then a gaming laptop and it has good use for me. Only disadvantage : the absence of working Nvidia drivers.But I have good faith :)

greetz,
Johan

---

### Post by k0mpjut0r on 2010-06-22
> **spinnekoppeke said:**
> Here is a bit a problem : apparently Nvidia or Asus, doesn't want or doesn't have the needed drivers. Caused by this, the kernel falls back on the graphic drivers linked to the cpu-board, which is Intel. According to ubuntu the proprieratty drivers need to be installed, but if you do that, you get a nice black screen. 

I can confirm this, on an ASUS K52JC notebook (Intel i3 350m + NVIDIA 310M).

After installing Ubuntu 10.10, the 'Restricted drivers' window shows up, recommending to install the Nvidia drivers. However, after the first reboot, black screen shows up every time. Using the recovery option does not help, because the screen goes blank right after loading the nvidia driver, even in text-only mode, so even changing to other consoles (Ctrl+Fn) doesn't work.

I also tried to change the settings in BIOS, however the only options are Hybrid/Windows7, which is the default, and "Restricted", which turns on only the Intel HD graphics (no NVIDIA-only option).

I guess I'll have to wait until a working NVIDIA driver is released :)

---

### Post by cherrypie on 2010-07-03
hey guys u think those [http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html) will work ? they have been released at [SIZE=1]2010.06.22. i own asus n71jv ;)
[/SIZE]

---

### Post by EL_Staso on 2010-07-05
Any progress solving this matter?

---

### Post by cherrypie on 2010-07-05
well i dunno how and im even too afraid to try those after installing recommended drivers from ubuntu lol so i wait, anyone tried ?

---

### Post by dugh on 2010-07-11
Yeah when Ubuntu asks you if you want to install the proprietary Nvidia drivers, don't, you will get a black screen with no way out except booting to a live cd and disabling gdm.

I tried the Nvidia driver Ubuntu installed and the latest version from the nvidia site, no luck.

Also, there is no way to turn off tap to click on the touchpad, and a couple of times in firefox, I've had the cursor jump around while typing.

---

### Post by neven on 2010-07-28
...except booting to a live cd and disabling gdm.
Dugh can you pls explain me how can i disable gdm from live cd.
I have important data on my ubuntu 10.04 and after instaling nvidia drivers i get black screen on boot, i have asus n61 with optimus graphic, and i know i can't use nvidia on ubuntu.I just want to go back on previous state :(.

---

### Post by EL_Staso on 2010-07-29
No need to disable gdm. Just remove /etc/X11/xorg.conf and reboot.

---

### Post by neven on 2010-07-29
EL_Staso tnx for the tip but problem is that i can't access console when i boot, don't know why, when i choose to ener ubuntu next thing i see is loading, i tried every shortcut i could find but nothing is working :(

---

### Post by neven on 2010-07-30
I insert live cd->mount ubuntu->delete xorg.config, restart, and now its working again, tnx again EL_Staso, but now it look like it doesn't recognise intel hd graphic, effect is on None, and i can't change to Normal or Extra, when i try, ubuntu try to find drivers and only show nvidia, but i am not going that way again :D, i tried with reinstall xserver-xorg-video-install, but no effect :(

---

### Post by katrinaaa on 2010-07-30
It's a special topic for me , I get much useful information from it .thanks very much !

---

### Post by EL_Staso on 2010-07-31
> **neven said:**
> but now it look like it doesn't recognise intel hd graphic, 
You have to switch the graphic card in bios.

---

### Post by joshiausdemwald on 2010-08-04
Hi, 

as a ubuntu user - not hacker ;) - i'd appreciate any workaround or solution on this problem - Same here with a Asus N82J, Intel i5 and Nvidia GT 335 M with "super hybrid engine". 

Installing from hardware driver center - blank screen on startup
Installing proprietary drivers downloaded from the NVIDIA download siete - blank screen on startup

No way to switch to a bash promt (even in recovery mode), no output at VGA port.

---

### Post by EL_Staso on 2010-08-05
> **joshiausdemwald said:**
> Hi, 

as a ubuntu user - not hacker ;) - i'd appreciate any workaround or solution on this problem - Same here with a Asus N82J, Intel i5 and Nvidia GT 335 M with "super hybrid engine". 

Installing from hardware driver center - blank screen on startup
Installing proprietary drivers downloaded from the NVIDIA download siete - blank screen on startup

No way to switch to a bash promt (even in recovery mode), no output at VGA port.

Just switch the graphic card in bios.

---

### Post by ERFrizki on 2010-10-17
> **EL_Staso said:**
> Just switch the graphic card in bios.

unfortunately, I can't find any option to switch the graphic card in N82JV's bios.
i'm going all google to find options to switch off the nvidia graphic card (because it turns up the heat considerably here :( ) and stumbled upon the thread here and thankfully i haven't downloaded and install the proprietary drivers..

---

### Post by hobbystas on 2010-10-24
hi everybody.
I'm otherwise a pleased owner of an n61jv and stuck with the same problem. This bios switching possibility sounds very nice, but, in my bios ver. 208 there is no such available. The newest bios update is ver. 220 and there is no history file mentioning the changes available. Is there anybody who has tried out ver. 220 who could confirm if there is such an option available or if there is not? I'm realy curious and i have to admit, since a bios update is a very delicant procedure, i would not like do go through it for nothing.
Thanx in advance people.

---

### Post by cherrypie on 2010-10-26
well well well, sadly in 10.10 nothing changed, still no working drivers...

---

### Post by PopTart911 on 2010-10-31
There's a workaround for some people. I have the u43jc and you can use the 320m by installing the nvidia drivers, blacklisting the intel chip and rebooting. If you don't disable the intel chip, you'll get stuck on the Checking battery state... 

Only problem is that the 310 is the only one running and the battery gets slurped up pretty quick.

If it doesn't work, you can boot in safe graphics and reset everything.

I guess we'll just have to watch closely for updated nv drivers.:popcorn:

---

### Post by hobbystas on 2010-11-01
> **PopTart911 said:**
> There's a workaround for some people. I have the u43jc and you can use the 320m by installing the nvidia drivers, blacklisting the intel chip and rebooting. If you don't disable the intel chip, you'll get stuck on the Checking battery state... 

Only problem is that the 310 is the only one running and the battery gets slurped up pretty quick.

If it doesn't work, you can boot in safe graphics and reset everything.

I guess we'll just have to watch closely for updated nv drivers.:popcorn:

I tried this workaround some months ago but it didn't work on my n61jv with an nvidia gt 325m cuda enabled. According to nvidia, the gt 320m is not cuda enabled. Could it be that on cuda enabled  cards the workaround is more difficult or even impossible? Anybody has an answer to that maybe?

@ PopTart911, what version of bios are you running on and have you the option to disable the intel graphics through the bios?

---

### Post by avilella on 2010-11-02
> **PopTart911 said:**
> There's a workaround for some people. I have the u43jc and you can use the 320m by installing the nvidia drivers, blacklisting the intel chip and rebooting. If you don't disable the intel chip, you'll get stuck on the Checking battery state... 

Only problem is that the 310 is the only one running and the battery gets slurped up pretty quick.

If it doesn't work, you can boot in safe graphics and reset everything.

I guess we'll just have to watch closely for updated nv drivers.:popcorn:

Great to know, thanks for the info. How did you blacklist the intel chip?

---

### Post by Vermind on 2010-11-02
UL30VT: does not work.
I created a file called ```
/etc/modprobe.d/blacklist-intel.conf
``` and put there the text ```
blacklist i915
```. I installed nvidia drivers. i915 still gets loaded and I get to my desktop running with the intel driver after reboot, but the graphics are upside-down (using wrong libGL I guess).

However, if I go to the BIOS and change "SATA Mode" from "Enhanced" to "Compatibility" I can use NVIDIA and the intel card is not even visible in lspci. On the other hand this requires a reboot and changing the BIOS setting, so it is not optimal.

---

### Post by benjamimgois on 2010-11-05
> **Vermind said:**
> UL30VT: does not work.
I created a file called ```
/etc/modprobe.d/blacklist-intel.conf
``` and put there the text ```
blacklist i915
```. I installed nvidia drivers. i915 still gets loaded and I get to my desktop running with the intel driver after reboot, but the graphics are upside-down (using wrong libGL I guess).

However, if I go to the BIOS and change "SATA Mode" from "Enhanced" to "Compatibility" I can use NVIDIA and the intel card is not even visible in lspci. On the other hand this requires a reboot and changing the BIOS setting, so it is not optimal.

This solution works for an ATI RADEON FGLRX too ? I have exactly the same issue on my HP dv42080br and my BIOS has no option to disable the onboard core i5 graphics.

---

### Post by cherrypie on 2010-11-09
I heard that N71JV works well on Nouveau drivers. Any ideas how to install it ? Im still a newbie :(

---

### Post by Bijd3hand on 2010-12-10
> **cherrypie said:**
> I heard that N71JV works well on Nouveau drivers. Any ideas how to install it ? Im still a newbie :(
You could do it via the terminal, but I think it's of nu use.

Got also black screens..

I didn't know about the blacklist workaround, have spended the whole day trying to solve the blackscreen. Editing xorg.conf didn't work anymore, and resetting with sudo dpkg command not too..

Had to re-install the stuff :(

I think the blacklist workaround switches on your Nvidia chip, but then you don't use your Intel...

I like to be informed in this interesting subject :)

---

### Post by abeowitz on 2011-01-07
> **PopTart911 said:**
> There's a workaround for some people. I have the u43jc and you can use the 320m by installing the nvidia drivers, blacklisting the intel chip and rebooting. If you don't disable the intel chip, you'll get stuck on the Checking battery state... 

Only problem is that the 310 is the only one running and the battery gets slurped up pretty quick.

If it doesn't work, you can boot in safe graphics and reset everything.

I guess we'll just have to watch closely for updated nv drivers.:popcorn:

I tried this and got a blank screen.  Do you have more details?  Did you use Nouveau or the Nvidia proprietary drivers?  What's your xorg.conf look like?

Can you confirm that you're running Nvidia opengl libs?

Thanks.

---

### Post by PopTart911 on 2011-01-10
Newer kernel breaks my workaround. :( Ubuntu is running fine on the intel chip 4500mhd for now though.

Hope nvidia comes up with a real fix soon.

---

### Post by UpSignal on 2011-02-10
I got a new laptop: Asus K452JC , and i'm happy to see everything got fixed on ubuntu (except nvidia).
Sp, intel HD graphics are suiting my needs very well, i got compiz effects all working like a charm. I've created a partition and installed windows just to play World of Warcraft.
i'm gonna give a big party with lots of beer, in the day nvidia driver comes out :D
lol, you're all invited :p

---

### Post by cherrypie on 2011-03-16
oi mates, i found this : [http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html](http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html) anyone tried this ?

---

### Post by UpSignal on 2011-03-16
> **cherrypie said:**
> oi mates, i found this : [http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html](http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html) anyone tried this ?

Mate, if you have the "optimus" technology, which allows your OS to switch between graphic 2 cards for better battery saving/performance, it doesn't matter how you install nvidia, it simply won't work. We not only need a driver, but we also need a system that does the switch automatically. I pray everynight for the guys at noveau work it out eheheh. keep an eye o this:

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

At least if you have the optimus tech :)

---

