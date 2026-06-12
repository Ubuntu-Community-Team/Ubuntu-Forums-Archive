---
title: "Brightness Control Messed Up"
date: 2009-04-25
forum: Hardware
---

### Post by pgn674 on 2009-04-25
I have a Lenovo 3000 C200 laptop. It has brightness controls, Fn+F10 and Fn+F11. In Ubuntu 8.10, they worked just fine and as expected. I just upgraded to 9.04 Jaunty Jackalope, and now they don't work right.

I get the brightness indicator box int he upper right when I use the buttons, and the brightness does go up and down, but incorrectly. Sometimes it goes up, and sometimes it goes down, but it never goes above the darkest 3 (out of probably 8). The indicator box does not always reflect the actual brightness. There seems to be some complex rules to determine if the actual brightness and the indicator go up or down, and by how much. It seems to depend on what I just hit, what I had hit the time before, and what the current brightness is, either in the indicator box or the actual brightness.

I have rebooted, and tried it with changing brightness before and after logging in, and before and after screensaver and sleep. My power management settings are set to not change the brightness. I looked around, but I didn't find any other people asking questions that seemed to fit my problem. So, anyone have any ideas?

---

### Post by Ozmodiar-X on 2009-04-26
I have almost the same problem on my acer aspire 6920. The hotkeys work fine, and I get the box saying it has changed brightness, but it doesn't actully change anything. The power management doesn't change it either. And thusly my battery life sucks. I need t find a way to fix this.

---

### Post by pgn674 on 2009-04-27
Oh yeah, my power management does work. I'm going to look into the video_brightnessup.sh thing, see if that might be doing it.

---

### Post by pgn674 on 2009-04-27
I just uninstalled acpi-support, and it's still doing the same thing. I need to find out what's catching my Fn+F10/Fn+F11 button presses.

---

### Post by LittleFoot on 2009-04-28
My brightness control hasn't worked at all from inside X since I upgraded to 8.10, I was hoping it would kick back in when 9.4 came out, but it didn't happen.  Figured out that I could change the brightness and contrast again by switching screens to an unlogged console via ctrl+alt+f1, using the hotkeys and then switching back to X.  It works but kind of a pain.

---

### Post by iTawm on 2009-04-29
I've been plagued by a similar problem on my Acer Aspire 5315.

Here's the thread I made detailing my issues: [http://ubuntuforums.org/showthread.php?p=7133174](http://ubuntuforums.org/showthread.php?p=7133174)


UPDATE:
I've found that gnome-power-manager is causing my problems. Disabling it under from starting on log-in under System -> Preferences -> Startup Applications works temporarily, but I lose all power-management tools.

---

### Post by pgn674 on 2009-04-29
Thank you, iTawm; that worked for me too. Before killing gnome-power-manager, I checked for the flashing you described, and I noticed I got it sometimes while using the brightness keys, and it always flashed when I opened the Power Management options window and when I slid the bar in there.

I found an alternative power manager: guidance-power-manager, in Synaptic Package Manager. There are probably other power managers out there, and this one is meant for KDE while I have Gnome, and there's no indication of the brightness level while using the brightness keys, but it's been working good for me so far. Oh, another thing: even when Gnome Power Manager was running, the Guidance Power Manager's brightness slider did not cause the screen to flash at all.

---

### Post by iTawm on 2009-04-29
Glad I could help, and thanks for suggesting an alternate power-manager :)
I'll probably try guidance-p-m out, doesn't bother me that it's KDE, as I already have a bunch of KDE libraries installed :)

---

### Post by pgn674 on 2009-05-08
Here's an update: I still have some problems.

Even though I took Gnome Power Manager out of Startup Applications, it still starts with Ubuntu every time. I guess I'll have to look through other startup methods to see if it's elsewhere, or see if I can find out what process is spawning it.

If I stop the gnome-power-manager process and just have Guidence Power Manager running, then my laptop doesn't sleep when I close the lid. I do have the "suspend when laptop lid closed" option checked in Guidance Power Manager. Maybe I'll try looking at other power managers.

---

### Post by iTawm on 2009-05-08
For some reason, VLC was starting gnome-p-m for me and messing up my brightness. So I uninstalled gnome-p-m, but with it gone, VLC just caused my system to freeze.
guidance doesn't allow me the control I'd like ie. it NEVER turns off my LCD's backlight, I have to use a python script that turns the backlight off when the screensaver launches.

---

### Post by pgn674 on 2009-05-14
Well, I did a bit of looking, and I found how to get Gnome Power Manager to tell you everything it's doing as you do it. Run gnome-power-manager --no-daemon --verbose. Here's what happens when I press increase brightness to go from the second lowest level to one up, and it goes down to the lowest level instead.```
TI:23:03:13	TH:0x8b6d640	FI:gpm-button.c	FN:hal_device_condition_cb,413
 - condition=ButtonPressed, details=brightness-up
TI:23:03:13	TH:0x8b6d640	FI:gpm-button.c	FN:gpm_button_emit_type,96
 - emitting button-pressed : brightness-up
TI:23:03:13	TH:0x8b6d640	FI:gpm-manager.c	FN:button_pressed_cb,1029
 - Button press event type=brightness-up
TI:23:03:13	TH:0x8b6d640	FI:gpm-srv-screensaver.c	FN:button_pressed_cb,167
 - Button press event type=brightness-up
TI:23:03:13	TH:0x8b6d640	FI:gpm-backlight.c	FN:gpm_backlight_button_pressed_cb,534
 - Button press event type=brightness-up
TI:23:03:13	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_screen,407
 - using resource 0x8cf5a68
TI:23:03:13	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 1 of 3
TI:23:03:13	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 2 of 3
TI:23:03:13	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_output_up,280
 - hard value=0, min=0, max=7
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 3 of 3
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_screen,407
 - using resource 0x8cf5a68
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 1 of 3
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 2 of 3
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_output_get_percentage,223
 - hard value=1, min=0, max=7
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_output_get_percentage,225
 - percentage 14
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_foreach_resource,368
 - resource 3 of 3
TI:23:03:14	TH:0x8b6d640	FI:gpm-feedback-widget.c	FN:gpm_feedback_display_value,169
 - Displaying 0.140000 on feedback widget
TI:23:03:14	TH:0x8b6d640	FI:gpm-backlight.c	FN:gpm_backlight_button_pressed_cb,549
 - emitting brightness-changed : 14
TI:23:03:14	TH:0x8b6d640	FI:gpm-info.c	FN:button_pressed_cb,679
 - Button press event type=brightness-up
TI:23:03:14	TH:0x8b6d640	FI:gpm-button.c	FN:gpm_button_filter_x_events,149
 - Key 233 mapped to key brightness-up
TI:23:03:14	TH:0x8b6d640	FI:gpm-button.c	FN:gpm_button_emit_type,92
 - ignoring duplicate button brightness-up
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_filter_xevents,545
 - Event0 0x8cf1c30
TI:23:03:14	TH:0x8b6d640	FI:gpm-brightness-xrandr.c	FN:gpm_brightness_xrandr_filter_xevents,545
 - Event0 0x8cf1c30
```Not really sure what it means; it seems to be mostly debug info special for the coders. But, I have work tomorrow morning, so I'll get back to it later.

---

