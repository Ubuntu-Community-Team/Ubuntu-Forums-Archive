---
title: "Script to switch monitors"
date: 2009-10-20
forum: Hardware
---

### Post by biozenunity on 2009-10-20
I have a laptop with a Nvidia video card and I would like to be able to plug in my external monitor and automaticly have nvidia-settings set that monitor to default and disable the laptop screen. Or at the very least have a script to do it rather than doing it manualy as I switch monitors at least a half dozen times a day. How would I go about doing this?

---

### Post by scragar on 2009-10-20
For now can you post the output of```
xrandr -q
```Both with and without the external montor connected?

---

### Post by biozenunity on 2009-10-21
Without external monitor
> biozen@labtop-jaunty:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1440 x 900
default connected 1280x800+0+0 0mm x 0mm
   1440x900       50.0     51.0     87.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0  
   720x450        72.0  
   700x525        73.0     74.0  
   680x384        75.0     76.0  
   640x480        77.0     78.0     79.0     80.0     81.0  
   512x384        82.0     83.0  
   400x300        84.0  
   320x240        85.0     86.0  
   1280x800       87.0     51.0* 
biozen@labtop-jaunty:~$ With external monitor
> biozen@labtop-jaunty:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0     87.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0  
   720x450        72.0  
   700x525        73.0     74.0  
   680x384        75.0     76.0  
   640x480        77.0     78.0     79.0     80.0     81.0  
   512x384        82.0     83.0  
   400x300        84.0  
   320x240        85.0     86.0  
   1280x800       87.0     51.0  
biozen@labtop-jaunty:~$ 

---

### Post by biozenunity on 2009-10-31
Bump

---

