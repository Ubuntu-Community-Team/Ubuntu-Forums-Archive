---
title: "Startup- Sudo- Command...."
date: 2008-09-09
forum: General Help
---

### Post by samathyr on 2008-09-09
Hi everybody!!

Once I had a problem with my soundcard and the solution was an startup command (something like "kill pulseaudio"). It worked perfectly and I did it using the graphical interface of Gnome (Preferences -> Sessions -> Startup)

Now I have another problem, my wireless device only work after I introduce a couple of commands in the terminal:

```
sudo modprobe b43
sudo ifconfig wlan0 up
```

I need to introduce my password every single time. I have been looking for this, and I found a lot of posts but I wasn't able to do it. One of them is modify "sudo visudo" but I don't know how to edit stuff in the command line.

Can someone give a step-by-step guide ? 

Thanks!

---

### Post by Zorael on 2008-09-09
You could enter them in /etc/rc.local. That file is run upon boot, before you get to the login parts.

However, I would suggest you add **b43** to the end of /etc/modules to get it modprobed automatically, and then use [wicd](http://wicd.sourceforge.net) to manage your network unless you can get your current network manager to automatically connect.

Just tick the 'automatically connect' box in the entry for your wlan in the wicd gui.

---

