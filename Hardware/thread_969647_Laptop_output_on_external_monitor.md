---
title: "Laptop output on external monitor"
date: 2008-11-03
forum: Hardware
---

### Post by asgharagha on 2008-11-03
Hi,

I have a laptop (Dell Latitude D630) inside a docking station plugged to a monitor (Dell E228WFP) using Ubuntu 8.10. If I switch on the PC I can see on both screens grub and the booting process. As soon as X get started and the GDM login screen shows up only the laptop screen has an output but not the monitor. After pressing FN+F8 key (toggle display) I can also see the login on the monitor but with the lower laptop resolution. Under "Screen resolution" there is no option for the desired resolution "1680x1050". Google gave me some hits about xrandr but I was not able to set the desired resolution. When at home I would like to only use the external monitor with the mentioned resolution and I don't use the laptop monitor.

Can you please give me some tips on how to achieve the needed screen output?

Thanks and regards,
Tom

---

### Post by crash0 on 2008-11-03
hi there, i had the same problem when i was running the livecd (not the permanent installation). unfortunately i forgot what exactly i did, but i know i added something like this to /etc/X11/xorg.conf:

Section "Monitor"
.......... -----> whatever goes into your monitor section

[B]SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection[/B]

EndSection ------> this is the closing tag refering for the monitor section...

(it's in the "Monitor" section). obviously depth is the color depth (8, 16, 24, 32), and "modes" refer to the resolutions you use. as i said, i don't know if this is the exact thing, i googled this, so it might not work. after you add it, restart xorg...

---

### Post by asgharagha on 2008-11-06
Hi,

I was not able to put this in "Monitor" section as X didn't start afterwards and gave some error messages. But I could put it in "Screen" section with the desired resolution "1680x1050" as "Modes". After restarting X I still didn't have any option under "Screen resolution" for the desired resolution.

Any help would be appreciated!

Tom

---

### Post by asgharagha on 2008-11-06
Hi,

I googled more and found out that I can use xrandr to add new modes. The output before modifications was:

```
tom@ubuntu:~$ xrandr 
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0  
   960x600        55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   800x600        59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   700x525        63.0  
   680x384        64.0     65.0  
   640x512        66.0  
   640x480        67.0     68.0  
   576x432        69.0  
   512x384        70.0  
   400x300        71.0  
   320x240        72.0
```

After the following lines it looked like
```
tom@ubuntu:~$ xrandr --newmode 1680x1050 147.14 1680 1784 1968 2256 1050 1051 1054 1087
tom@ubuntu:~$ xrandr --addmode default 1680x1050
tom@ubuntu:~$ xrandr 
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1680 x 1050
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0  
   960x600        55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   800x600        59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   700x525        63.0  
   680x384        64.0     65.0  
   640x512        66.0  
   640x480        67.0     68.0  
   576x432        69.0  
   512x384        70.0  
   400x300        71.0  
   320x240        72.0  
   1680x1050      60.0
```
But if I try to set this I get an error:

```
tom@ubuntu:~$ xrandr --output default --mode 1680x1050
tom@ubuntu:~$ xrandr: Configure crtc 0 failed
```

Any idea what going wrong here?

Tom

---

