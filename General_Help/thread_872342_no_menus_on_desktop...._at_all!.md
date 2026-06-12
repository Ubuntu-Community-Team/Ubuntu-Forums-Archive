---
title: "no menus on desktop.... at all!"
date: 2008-07-27
forum: General Help
---

### Post by skeletor13 on 2008-07-27
im new to linux adn ubuntu but decided to dual boot and have been tinkering with ubuntu the last 2 weeks.  had everthing working fine .  just reorganized my music 2 days worth of time to songbird.  anyhoo i go to use the laptop today and i couldnt access my documents or any of the 'places'.  so i reboot.  upon rebooting i find i no longer have a desktop.  the background is there, i can switch between space 1 and 2, if i hit print screen the little window comes up to ask where i wish to save but that is it!!! the help button from that window works normally.  

so im stuck with no menus or too bars.  since im new to ubuntu i dont know any key combinations to even see if things are working or what. ctrl alt delete pops the screen up asking is i wish to shut down restart hybernate etc as per usual.  

im at a loss as to what happened and what to do about it. i relaly hope i doesnt require a fresh instal after i spent so much time getting the wireless working and reporganzing my music.

thanks in advance

---

### Post by skeletor13 on 2008-07-27
tried plugging in my ipod and nothing happens, no icon shows up on the desktop.  also i tried saving a print screen to the desktop and again nothing shows up.

---

### Post by skeletor13 on 2008-07-27
oh and i think the last thing i changed was i was fiddling around with the power management thing.  changing what happens when i close the lid of the laptop.... if that helps.

---

### Post by fooman on 2008-07-27
try pressing alt-f2 and see if the "run application" box pops up.

...if it does, type:

```
gnome-panel &
```

and click the "run" button.

---

### Post by jnvta on 2008-07-27
[FONT="Courier New"][/FONT]sorry i don't have a fix, but this happend to me also, but in my case it happend when i click the bubble that says " 365 updates availeable" after 45 minutes it said reboot and when i did, the screen was just solid blue with no task bars at all. i had to right click...the mouse to get a menu.good luck

---

### Post by skeletor13 on 2008-07-27
thanks for the reply.  alt-f2 isn't doing anyting.

i hit ctrl alt and the f keys and some black terminal esk screen comes up

ubuntu 8.04.1 brendan-laptop tty1

brendan-laptop login:       

and its waiting for me to type whatever

---

### Post by UbuntuNerd on 2008-07-27
you can reset to default panels by typing in the console 

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

to get to the terminal boot in safe mode

also you can try this command 


sudo apt-get install gnome-menus

---

### Post by skeletor13 on 2008-07-27
i assume you mean in the root shell prompt,
after i tuped teh first thing it said 'cannot open display:
run 'gnome-session-remove --help' to see full list of available comand line options.

i put in 'gconftool-2 --recursive-unset /apps/panel'  and that didnt seem to do anything as it just went back to root@brendan-laptop:~#

---

### Post by skeletor13 on 2008-07-27
i tried 'gnome-panel'   and it retuns with:
the program gnome-panel is currently not installed. you can insall it by typing: apt-get gnome-panel

so i tried that but it gets caught.  says failed to fetch the the site on ca.ubuntu then says could not resolve 'ca.archive.ubuntu.com'
unable to fetch some archives, maybe try apt-get update or try with --fix-missing?

---

