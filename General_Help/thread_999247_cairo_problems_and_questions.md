---
title: "cairo problems and questions"
date: 2008-12-01
forum: General Help
---

### Post by manosone on 2008-12-01
Hello to all.Well i got a problem with the cairo and i need some help...

1)The first issue is the manual lucher.I add a manual luncher an i can not delete it.When i right click on the luncher the menu that comes up is the settings menu for the dock and not for the luncher.So i do not have the "remove" option and cause of this i can not delete it.

2)How can i resize the dock?I want it to be smaller.


Thanks a lot.I am using 8.10

[[img]http://img10.imagehosting.gr/out.php/t348283_cas.jpg[/img]](http://www.imagehosting.gr/show.php/348283_cas.jpg)

---

### Post by Ng Oon-Ee on 2008-12-02
> **manosone said:**
> Hello to all.Well i got a problem with the cairo and i need some help...

1)The first issue is the manual lucher.I add a manual luncher an i can not delete it.When i right click on the luncher the menu that comes up is the settings menu for the dock and not for the luncher.So i do not have the "remove" option and cause of this i can not delete it.

2)How can i resize the dock?I want it to be smaller.


Thanks a lot.I am using 8.10

[[img]http://img10.imagehosting.gr/out.php/t348283_cas.jpg[/img]](http://www.imagehosting.gr/show.php/348283_cas.jpg)

The manual launcher just has a very very small 'hit area', so you need to try repeatedly to right-click on the right spot. Also, if I'm not wrong, you shouldn't click on the words "New Launcher", but somewhere below/above it, as that's where the icon is supposed to be (if there was an icon). Alternatively, I suppose you could go to ~/.config/cairo-dock/current_theme/launchers and try to delete from there, not sure if that would work.

You don't want to resize the dock, you want to resize the icons. In the advanced configuration, go to 'Icons', you'll find separate entries for icon size of launchers, applications, and applets. Change all those to a smaller size.

---

