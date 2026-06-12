---
title: "[SOLVED] External monitors don't come on at boot, 2011 iMac 27&quot;"
date: 2024-01-24
forum: Hardware
---

### Post by furtivehippo on 2024-01-24
Hi there

I'm running Ubuntu 23.10 on the aforementioned iMac. It has a pair of Benq external monitors attached, but when you boot the machine only the iMac screen shows the desktop. The external monitors stay in standby.

I do have a workaround: if I open a terminal and issue the command

```
sudo systemctl restart gdm
```

then all three start working. Any ideas how I can get them all to fire up at boot time please?

---

### Post by furtivehippo on 2024-01-27
Fixed... I found [someone who had a similar problem]("https://superuser.com/questions/1613275/how-could-i-boot-my-ubuntu-20-04-laptop-to-show-2-external-monitors-and-usb-devi"), albeit not with a Mac, and used the following from their solution which has got my setup working.

> 
[LIST=1]
[*]You should configure your monitor configuration  with Desktop -> right click -> Display Settings. Turn on / off the  monitors like desired, and set the main monitor, afterwards apply. 
[*]You have to finally copy the monitor configuration to the the gdm  (Gnome Display Manager), to let the configuration also apply to the  login screen after boot (/var/lib/gdm3/):
 $ sudo cp -rvf ~/.config/monitors.xml ~gdm/.config/ 
[*]Reboot and it should work now as wished! 
[*]Use Xorg instead:
  $ vim /etc/gdm3/custom.conf 
[/LIST]
           and uncomment
           WaylandEnable=false


---

