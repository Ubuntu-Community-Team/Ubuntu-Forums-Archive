---
title: "xauthority problem with fglrx power management script"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by heng on 2006-11-29
I am trying to get my ATI card to go into low power mode when on the battery.

I have got the fglrx-powermode.sh script to execute, but at the line:

su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode" &>/dev/null

I get no output. Now, i can confirm that $XAUTHORITY has been set to point to  /home/hen/.Xauthority, however, if i redirect the output from the command, I get:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Unable to open display `:0'.

I can execute the command by hand at the command line and it works fine (changing the powerstate correctly).

$user returns hen correctly in the script, and $powermode is set to the correct value.

I hope someone can see the problem.

---

### Post by leogibson on 2006-12-05
I'm having a similar problem, i used tseliot's HOWTO/TEST ATI DRIVERS post to install fglrx, but i want the powersave mode both with and without battery installed...how do i configure aticonfig to do this??  i have an x700 radeon on a laptop that tends to run very hot, and even in AC power, its too hot.  rather than take it all apart and add Artic silver to the x700 chip itself, what can i do?

leo

---

### Post by onaka_the_kaka on 2006-12-09
I can see your problem. I've been trying to set up the same sort of script as you. What works is opening a command-prompt and typing:

xhost +local:

Then you will be able to run the script. To make this run at boot-time you are supposed to add the line:

local:

to the file /etc/X0.hosts, unfortunately this doesn't seem to work for me.

It's probably also possible to fix this using xauth although I haven't figured how and therefore I simply opened in the gnome-menu: 
Gnome-Toolbar->System->Preferences->Sessions->Startup Programs-> and added

xhost+local:

If someone figured out a better solution we might be able to put this on a wiki-page.

---

