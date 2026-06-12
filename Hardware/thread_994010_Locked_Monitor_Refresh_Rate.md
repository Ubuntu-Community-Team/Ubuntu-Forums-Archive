---
title: "Locked Monitor Refresh Rate"
date: 2008-11-26
forum: Hardware
---

### Post by euphonism on 2008-11-26
Under Screen Resolution settings found in System Preferences there are two listed refresh rates: 50Hz and 51Hz.

Running xrandr -q gives the following output:

```
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0     51.0* 
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   700x525        76.0     77.0     78.0  
   680x384        79.0     80.0  
   640x512        81.0     82.0  
   640x480        83.0     84.0     85.0     86.0  
   640x400        87.0  
   576x432        88.0     89.0     90.0     91.0  
   512x384        92.0     93.0     94.0  
   416x312        95.0  
   400x300        96.0     97.0     98.0     99.0  
   320x240       100.0    101.0    102.0
```  

However, when I run "sudo nvidia-settings" from terminal my refresh rate is listed at 75Hz under the X Server Display Configuration tab. Under this tab there is also an option to merge display settings with xorg.conf, which I have done. I've also tried entering a custom modeline generated with gtf but xrandr and Screen Resolution still report 50Hz and 51Hz. Do I trust that my refresh rate is at 75Hz as reported by nvidia-settings or does xrandr give me the accurate output?

---

### Post by euphonism on 2008-11-28
Bump

---

