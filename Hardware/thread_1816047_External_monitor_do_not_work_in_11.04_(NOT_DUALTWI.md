---
title: "External monitor do not work in 11.04 (NOT DUAL/TWIN!!!)"
date: 2011-08-01
forum: Hardware
---

### Post by Longshankss on 2011-08-01
Please, if you suffer from the same problem, please do not make entries saying; me too or i have the problem. Doesn't help one bit, just makes navigating for a solution that much more difficult.

Nvidia geforce 8600m gt 512 mb dedicated.
driver version current.
tried 173 and experimental

Since the upgrade to 11.04 I cannot get my flatscreen connected properly, or at all as a matter of fact. I have tried the native monitors app, and my nvidia settings app. None of them worked....
The native monitor app doesn't even locate my screen, the nvidia does, but nothing happens. I tried the fn/f4 button-combo, nothing. I tried to update the kernel to 2.6.39, alas no result. I have read about the "xrandr-fix", but do not quite know how it works, or what it might corrupt. Have also tried restarting into gnome.... I actually like the unity, so please, unless u have a way to install gnome 3, that actually works, I WANT to make it work in unity.

Please let me know if you might have a solution, as I am really sick and tired of constantly reinstalling. 
And please, when/if helping, have in mind, that I know NOTHING about computers. Everything has to be put in a step by step explanation, as well as the means to undo eventual damage. Even the simplest thing, you will have to spell out. Slowly.
Bitching aside, I would really appreciate any help to this simple, yet difficult problem.

---

### Post by ipodless on 2011-08-01
> **Longshankss said:**
> Please, if you suffer from the same problem, please do not make entries saying; me too or i have the problem. Doesn't help one bit, just makes navigating for a solution that much more difficult.

Nvidia geforce 8600m gt 512 mb dedicated.
driver version current.
tried 173 and experimental

Since the upgrade to 11.04 I cannot get my flatscreen connected properly, or at all as a matter of fact. I have tried the native monitors app, and my nvidia settings app. None of them worked....
The native monitor app doesn't even locate my screen, the nvidia does, but nothing happens. I tried the fn/f4 button-combo, nothing. I tried to update the kernel to 2.6.39, alas no result. I have read about the "xrandr-fix", but do not quite know how it works, or what it might corrupt. Have also tried restarting into gnome.... I actually like the unity, so please, unless u have a way to install gnome 3, that actually works, I WANT to make it work in unity.

Please let me know if you might have a solution, as I am really sick and tired of constantly reinstalling. 
And please, when/if helping, have in mind, that I know NOTHING about computers. Everything has to be put in a step by step explanation, as well as the means to undo eventual damage. Even the simplest thing, you will have to spell out. Slowly.
Bitching aside, I would really appreciate any help to this simple, yet difficult problem.

Hey Longshankss,

Please bear with me as I'm new to the forums and this is my first post.

What's the output of xrandr in the Terminal?

---

### Post by Longshankss on 2011-08-02
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0*    51.0  
   1600x1024      52.0  
   1440x900       53.0  
   1360x768       54.0     55.0  
   1280x1024      56.0  
   1280x960       57.0  
   1152x864       58.0     59.0     60.0     61.0  
   1024x768       62.0     63.0     64.0     65.0     66.0  
   960x720        67.0  
   960x600        68.0  
   960x540        69.0  
   928x696        70.0  
   896x672        71.0  
   840x525        72.0     73.0     74.0     75.0     76.0  
   832x624        77.0  
   800x600        78.0     79.0     80.0     81.0     82.0     83.0     84.0     85.0     86.0     87.0  
   800x512        88.0  
   720x450        89.0  
   720x400        90.0  
   700x525        91.0     92.0     93.0     94.0  
   680x384        95.0     96.0  
   640x512        97.0     98.0     99.0  
   640x480       100.0    101.0    102.0    103.0    104.0    105.0  
   640x400       106.0  
   640x350       107.0  
   576x432       108.0    109.0    110.0    111.0    112.0    113.0    114.0  
   512x384       115.0    116.0    117.0    118.0    119.0  
   416x312       120.0  
   400x300       121.0    122.0    123.0    124.0    125.0  
   360x200       126.0  
   320x240       127.0    128.0    129.0    130.0  
   320x200       131.0  
   320x175       132.0

---

### Post by ipodless on 2011-08-03
Sorry about the delay in responding to you. I was trying to look into this to no avail.
 
Bumping for interest in hopes that someone else can help.

---

### Post by Longshankss on 2011-08-04
no problem :) I am patient :)

---

