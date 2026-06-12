---
title: "need help to replace xubuntu by ubuntu 8.1 from dvd on my eee 700"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by zuzuzu on 2009-04-20
Hello,

I have a 4gb eee pc 700 with xubuntu and want to replace it with ubuntu 8.1 with an external cd/dvd from a dvd where I burnt the last version of ubuntu.

I did change the boot priority by the dvd before the hard drive but it does not work, I can see the dvd working during the set up but after a 2 minutes where the green light of the dvd is flashing there is xubuntu starting like before.

Any help or solution is welcome

thank you

---

### Post by Darael on 2009-04-20
There's no need to replace it, you can just run a single command to install the Ubuntu desktop as they use the same repository.  Then you can choose a GNOME session next time you log in.

The command to add the other desktop environment is "sudo apt-get install ubuntu-desktop"

EDIT: you'll probably need to remove the xubuntu-desktop packages afterwards, considering your drive space limitations.  You need a much longer command to remove them all, but here it is:
```
sudo apt-get remove abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0 libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-desktop
```

---

### Post by zuzuzu on 2009-04-20
well I am a newbie to linux so I made the command but no more space on the disk so got some error message. I have some files like the iso of ubuntu 8.1 on my desktop I can not delete another error message.

Is there a way I can format and restore from scratch

---

### Post by zuzuzu on 2009-04-22
no way I can restart from scratch ?

---

