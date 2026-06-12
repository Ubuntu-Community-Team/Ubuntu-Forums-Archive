---
title: "DPMS problems with Edgy"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by artnay on 2006-11-20
I'm having difficulties with DPMS and X.Org in Edgy. The point is that I can't get DPMS (power saving features) off. I've installedUbuntu as a server and after that I've downloaded Edgy versions of xorg, GDM, openssh-server, cron-apt, fluxbox, sun-java5-jre, msttcorefonts, localepurge and feh with the dependencies those packages have. I've manually installed Adobe Acrobat 7.0.8 and Flash 9 Beta, and Opera 9.02 from their own repository.

The computers I'm using are pretty basic and meant only for web surfing as a kiosk. Display adapter is the same in all of them, Ati Radeon 7000 VE. They all have the same hardware. Mother board is Asus A7V8X which is based on VIA KT400 chipset and it uses AwardBIOS. I've tried several LCD monitors, such as Samtron 51S and Acer Al1713. Power saving features occur on every computer in spite of all the settings that should disable DPMS.

I've commented out xorg.conf's Option DPMS and .xsession contains line xset -dpms, but still the monitor goes into power saving mode. I've disabled power saving features from BIOS as well. I even tried using vesa drivers but still the monitor goes into power saving mode after some idle time. Currently I'm using stock driver ati and the latest Ubuntu server kernel. Despite of all my efforts, DPMS is being loaded every time X.Org starts according to /var/log/Xorg.0.log. I even disabled extmod, only effect having one DPMS line less in a log file. So that didn't do the trick.

Could this happen because of EDID? I haven't enabled that on  /etc/X11/xorg.conf, maybe I should insert a line just to be sure that it's disabled. So how do I disable DPMS? Any help is greatly appreciated.


I've attached my xorg.conf here and since the limits of Ubuntoforums.org, Xorg.0.log with and without extmod being loaded can be found from [here]("http://www.saunalahti.fi/~gronji").

---

### Post by artnay on 2006-11-20
*bummer*

Could someone confirm this? Should I file a bug or is there a way that I've completely missed? When it comes to actual solution... Well, the sooner the better.

---

### Post by rod.naph on 2006-11-21
i am running kubuntu edgy with an ati card (drivers v8.29.6) and having exactly the same problem as described here.  i'm trying to watch movies but have to move the mouse every 10 minutes, it's driving me nuts!"&£*  if there's anyway i can help by giving more information just let me know.  i've tried everything the above post mentions but still nothing...

---

### Post by artnay on 2006-11-21
Fedora lists had a comment that "xset -dpms" no longer works, although xset's man page has that option mentioned. Instead one should try "xset dpms force off". On some computers I tried it, monitor went dead black and wouldn't wake up before restarting X. Had no effect on actual DPMS for some reason.

Plan B, vbetool. "sudo vbetool dpms off". No dice, power saving features are still active.

And one probably important note that I left mentioned before, this happens with both VGA and DVI.

I'm eagerly trying to find a solution, going through logs etc. I'll probably install gnome-power-manager just for testing. If that doesn't help, then it's time for a bug hunt. ](*,)

rod.naph, the reason might be the software you use to watch videos. Perhaps you're running Kaffeine?

---

### Post by rod.naph on 2006-11-22
my (hopefully temporary) solution is this little program which fakes mouse moves, i just run it as a daemon started automatically when i log into kde.  if it's any help to anyone, it certainly makes movie watching a little more bearable for me!

---

### Post by anboni on 2006-12-08
Thanks for that one, Rod :)

I took the liberty of slightly modifying the code, so the mouse cursor doesn't pop up in the middle of my (mouseless) MythTV screen every minute :)

For anyone interested in this modified version, edit main.c line 30 to match roughly your screen resolution (for my 1360x768 screen I picked 1350x760, so I'm always within the bounds of the screen). Please do note that the modified version uses fixed positioning, so you wont want to use it on a system where you actually control the mousepointer yourself :cool:

---

