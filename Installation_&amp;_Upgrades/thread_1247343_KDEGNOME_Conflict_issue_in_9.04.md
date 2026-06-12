---
title: "KDE/GNOME Conflict issue in 9.04"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by us3598 on 2009-08-22
I have just installed the netbook remix onto a friends laptop. Unfortunately, the remix desktop ran too choppy on the machine, so I disabled it. I also just installed KDE and XFCE via synaptic (the kubuntu-desktop and xubuntu-desktop packages). Now, when I login to KDE, both KDE AND Gnome start simultaneously. Not only that, but Gnome in this instance defaults to the netbook desktop, and my only alternative is to restart the system. Any help would be greatly appreciated.

---

### Post by aysiu on 2009-08-22
It's not possible for Gnome and KDE to start simultaneously. Can you describe exactly what you see when you log in? Or, better yet, take a screenshot and post it up?

Alternatively, you can remove Gnome completely:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by us3598 on 2009-08-23
See, thats what I thought. Unfortunately, I am unable to take a screenshot, however when I boot into sfce, the same thing happenes. Exactly what occurs, is when I click Select Session, then KDE (or XFCE), then input username and password, the system boots into the KDE or XFCE environment. About 10 seconds later the netbook remix screen pops up OVER KDE. When I select classic view, both the GNOME screen and the KDE or XFCE desktops overlap each other, changing focus every time I move the mouse to a different part of the screen. I have attempted to reinstall twice, with the same result.

---

### Post by aysiu on 2009-08-23
Not sure about the overlapping thing, but the netbook remix thing you can remove by itself by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove maximus human-netbook-theme ubuntu-netbook-remix ubuntu-netbook-remix-default-settings netbook-launcher
```

---

### Post by junn0suk3 on 2009-08-24
I had the same issue with the "Overlapping" of the UNR enviroment over KDE.  The situation is that UNR is based off Gnome and when you change the desktop mode to classic, it wakes up the gnome enviroment over the already open KDE.  This is what I did...  First of all, boot up in KDE.  The UNR enviroment will appear.  Do not change back to Classic desktop mode.  Instead, click on "Exit" (Specifically in the UNR enviroment) and then log off.  This should disable UNR and leave you on KDE exclusively.  When this is done, go to "System Settings" and in the "Advanced" tab, you'll click on "Autostart".  You'll see UNR launcher's box is checked...  Uncheck it.   Apply changes, log off KDE then log on.  You should be able to log in without UNR bothering you.  This worked for me, hope it does for you. :)

---

