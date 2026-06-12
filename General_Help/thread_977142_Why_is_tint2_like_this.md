---
title: "Why is tint2 like this?"
date: 2008-11-09
forum: General Help
---

### Post by cgrenier on 2008-11-09
My tint2 doesn't seem to be able to handle transparency at all, and instead displays these ugly white streaks. Why is this?  Attached is my tintrc and a screenshot.  I'm using compiz on a fresh Intrepid Ibex install.

```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_monitor
panel_monitor = 1
panel_position = bottom left
panel_size = 900 28
panel_margin = 1 0
panel_padding = 9 3
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 10
panel_border_width = 0
panel_background_color = #000000 70
panel_border_color = #ffffff 18

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 120
task_margin = 2
task_padding = 6
task_icon_size = 13
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 5
task_background_color = #ffffff 30
task_active_background_color = #ffffff 50
task_border_width = 0
task_border_color = #ffffff 18
task_active_border_color = #ffffff 70

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 76

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

```

---

### Post by ad_267 on 2008-11-09
Does it work if you set a background image?

---

### Post by cgrenier on 2008-11-09
Wow, that's strange.  It works fine now that I've set a background.  Thanks a lot.

---

### Post by ad_267 on 2008-11-09
Yeah I had this problem too, I never bothered to find out if it's supposed to do that. I guess you could set a blank png as the wallpaper if you want.

---

### Post by kowic on 2008-11-25
I had another problem, my tint appears as window (with decorations and stuff). Any suggestions how to fixed this?

thanks in advance guys

I attached a screenshot

---

### Post by ad_267 on 2008-11-25
> **kowic said:**
> I had another problem, my tint appears as window (with decorations and stuff). Any suggestions how to fixed this?

thanks in advance guys

I attached a screenshot

What window manager are you using? Openbox?

---

### Post by kowic on 2008-11-25
I use xfce (managing desktop) with compiz (managing windows, composite eff. and stuff)

---

### Post by COLiNx86 on 2008-11-25
> **kowic said:**
> I use xfce (managing desktop) with compiz (managing windows, composite eff. and stuff)
Go into CompizConfig Settings Manager (if it's not installed go into synaptic and install CompizConfig Settings Manager). Go into the Window Decoration plugin settings and in the box that says Decoration Windows put ```
any & !type=dock
```

---

### Post by kowic on 2008-11-26
Worked perfectly, thanks a lot COLiNx86 :D

---

### Post by hofa on 2009-01-04
I just came across a problem: My tint2 taskbar doesn't want to stay docked at the lower border of my screen. (I just installed it)

At startup it does, but once I click in the area, it goes up about 30 or 40 pixels. I really don't know what could be doing this.

ps: I'm using Ubuntu 8.04 (still gnome) with Compiz


edit: I just put back a gnome panel and it looks like tint tries to evade the space that the gnome-panel would be using.

---

