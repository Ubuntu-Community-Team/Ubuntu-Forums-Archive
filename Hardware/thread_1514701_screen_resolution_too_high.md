---
title: "screen resolution too high"
date: 2010-06-21
forum: Hardware
---

### Post by albertz on 2010-06-21
Hi,

After I installed the NVIDIA drivers, Xorg started at the next reboot with 1600x1200 -- which my monitor does not support.

How can I disable any resolution >= 1600x1200 ?

(That is Kubuntu 10.04 with xorg 1:7.5+5ubuntu1.)

Thanks,
Albert

---

### Post by diesch on 2010-06-21
Have a look at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Use *xrandr --delmode* to remove a mode from the set of valid modes for an output.

---

### Post by albertz on 2010-06-21
```
az@acompneu:~$ DISPLAY=:0 xrandr --rmmode 1600x1200
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  17 (RRDestroyMode)
  Serial number of failed request:  18
  Current serial number in output stream:  19
az@acompneu:~$ DISPLAY=:0 xrandr --delmode default 1600x1200
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  19 (RRDeleteOutputMode)
  Serial number of failed request:  18
  Current serial number in output stream:  19
az@acompneu:~$ DISPLAY=:0 sudo xrandr --delmode default 1600x1200
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  19 (RRDeleteOutputMode)
  Serial number of failed request:  18
  Current serial number in output stream:  19

```

Can't I just edit some config file and state that I want to disallow this resolution?

The wiki page doesn't really help -- it mostly say how I can edit that for the user. But of course I don't want to have that only for one user. I want to have it globally and esp. also at login.

---

### Post by albertz on 2010-06-21
Funny thing is:

```
az@acompneu:~$ DISPLAY=:0 sudo xrandr -s 1280x1024
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 14 requests (11 known processed) with 0 events remaining.

```

crashes the whole Xserver.

---

### Post by albertz on 2010-06-21
Earlier, I would have edited the xorg.conf. However, it seems that this file is mostly empty and obsolete these days and it detects everything automatically. I have seen that I can still set all resolutions manually there. However, I don't want to do that, I would like to have it automatically detected and only disable everything >=1600x1200. Or maybe it doesn't matter that much if it have those resolutions in the list if I can just get Xorg to automatically select 1280x1024 (or sth like that) and not just the highest resolution it found. How can I do that?

---

### Post by efflandt on 2010-06-22
What is the native resolution of your monitor and how is it connected (VGA, DVI, HDMI)?

What does just plain **xrandr** say?  Although, that may only work from a terminal in X and may not reveal anything from a text console if you cannot get X to work.

Sometimes when using a laptop or DVI (which can do VGA or DVI) the nVidia drivers mistakenly output to VGA instead of DVI, but that is usually if you get blank screen or no graphics at all in X.  If that is the case, you might try adding the following to the "Screen" section of /etc/X11/xorg.conf from recovery boot, then reboot:

Option "UseDisplayDevice" "DFP"

---

### Post by albertz on 2010-06-22
It doesn't have a native resolution. It's connected via VGA.

xrandr:
```
az@acompneu:~$ DISPLAY=:0 xrandr 
Screen 0: minimum 320 x 175, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      50.0*    51.0     52.0     53.0     54.0  
   1440x900       55.0  
   1400x1050      56.0     57.0     58.0     59.0  
   1360x768       60.0     61.0  
   1280x1024      62.0     63.0     64.0  
   1280x960       65.0     66.0  
   1152x864       67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   1024x768       74.0     75.0     76.0     77.0     78.0  
   960x600        79.0  
   960x540        80.0  
   840x525        81.0     82.0     83.0     84.0     85.0  
   832x624        86.0  
   800x600        87.0     88.0     89.0     90.0     91.0     92.0  
   720x450        93.0  
   720x400        94.0  
   700x525        95.0     96.0  
   680x384        97.0     98.0  
   640x480        99.0    100.0    101.0    102.0    103.0    104.0  
   640x400       105.0  
   640x350       106.0  
   512x384       107.0    108.0    109.0  
   400x300       110.0  
   320x240       111.0    112.0  
   320x175       113.0  
```

---

