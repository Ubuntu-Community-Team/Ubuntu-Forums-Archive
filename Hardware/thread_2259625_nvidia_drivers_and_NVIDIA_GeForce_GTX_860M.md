---
title: "nvidia drivers and NVIDIA GeForce GTX 860M"
date: 2015-01-05
forum: Hardware
---

### Post by JDAIII on 2015-01-05
This is going to be a short story of how I tried commiting suicide with a plastic spork from FKC after trying to get nvidia drivers to work on my new laptop.

I did crosspost this on another external forum which is specific to the 30 people in the world who have my laptop and are trying to install linux on it. None of them use UbuntuGnome so......

I have a lenovo Y50 4K I installed Ubuntu Gnome 14.04.1. My laptop has the NVIDIA GeForce GTX 860M 2GB video card.

I also noticed a few other issues that maybe folks here who have a 4k laptop on ubuntugnome may have fixes for.

1. chrome on my 4k screen is not usable. The address bar is soooooo  tiny, I need a loupe to read it. sign of awesome resolution though.
2. when I connect my 27" 1080 monitor, the res on that monitor is  horrid. I tried using the xrandr command here, but I get an issue with  mouse constraints and using the panning option with --panning 1920x1080  or --panning 3840x2160 causes even worse issues.
        xrandr --output eDP1 --auto --output HDMI1 --auto --scale 2x2 --right-of eDP1
3. randomly (I haven't found the cause yet) my screen resolution will  just go wrong and I lose mouse and keyboard input. I'll look for better  details, but want to know if anyone else has the same issue. Only happened 3 times in two days using it 12 hours a day.

Specific issues with driver installtion:
-NVIDIA driver:
I tried downloading the nvidia drivers (.run file) from the nvidia website here: [http://www.nvidia.com/download/driverresults.aspx/74888/en-us](http://www.nvidia.com/download/driverresults.aspx/74888/en-us)
I followed the directions that I found which are ctrl-alt-F2, then kill lightdm (gdm for me) then install as root, and reboot
This installed, then would never boot a gui. I reformatted since I just got the laptop and I didn't know how to remove those drivers

-driver nvidia-340 from ppa:xorg-edgers/ppa
added the ppa, updated, then installed. 
Rebooted, then,
Good news is that the nvidia drivers saw both intel integrated graphics  and the nvidia graphics so I'm guessing that this will somehow be  possible to configure.
1. The screens switched places and the secondary monitor now had the top and bottom bars
2. I tried running nvidia settings application in order to change the settings
2a. application loaded on 4k monitor with 4k resolution, and would not allow mouse or keyboard back on the other monitor.
3. nvidia settings crashed when I selected 'detect monitors' -repeatedly -even after reboots
4. monitors were showing as a single monitor 'X Server'
5. tried editing xorg.conf to add a second monitor, but not too familiar so it failed probably because of my own fault
There were a lot of issues, these were the ones that made it completely  unusable. I uninstalled and rebooted and went back to where I started.
I kept a copy of the xorg.conf in case it's relevant.

Other options:
I have seen a few autobat named drivers, optimus (my machine uses switchable and not optimus), bumblebee, and another that I can't remember. Are these an option? 
Should I go back to the nvidia from ppa and manipulate the xorg? 

Links:
In case it matters.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834317540](http://www.newegg.com/Product/Product.aspx?Item=N82E16834317540)

---

### Post by JDAIII on 2015-01-06
So I tried the nvidia-343 from the ppa and had the same issue, although this time I did not lose keyboard and mouse control.

Anyone recommend bumblebee or optimus? My laptop uses nvidia switchable and not nvidia optimus, but the drivers have been said to work. Just like doing research before trying things like that.

---

