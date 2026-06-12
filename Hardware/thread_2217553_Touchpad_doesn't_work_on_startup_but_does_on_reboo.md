---
title: "Touchpad doesn't work on startup but does on reboot"
date: 2014-04-17
forum: Hardware
---

### Post by stevebag on 2014-04-17
I have a Lenovo Thinkpad Twist.  This problem began while running 13.10, I tried to resolve it on my own, then decided to wait and see if an upgrade to 14.04 would solve it.  It didn't.

When I initially boot up, the cursor appears on the login screen, doesn't function, then disappears upon login. I have no touchpad functions whatsoever. When I restart the computer, the touchpad works fine. One of the screenshots is startup, other is reboot.
 [ATTACH=CONFIG]252152[/ATTACH][ATTACH=CONFIG]252153[/ATTACH]

If I run System Settings>Mouse and Touchpad there are no Touchpad options that appear. They are simply missing.  
If I run dconf, all the right options do appear and are checked.
If I run synclient TouchpadOff=0 in terminal I get the response:  couldn't find synaptics properties. No synaptics driver loaded?

It isn't a big deal because I can get the touchpad to run perfectly upon restart, but it is an irritation.

Any ideas/help greatly appreciated.

---

### Post by stevebag on 2014-04-18
It seems to me that it could be a simple fix:  is there a different script for startup and restart?  If I could compare those files would that give me a clue?  If the drivers not being loaded properly on startup could I write a script that would load the synaptics driver?

---

### Post by stevebag on 2014-04-21
This post was made on Ask Ubuntu in October with the same problem

[http://askubuntu.com/questions/354305/mouse-and-keyboard-dont-work-from-shutdown-do-work-from-restart](http://askubuntu.com/questions/354305/mouse-and-keyboard-dont-work-from-shutdown-do-work-from-restart)

as well as this one on the forums from back in September.  

[http://ubuntuforums.org/showthread.php?t=2177295](http://ubuntuforums.org/showthread.php?t=2177295).

Any ideas?

---

### Post by vincent_lin3 on 2014-05-04
Did a google search on linux mint instead, and came up with this:

[http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402](http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402)


It works on my ThinkPad Twist with i5.  I hope it works on yours.

Vincent

---

### Post by stevebag on 2014-05-13
Vincent!!!

Thanks, that works. 

Amazing that such a small thing can bring such great happiness.

Again here is the link:  [http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402](http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402)

Here is the solution:

1. Run the following command in terminal:
sudo gedit /etc/default/grub

2. The GRUB configuration file should open. Locate the following line:
GRUB_CMDLINE_LINUX=" "

3. Add this into the parameters:
i8042.nomux=1 locale=fr_FR i8042.reset

4. The final line should look like this:
GRUB_CMDLINE_LINUX="i8042.nomux=1 locale=fr_FR i8042.reset"

5. Save the file and exit gedit.

6. Run the following command in terminal:
sudo update-grub

7. Let the grub.conf file get recreated, and then restart.

---

