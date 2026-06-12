---
title: "Problems with tint"
date: 2008-07-31
forum: General Help
---

### Post by Tuning_In on 2008-07-31
Hi!

I have installed tint following [this guide]("http://ubuntuforums.org/showpost.php?p=5431755&postcount=74").

My problem is that the panel is moving up when pressing tasks (see picture)
Im not sure, but I think it has someting to do with my screen resolution. But I dont know. My resolution is 1680x1050.

Also, I dont get any error when running "tint" from the terminal 

Here is my tintrc
```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_desktop
panel_monitor = 1
panel_position = bottom center
panel_size = 1100 34
panel_margin = 0 0
panel_padding = 5 5
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 9
panel_border_width = 2
panel_background_color = #000000 0
panel_border_color = #000000 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 200
task_margin = 2
task_padding = 2
task_icon_size = 0
task_font = Calibri bold 8
task_font_color = #ffffff 59
task_active_font_color = #ffffff 90

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 3
task_background_color = #000000 40
task_active_background_color = #000000 55
task_border_width = 1
task_border_color = #d1d1d1 34
task_active_border_color = #d1d1d1 40

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = Calibri bold 8
#time2_format = %A %d %B
time2_font = Calibri bold 6
clock_font_color = #ffffff 90

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

Got any ideas?

---

### Post by thil77 on 2008-08-01
hi,

can you send the result on command
xrandr -q

and check if you have margin in xfce config.

does the panel move up on each clic ?
or is it just on the first clic ?

---

### Post by Tuning_In on 2008-08-01
Hi:) 

This is the output of  xrandr -q:

```
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0* 
   1600x1024      51.0  
   1440x900       52.0  
   1400x1050      53.0  
   1280x1024      54.0     55.0  
   1280x960       56.0  
   1280x800       57.0     1280x768       58.0  
   1152x864       59.0  
   1024x768       60.0     61.0     62.0  
   960x600        63.0  
   840x525        64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0  
   800x512        72.0  
   720x450        73.0  
   640x512        74.0     75.0  
   640x480        76.0     77.0     78.0     79.0  
   640x400        80.0  
   640x384        81.0  
   576x432        82.0  
   512x384        83.0     84.0     85.0  
   416x312        86.0  
   400x300        87.0     88.0     89.0     90.0  
   320x240        91.0     92.0     93.0  
```

The panel moves up on each clic.

```
and check if you have margin in xfce config.

```
Maybe this is a really dumb question, but wich xfce config are you thinking of? The files in /home/sjur/.config/xfce4? Or something else?

Thank you very much for your time and help:)

---

### Post by thil77 on 2008-08-02
Hi Tuning_In,

have not enougth time this week end, but added a bug report on
[http://code.google.com/p/tint2/issues/detail?id=15](http://code.google.com/p/tint2/issues/detail?id=15)

hope to have a look at it next week.

---

### Post by Tuning_In on 2008-08-02
Thanks:)

---

### Post by victorb on 2008-08-04
Hi,

I have the same problem with the panel moving up (only on the first click though) on my gnome desktop w/ compiz. If i switch to metacity, then the problem disappears.

Hope this will help isolating the problem.

---

### Post by raskolnikov_kr on 2008-08-09
I found a solution, but not perfect.
I using compiz 0.7.4 + gnome 2.22.3

```
1. open compizconfig-setting-manager
2. off "Place Windows"

```

I think this problems is connection with compiz.
somebody better have a better solutions?

---

### Post by Beth1957 on 2008-08-15
> **raskolnikov_kr said:**
> I found a solution, but not perfect.
I using compiz 0.7.4 + gnome 2.22.3

```
1. open compizconfig-setting-manager
2. off "Place Windows"

```

I think this problems is connection with compiz.
somebody better have a better solutions?

I'm gaving similar "jumping windows" problems with contact cards in Evolution and with Emerald & even Advanced Desktop Effects Settings (strangely!). 
I tried switching off "place Windows" but although this solved the issue with Evolution, it had no effect on either Emerald or Advanced Desktop Effects Settings.
I've come up with my own rather clumsy workround involving compiz-switch in [this thread]("http://ubuntuforums.org/showthread.php?t=883577").

---

