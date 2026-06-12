---
title: "Duel Monitors on a Nvidia 9800 GT"
date: 2009-04-09
forum: Hardware
---

### Post by glubbdrubb on 2009-04-09
I am trying to activate the second display on the duel monitor graphics card.

I have the recommended drivers and "utilities" installed. As you will see in the screenshot, I am using the "Nvidia X Server Settings" utility to configure the second monitor display. However, I seem to need to restart X Server to apply the settings. I dont know how to do that.

Am I on the right t track?

EDIT:

Sorry, the screen shot should be up now.

---

### Post by Joeb454 on 2009-04-09
It should do it automatically for you, what I would advise is to play around with the settings (make sure it's set to twinview) until you get it right, then restart as root so you can save it to the xorg.conf file to make it permanent :)

At least - that's how I got mine set up on a 9500GT :)

---

### Post by loomsen on 2009-04-09
Specify your desired settings, save the xorg.conf file to a place you can simply access it, like ~/Desktop for instance.

Close nvidia-settings, startup a terminal, do this to backup your existing xorg.conf and replace it with your generated:

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup && sudo cp $HOME/Desktop/xorg.conf /etc/X11/xorg.conf
```

Restarting your PC is the way if you don't know how to drop into a shell and issue init functions there. So do it.

---

### Post by glubbdrubb on 2009-04-09
I have been fiddling with it now for half an hour and I also get the error you will see in the second screen shot.

I have got it to work in Vista after a restart but it wont work in Ubuntu. Do I need to restart Ubuntu? I would prefer it if I don't because I have uninterpretable processes running.

---

### Post by glubbdrubb on 2009-04-09
Thanks, that worked beautifully [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif) . 

Would it be possible to assign a workspace to a monitor? And then could I assign certain applications? to that workspace/monitor?

That would streamline my work-flow quite nicely.

---

### Post by loomsen on 2009-04-09
The only restriction in linux is the user. Everything is possible.

Hint: compiz(assigning names to workspaces, creating window rules and so on), manual pages(from a terminal type 'man <command>, for instance
[color=red]man nvidia-settings[/color], google.......

---

### Post by genesis2seven on 2009-04-28
I have two Nvidia 9800 cards with dual monitors. Follow the instructions here on my blog. I am using the 180.51 driver from Nvidia without any issues. I don't have SLI enabled.

[http://www.adamlowe.me/2009/02/nvidia-18029-driver-on-ubuntu-810.html](http://www.adamlowe.me/2009/02/nvidia-18029-driver-on-ubuntu-810.html)

If you don't get back into gnome after you install and reboot then just hit Alt+F1 and then edit your xorg.conf file in nano

$sudo /etc/X11/xorg.conf

Then save and reboot once you've got your Busid in the xorg.conf and you should be good to go. Once you're in gnome open up a terminal and run

$sudo nvidia-settings

Activate both monitors, enable Twinview, click the Apply button and all should be well. Might also need to enable compiz effects.

---

