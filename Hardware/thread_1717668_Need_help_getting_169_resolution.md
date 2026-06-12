---
title: "Need help getting 16:9 resolution"
date: 2011-03-30
forum: Hardware
---

### Post by Franklinscott57 on 2011-03-30
Hello,

I have a cyberpower laptop, on which I have installed Ubuntu 10 LTS.

My laptop's screen is a widescreen format that uses a display ratio of 16:9, however, that option is not available when I go to change screen resolutions.  I know that 16:9 is the right ratio, because I was using MintOS on the laptop earlier and that ratio is the only one that did not stretch or squish my images.  Unfourtanatly, MintOS did not support a few of my laptop's features (would only boot in low graphic mode) so I switched.

I have used previous versions of Ubuntu on my desktop, but have never had to configure anything, so I am extremely new to this.  I know it has something to do with my xorg.conf file, but I have no clue where to start.

The video card in my laptop is and intel integrated GFX PCIe card.  I do not know if I need to install any additional software enable for Ubuntu to support this card, or if I just need to reconfigure the xorg.conf file.

Currently, only three options are available for display, in 5:4 ratio and 4:3 ratio.  Everything is stretched on my screen.

Could anyone help me to add a 16:9 ratio to my system?

Thanks in advance for any help.

PS. Sorry if I sound like I don't know what I'm talking about... I don't.  This is all fairly new to me.

---

### Post by Franklinscott57 on 2011-03-31
Please ANYONE.

I'm not being lazy, I have checked all over the forums for a possible solution, but non of them seem to work for my laptop.

---

### Post by Cavsfan on 2011-03-31
Do you have an nVidia card? What is the native resolution?
This will display the possible resolutions and the top one should be native
**sudo xrandr -q**

---

### Post by Cavsfan on 2011-03-31
You can use that same command to change the resolution to what your monitor will support - the output of the first command.
If you wanted 1280 x 720 (16x9) for example you would enter:
**sudo xrandr -s 1280x720**

Just make sure you set it to whatever your monitor supports.
HTH

---

### Post by fuquam on 2011-09-15
I'm having the same problem but when I run the command I get "Size 1366x768 not found in available modes". I run Windows 7 as well and it uses 1366x768 screen resolution. Ubuntu won't let me change it.

---

### Post by Cavsfan on 2011-09-16
> **fuquam said:**
> I'm having the same problem but when I run the command I get "Size 1366x768 not found in available modes". I run Windows 7 as well and it uses 1366x768 screen resolution. Ubuntu won't let me change it.

Does **sudo xrandr -q** show 1366x768?

My output only lists 1360x768:```


cavsfan@cavsfan-desktop:~$ sudo xrandr -q
[sudo] password for cavsfan: 
Screen 0: minimum 320 x 175, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200      50.0* 
   1920x1080      51.0     52.0     53.0     54.0  
   1680x1050      55.0     56.0     57.0     58.0  
   1600x1200      59.0     60.0     61.0  
   1600x1024      62.0  
   1440x900       63.0  
   1440x480       64.0  
   1400x1050      65.0     66.0     67.0     68.0     69.0  
   1360x768       70.0     71.0  
   1280x1024      72.0     73.0     74.0  
   1280x960       75.0     76.0  
   1280x720       77.0     78.0  
   1152x864       79.0     80.0     81.0     82.0     83.0     84.0     85.0  
   1024x768       86.0     87.0     88.0     89.0     90.0     91.0     92.0  
   960x720        93.0     94.0     95.0  
   960x600        96.0  
   960x540        97.0  
   928x696        98.0     99.0  
   896x672       100.0    101.0  
   840x525       102.0    103.0    104.0    105.0    106.0  
   832x624       107.0  
   800x600       108.0    109.0    110.0    111.0    112.0    113.0    114.0    115.0    116.0    117.0  
   800x512       118.0  
   720x480       119.0    120.0  
   720x450       121.0  
   720x400       122.0  
   700x525       123.0    124.0    125.0    126.0  
   680x384       127.0    128.0  
   640x512       129.0    130.0    131.0  
   640x480       132.0    133.0    134.0    135.0    136.0    137.0    138.0    139.0  
   640x400       140.0  
   640x350       141.0  
   576x432       142.0    143.0    144.0    145.0    146.0    147.0    148.0  
   512x384       149.0    150.0    151.0    152.0    153.0  
   416x312       154.0  
   400x300       155.0    156.0    157.0    158.0    159.0  
   360x200       160.0  
   320x240       161.0    162.0    163.0    164.0  
   320x200       165.0  
   320x175       166.0  

```

I am far from an expert at this and my resolution has never changed nor have I ever attempted to change it.
My system has always picked my native resolution and refresh rate.

---

