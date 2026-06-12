---
title: "xrandr doesn't detect my VGA output"
date: 2008-09-10
forum: Hardware
---

### Post by josebama on 2008-09-10
Hello everybody, I have a laptop with a VGA output and when I want to toggle the screen (between laptop's screen and external screen) y use the X fronted nvidia-settings, and all works perfect. But I wan to change these with command-line because in this way I will can to make an script to do this change more easily, and after googling a little I founded the way with xrandr, but I do the command to change the screen and it doesn't take any effect, so I have looked the displays detected by xrandr and it only detects the laptop's screen.

More info:

when I do *xrandr -q*
it shows
```
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   700x525        55.0  
   640x512        56.0  
   640x480        57.0     58.0  
   640x400        59.0  
   640x384        60.0  
   512x384        61.0  
   400x300        62.0  
   320x240        63.0  

```

and it should appear the VGA too because I have it plugged.
I have googled a lot and I can't reach nothing useful, so I have decided to ask you.

My grafic card is an Nvidia Geforce 8400M and I use the nvidia-glx-new drivers from the ubuntu restricted repositorys

---

