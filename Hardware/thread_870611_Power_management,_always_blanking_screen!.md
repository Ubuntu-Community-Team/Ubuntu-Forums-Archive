---
title: "Power management, always blanking screen?!"
date: 2008-07-26
forum: Hardware
---

### Post by occhiso on 2008-07-26
Hi,

I have an ASUS A6 series notebook with a 256MB ATI Radeon X1600 built in.
I am running Ubuntu - Hardy

The problem I am having is that regardless of what my power management settings say, my screen always blanks after 5minutes of being idle.
I am happy for the screen to blank when the power adapter is not plugged in, but if the adapter is plugged in, I dont want the screen to blank out.

Below is a screen shot of my power settings and screen saver settings:
[IMG]http://i81.photobucket.com/albums/j230/occhiso/posts/power1.png[/IMG][IMG]http://i81.photobucket.com/albums/j230/occhiso/posts/power2.png[/IMG]

Is there some other configuration hiding somewhere?
Appreciate any help.

Thanks,
occhiso

---

### Post by Dark_Stang on 2008-07-26
Do you have ATI Catalyst installed? If you do check it. If not install it and check it. There may be a switch in there.

---

### Post by Yellow Pasque on 2008-07-26
Try this:
```
gksudo gedit /etc/X11/xorg.conf
```
Copy and paste this into the file :
> Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

Also, look at all of the gnome power-manager settings with:
```
gconf-editor
```
The path is /apps/gnome-power-manager

If that doesn't work, it could have something to do with ACPI.

---

### Post by occhiso on 2008-07-30
Hi Temüjin,

I pasted that code into my xorg.conf file and it looks like it fixed it.
Thanks for your help

occhiso

---

