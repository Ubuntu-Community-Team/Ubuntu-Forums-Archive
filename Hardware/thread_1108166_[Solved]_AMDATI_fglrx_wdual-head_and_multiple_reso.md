---
title: "[Solved] AMD/ATI fglrx w/dual-head and multiple resoultions"
date: 2009-03-27
forum: Hardware
---

### Post by mpiermar on 2009-03-27
I've been screwing w/my new AMD/ATI board (HD4850) for some time now (days) and was cursing myself for not going nvidia.  I finally figured out to get it into dual-head/bigDesktop mode using the latest catalyst 9.2 drivers.  I installed the latest drivers according this this wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

I have 2 LCD's attached to single HD4850 card.  Each monitor is a different size & resolution (22"@1680x1050, 19"@1280x1024).  I could not for the life of me get the big Destop to use the native resolutions of each monitor.  It always wanted either 3360x1050 or 2560x1024.   What I really wanted is 2960x1050, which uses the native resolution of each monitor.

I almost gave up when I did this:

```

aticonfig --add-pairmode=1680x1050+1280x1024

```

This added a new resolution to what the catalyst drivers think valid bigDesktop resolutions are: 

```

#aticonfig --list-pairmode
Get pair modes : 3
 0    1680x1050 + 1680x1050 --> 3360x1050 
 1    1280x1024 + 1280x1024 --> 2560x1024 
 2    1680x1050 + 1280x1024 --> 2960x1050 

```

Now, how to enable this resolution.  "amdcccle" now saw it in the list, but was not able to activate it.  On a hunch, I tried xrandr:

```

$xrandr
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 3360 x 1200
default connected 3360x1050+0+0 0mm x 0mm
   3360x1050      60.0*  
   2960x1050      60.0 
   2560x1024      60.0  
....

```

To enable the new resolution:
```

xrandr --output default --mode 2960x1050

$xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 3360 x 1200
default connected 2960x1050+0+0 0mm x 0mm
   3360x1050      60.0  
   2960x1050      60.0* 
   2560x1024      60.0  
   ...

```

I think you could also use gnome-display-properties to set the new resolution.

Anyway, hope this helps.  Now I'm trying to get the on-board HD3200 graphics chip working in cross-fire mode *AND* still have dual-head.  More wasted time.

Matt

machine specs:
AMD phenom quad core CPU
AMD 780g motherboard
Ubuntu 8.10 64bit
4gig ram
HD4850

---

### Post by markbuntu on 2009-03-27
Good luck with that.

I have a HD3300 on board and a HD3450 in a box. I am using a HD3650 but I would like to get the 3300 and 3450 in hybrid crossfire for one monitor and use the 3650 for another, all on a big desktop. I am sort of dreading the amount of work to get this set up on my 5 different distros... but if i ever do!!!

---

