---
title: "[SOLVED] install tint2 but i have a problem."
date: 2008-07-23
forum: General Help
---

### Post by raskolnikov_kr on 2008-07-23
Using Ubuntu 8.04, Gnome 2.22.2, Compiz, emerald.
install tint2 from google.
and run tint2, look emerald border on tint.

please [http://campusnote.co.kr/cap/tintborder.png](http://campusnote.co.kr/cap/tintborder.png)

how to remove only tint's emerald border?
or any solutions..
please help me.

Thanks for read.


.tintrc
> tintrc :
```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_desktop
panel_monitor = 1
panel_position = bottom left
panel_size = 900 34
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
task_margin = 5
task_padding = 3
task_icon_size = 0
task_font = NeutraTextLightSCAlt Bold 7.5
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
time1_font = sans bold 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

---

### Post by Fufkin on 2008-07-24
I have the same problem

---

### Post by raskolnikov_kr on 2008-07-24
> **Fufkin said:**
> I have the same problem

hi!

you have any solution?

i keep finding..but no infomations...:confused:

---

### Post by thil77 on 2008-07-24
hi,

have found this post, but can't try
"To prevent compiz giving tint emerald's borders - open compizconfig settings manager, go to Window Decoration plugin and type
any & !type=dock
into Decoration Windows box."

---

### Post by raskolnikov_kr on 2008-07-24
> **thil77 said:**
> hi,

have found this post, but can't try
"To prevent compiz giving tint emerald's borders - open compizconfig settings manager, go to Window Decoration plugin and type
any & !type=dock
into Decoration Windows box."

oh!! wow @!
Thank you very much!!
i do it. very nice working!
Thank you :D 

solved screens shot : [http://campusnote.co.kr/cap/thankyou.png](http://campusnote.co.kr/cap/thankyou.png)

---

### Post by Fufkin on 2008-07-25
> **thil77 said:**
> hi,

have found this post, but can't try
"To prevent compiz giving tint emerald's borders - open compizconfig settings manager, go to Window Decoration plugin and type
any & !type=dock
into Decoration Windows box."

Thank you!

Worked for me too :)

---

### Post by markitoxs on 2008-11-29
Worked for me as well, thank you.

---

