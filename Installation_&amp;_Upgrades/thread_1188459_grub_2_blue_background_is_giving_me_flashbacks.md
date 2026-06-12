---
title: "grub 2 blue background is giving me flashbacks"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2009-06-15
My new grub 2 start up menu is blue and it is giving me flashbacks of Vista Blue screens of death! Can someone please tell me how to change the color?

---

### Post by brncao on 2009-06-15
This info is stored in the menu.lst file in /boot/grub/ directory. I forgot what line it was but a simple google search should get you the answer. You can even upload your own background if you wanted to (needs to be in a specific format).

---

### Post by lindsay7 on 2009-06-17
Thanks, but I need help with grub2. I can not find any info on how to change the startup menu color anywhere for grub2.

---

### Post by mrtomservo on 2009-06-22
Hello!  I'm playing around with GRUB 2 myself.  It's funny, the blue reminds me of my old Debian install.  Anyway, this is what i've learned so far:  There's no more /boot/grub/menu.lst.  It should be /boot/grub/grub.cfg.  BUT, you can't edit that either.  It's generated from a series of script files located in /etc/grub.d/.   You will find several files much like in /etc/init.d/ with numbers preceding the script title indicating the order of it's final placement in your /boot/grub/grub.cfg.  Make a backup of the file you intend to edit in another directory (home? desktop?).  The file you want is /etc/grub.d/05_debian_theme.  Once you finish editing it, make sure to run "sudo update-grub", if that runs ok, check your /boot/grub/grub.cfg to see if it includes your changes just to be sure.

Oh yeah, a few other settings can be found in /etc/default/grub.

Hope that helps! :)

---

### Post by running_rabbit07 on 2009-06-22
Go to your Synaptic Package Manager and install StartUp-Manager. After installed, when you open it, one of the tabs allows you to change or remove startup/grub background colors.

---

### Post by lindsay7 on 2009-06-22
Well, I found out how to change the screen to a picture but not change the color, which is fine with me. I just did not like the similarity to the BSOD.

Here is the info and link, Note I used gedit and not nano to edit the file.


[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)


TO:  Running_Rabbit 07,

Part of this problem is that when you install grub2 the Startup- Manager menu changes and there is no option to change anything i.e. colors.

---

### Post by merlinus on 2009-06-22
Maybe this will help:

To change the colors in GRUB2 you would specify one option in [COLOR=#005500][FONT=monospace]/boot/grub/grub.cfg[/FONT][/COLOR]: 
 color light-blue/black light-cyan/blue
These are the default colors for Arch's release of GRUB-legacy. The available colors for GRUB2 are at [http://www.gnu.org/software/grub/manual/html_node/color.html](http://www.gnu.org/software/grub/manual/html_node/color.html)

---

