---
title: "Dual monitors, one switched to a lower resolution yesterday, 12/16/2015"
date: 2015-12-17
forum: Hardware
---

### Post by handydoug on 2015-12-17
I have a triple boot system(Vista, Ubuntu  14.04, Linux Lite 2.6) on a Gateway desktop GT5412 with two hard drives, two monitors. Vista works fine, Ubuntu,  Linux Lite do not. The monitors are same size, have had the same  resolution (1920x1080) for weeks until yesterday, 12/16/2015. One has 1920x1080, the  other has dropped to 1024x768. Video card is MSI GT 720. Does anyone  have a solution, please?

---

### Post by TheFu on 2015-12-18
xrandr, lxrandr, arandr?
Pick one, I'd start iwth **lxrandr**, it is the easiest.

---

### Post by handydoug on 2015-12-19
Thank you for the quick response. I opened up the Lite Control Center on the Linux Lite OS and found the display settings with the 1920x1080 option and that fixed the problem.
The other options for changing the resolution, Nvidia X Server settings and the display options in settings would not give me the 1920x1080 resolution option. 
Update:The fix lasted a day, now one monitor is back to the lower resolution. I will try your suggestion and let you know.

---

### Post by handydoug on 2015-12-20
I tried lxrandr, the 1920x1080 resolution option was not available. Here's the output of xrandr:
doug@doug-GT5412:~$ xrandr
Screen 0: minimum 8 x 8, current 2944 x 1080, maximum 16384 x 16384
VGA-0 connected primary 1024x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-D-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+   50.0  
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0     50.0  
   1152x864       75.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
doug@doug-GT5412:~$ 
Any ideas?
Thanks

---

### Post by TheFu on 2015-12-20
1920x1080 60.0*+ 50.0 is being used for the DVI connection.
If you want to override the VGA (which can be dangerous if the monitor doesn't support a higher resolution), then you can modify the xorg.conf file manually. It really shouldn't be required, but the X/Windows probes aren't able to determine the monitor capabilities, so not much choice. I suppose.  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) explains.

---

### Post by handydoug on 2015-12-20
The monitors are same size, same resolution, and displayed the same resolution (1920x1080) for weeks until 12/16/2015. Now one has 1920x1080, the other has now dropped to 1024x768. I did not manually change the resolution. The day before the monitors were working perfectly, the next day, they're not. They both support 1920x1080 resolution.

---

### Post by handydoug on 2015-12-20
Is there any way to find out what happened to change the resolution on the second monitor?

---

### Post by TheFu on 2015-12-20
> **handydoug said:**
> Is there any way to find out what happened to change the resolution on the second monitor?

Sure.  Compare the files that changed from a few weeks ago with the day you noticed the changes. Good backups will support that. 

What backup tool(s) do you use? 
Are 30-60 days of versioned backups retained?  If you don't have backups, the options are much more limited. 

Suppose you could look through all the files that changed in the last week. **find** can provide a list:
```
$ find / -mtime -7 -type f
```
I'd probably limit it to the /etc directory:
```
$ find /etc -mtime -7 -type f
```
Not all files are readable in /etc, so use sudo.
```
$ sudo find /etc -mtime -7 -type f
/etc/apt/apt.conf.d/01autoremove-kernels
/etc/cups/printers.conf.O
/etc/cups/printers.conf
/etc/apparmor.d/cache/usr.sbin.cups-browsed
/etc/apparmor.d/cache/usr.sbin.cupsd
/etc/mtab
/etc/ld.so.cache
/etc/mailcap

```
Nothing very interesting there related to X/Windows.  
Perhaps 2 weeks?  Nope.  Just some NTP stuff added.  I ran: sudo find /etc -mtime -14 -type f
3 weeks?  Nope. Nothing new.  
I don't have the same graphics hardware you do, actually my "desktop" isn't really a physical machine. It runs in a private cloud virtual machine. The chromebook I use normally to access it is being repaired, so I'm slumming on an old Win7 box using an x2go remote desktop on dual monitors, but even from the chromebook, I'd be using x2go into the same virtual machine. My display sizes change all the time (1366x768 or 1920x1200 or 1920x1080), so I'm pretty familiar with lxrandr.

Sorry, this probably doesn't help much.

---

### Post by handydoug on 2016-03-06
Thanks for your help, TheFu. I stopped trying to find out what happened and used this information: 
[http://askubuntu.com/questions/100900/how-do-i-set-the-correct-monitor-resolution-with-nvidia-drivers-for-a-monitor-th](http://askubuntu.com/questions/100900/how-do-i-set-the-correct-monitor-resolution-with-nvidia-drivers-for-a-monitor-th)
I has been working for about a week now, the resolution has remained at the highest resolution even after rebooting.
IIRC, I only did steps 4-11 and that was successful.

---

### Post by handydoug on 2016-03-07
Thanks for your help.

---

