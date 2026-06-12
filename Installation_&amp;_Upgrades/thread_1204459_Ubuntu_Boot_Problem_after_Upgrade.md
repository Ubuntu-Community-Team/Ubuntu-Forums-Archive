---
title: "Ubuntu Boot Problem after Upgrade"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by robertqadkins on 2009-07-04
I installed Ubuntu 9.04 and installed the upgrades. I have restarted the computer and ubuntu had worked fine. I then installed wine, restarted, and booted up no problem. I then tried installing XGL/Compiz. Now when I boot up my computer, Ubuntu is listed twice in grub. I have tried booting both versions and they both boot up past the ubuntu loading screen, the monitor flashes some weird patterns about 3 time and then freezes on the fourth time. I would really like to get this fixed because i don't have hsi and had to take my computer to a buddy's house and install wine. Any help would be appreciated.

---

### Post by darolu on 2009-07-04
The two Ubuntus listed in GRUB is easy to solve, just install **StartUp Manager** with synaptic and then set it to display only 1 kernel version.

You can fix compiz by pressing "Control+Alt+F1", this will lead you to a console-mode terminal (TTY1) (you can switch back to Graphical mode with "Ctrl+Alt+F7"), once you are there log in and kill compiz with "sudo killall compiz", doing this will fix the monitor flashing and freezing thing temporarily, at least you'll be able to use your computer so you can fix it permanently later on.

It is usually a drivers problem, try propietary video drivers or uninstalling XGL/Compiz and using the regular one; there are several howtos for compiz in the forum; search for them as I personally can't tell you a sure way to fix it, not without more information; if you can include your system configuration (specially what video card you are using) and also try running compiz on a console and let us know the errors it gives you.

I hope this helps.

---

### Post by robertqadkins on 2009-07-04
> **darolu said:**
> The two Ubuntus listed in GRUB is easy to solve, just install **StartUp Manager** with synaptic and then set it to display only 1 kernel version.

You can fix compiz by pressing "Control+Alt+F1", this will lead you to a console-mode terminal (TTY1) (you can switch back to Graphical mode with "Ctrl+Alt+F7"), once you are there log in and kill compiz with "sudo killall compiz", doing this will fix the monitor flashing and freezing thing temporarily, at least you'll be able to use your computer so you can fix it permanently later on.

It is usually a drivers problem, try propietary video drivers or uninstalling XGL/Compiz and using the regular one; there are several howtos for compiz in the forum; search for them as I personally can't tell you a sure way to fix it, not without more information; if you can include your system configuration (specially what video card you are using) and also try running compiz on a console and let us know the errors it gives you.

I hope this helps.

When do I press "Control+Alt+F1" to get to a console -mode terminal...sorry, new to ubuntu.

---

### Post by darolu on 2009-07-05
> **robertqadkins said:**
> When do I press "Control+Alt+F1" to get to a console -mode terminal...sorry, new to ubuntu.

Hey take it easy we all were new to Ubuntu and GNU/Linux, I'm glad you are learning. You can press ctrl+alt+F1 at any moment, even before you log in in GDM (GNOME Display Manager) aka the screen where you type your user name and password; actually I would recommend to log in to TTY1 here (the ctrl+alt+f1 thing), so you are ready to act as soon as compiz problems begin; you can actually have more than one console-mode terminal by pressing F2, F3... instead of F1. the graphic one is F7 so you can switch from one to another by pressing ctrl+alt+F#; when you log in via GDM (graphical mode) and the flashing screen appears, you go to TTY1 and do the "sudo killall compiz", this will stop/close all compiz which is the one causing the flashing screen. This link will teach you more about the "killall" command: [http://www.hscripts.com/tutorials/linux-services/killall.html](http://www.hscripts.com/tutorials/linux-services/killall.html)

And if you have time and curiosity to learn more about Linux: [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/) (start with the general commands).

Hope this helps

---

### Post by robertqadkins on 2009-07-05
> **darolu said:**
> Hey take it easy we all were new to Ubuntu and GNU/Linux, I'm glad you are learning. You can press ctrl+alt+F1 at any moment, even before you log in in GDM (GNOME Display Manager) aka the screen where you type your user name and password; actually I would recommend to log in to TTY1 here (the ctrl+alt+f1 thing), so you are ready to act as soon as compiz problems begin; you can actually have more than one console-mode terminal by pressing F2, F3... instead of F1. the graphic one is F7 so you can switch from one to another by pressing ctrl+alt+F#; when you log in via GDM (graphical mode) and the flashing screen appears, you go to TTY1 and do the "sudo killall compiz", this will stop/close all compiz which is the one causing the flashing screen. This link will teach you more about the "killall" command: [http://www.hscripts.com/tutorials/linux-services/killall.html](http://www.hscripts.com/tutorials/linux-services/killall.html)

And if you have time and curiosity to learn more about Linux: [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/) (start with the general commands).

Hope this helps

I can't boot past the Ubuntu Loading screen. Once the loading bar gets to about 90% the screen starts flashing and freezes up. The only thing I can do somewhat successfully is boot in to the recovery mode.

---

