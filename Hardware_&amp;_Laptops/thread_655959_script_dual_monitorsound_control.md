---
title: "script dual monitor/sound control"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by scamper_22 on 2008-01-02
Hi,

I've been trying to write a script so I can switch to 'presentation mode' by running one file.
This script does the following

1.  sets the volume of the laptop to 0% and the line out to 100%
2.  configures the video for dual monitor

I've managed to get the sound part working fine

  echo "Setting Movie Mode"
  amixer -c 0 sset Master,0 0%
  amixer -c 0 sset Headphone,0 100%

Does anyone know how I would automatically control the video?
I can manually do it via the Nvidia Settings tool [Application-System tools] .

What I have tried:
using the nvidia settings, I saved the xorg.conf files.  as xorg.conf.movie
I was thinking I would just copy this file over the /etc/X11/xorg.conf.
But how do I get the x11 server to 'apply the settings'
I tried 
sudo /etc/init.d/gdm restart
but it's not what i want.  The desktop does not come back.

Any ideas?

---

### Post by foolsh on 2008-01-02
I use a script to change from dual monitors to single monitor 
the script only copys a xorg.conf over the /etc/X11/xorg.conf file and I have to Ctrl+Alt+Backspace to restart X with the new setting putting "sudo /etc/init.d/gdm restart" in the script causes it to hang at restarting gdm. if I run the scirpt from inside the GUI.

you could add it to the script but you would have to run the script from the CLI for it not to hang.
has something to do with the script being killed when X is restarted.
If you figure out how to do this from inside the GUI could you share your insight?

---

### Post by scamper_22 on 2008-01-02
Thanks,

ctrl-alt bkspace does work and the desktop does return, but I have relogin in again...
Better than what I had before :)
Thanks for that tip.

When I use the nvidia control panel, it does not need to restart X to 'apply the settings' for dual/single monitor.  Wonder if theres a way to do that.

Hmmm, if worst comes to worst, is there a gui scripting, that can record mouse actions or something that I can use.

---

### Post by scamper_22 on 2008-01-02
hmm, some further research reveals it may be possible to use nvidia-settings via the command line.
man nvidia-settings

I will investigate this when I get home.
any feedback on doing this would be helpful

---

