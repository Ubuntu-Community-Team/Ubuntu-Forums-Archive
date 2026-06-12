---
title: "Custom resolution not remembered after restart"
date: 2018-01-02
forum: Hardware
---

### Post by br4to92 on 2018-01-02
Hello guys, i have a problem regaring setting a custom resolution on my built-in display for my laptop. My desired resolution is 1600x900. It's not shown into Display settings in Ubuntu 16.04, but after running
sudo xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync and
sudo xrandr --addmode eDP-1 "1600x900_60.00"
the resolution is added to Displays settings and i can apply it. Also i put the 2 commands into .profile file ([COLOR=#333333][FONT=Monaco]gedit ~/.profile)[/FONT][/COLOR], at the end of the file, to supposedly remember the resolution after a restart, as this tutorial said ([http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)). The problem is it won't remain after a restart, I get an error ("Could not apply the stored configuration for monitors") and as i saw in another tutorial, i don't have the location [COLOR=#333333]/etc/gdm/Init/Default to put the commands in that startup script. What should i do? Thanks and have a nice day![/COLOR]

---

### Post by howefield on 2018-01-02
Thread moved to the "*Hardware*" forum.

---

### Post by br4to92 on 2018-01-03
[COLOR=#111111][FONT=Ubuntu]Problem solved. I have accidentally inserted the 'sudo' command in front of the two 'xrandr' commands, in the ~/.profile file. After removing them everything works. After restart the resolution remains the custom one. Have a nice day all![/FONT][/COLOR]

---

