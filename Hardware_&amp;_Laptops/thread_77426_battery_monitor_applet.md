---
title: "battery monitor applet"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by vtec on 2005-10-16
I have a compaq v2000. Hoary worked fine, however i just did a clean install of breezy and the battery applet never shows when the computer is pluged in. Is there anyway to fix this??

---

### Post by civilwarlord on 2005-10-16
right-click on the bar at the top & choose "add to panel" you might find it there.

---

### Post by vtec on 2005-10-16
I'm sorry... i didn't explain the problem to well. The applet is there, however when you mouse over it always shows that u are using battery power. Never shows that it is pluged in. It does however seem to have the correct amount of power showing.

---

### Post by vtec on 2005-10-16
Well i'm not sure why, but after using it for a while it started to work. I'm not sure what i changed if anything:???:

---

### Post by bereillyte on 2005-10-17
I've seen the same issue, especially if the battery is fully charged. If you enter acpi -V you can see that the battery is "Discharging" but the AC is on-line. Someone else suggested that the Charging/Discharging might just be a binary value - so if the battery is full charged, it is no longer charging, hence must be discharging.

I installed gnome-power-manager and that seems to take the AC status to display the correct icon.

---

### Post by sigma2805 on 2005-10-18
Hi,
I tried installing the gnome-power package and it still doesn't show that the laptop is plugged in....When i run the mouse over the applet it says "System is running on battery power Unknown time(98%) remaining

---

### Post by mjukr on 2005-10-18
I have a v2000 as well. What does $ acpi -V show for you? Here is my output. (The first on battery power, the second after plugging in the AC adapter):


muk@wixt:~$ acpi -V
     Battery 1: discharging, 76%, 01:53:44 remaining
     Thermal 1: ok, 58.0 degrees C
  AC Adapter 1: off-line
muk@wixt:~$ acpi -V
     Battery 1: charging, 76%, 00:19:54 until charged
     Thermal 1: ok, 58.0 degrees C
  AC Adapter 1: on-line

---

### Post by Bondolon on 2005-10-18
I too have a V2000, and my battery applet also doesn't work.  Originally, my thermal was freaking out completely, so I tried turning off ACPI.  That helped to completely rule out the possibility that I could use hardware monitoring at all, much less battery.  Maybe there's a fix in developement right now.

---

### Post by edal on 2005-10-18
Add me to the list, although I'm using a Sony Vaio PCG-K415B. No matter what I do the battery charge applet indicates that I am on AC power and no battery is present.

This fault was in Ubuntu 5.04 and is also present in 5.10. The weird thing is that acpi -V gives the correct information:

Battery 1: charging, 19%, 03:10:49 until charged
Thermal 1: ok, 48.0 degrees C
AC Adapter 1: on-line

Ed Almos

---

### Post by estornino on 2005-10-18
I've the same problem with a HP dv1000 series. I'll post the acpi -V thing if you want to.

---

### Post by sigma2805 on 2005-10-18
[QUOTE=sigma2805]Hi,
I tried installing the gnome-power package and it still doesn't show that the laptop is plugged in....When i run the mouse over the applet it says "System is running on battery power Unknown time(98%) remaining[/QUOTE]

I noticed that it does show that the battery is charging like its supposed to when i plugged it in after using the battery for awhile so at least that works. I think the issue arises out of the computer thinking that the battery is constantly discharging when its plugged in.

---

### Post by picole on 2005-10-19
I have the compaq evo N610 ,my battery monitor applet is just fine.
picole@tongji-picole:~$ acpi -V
     Battery 1: charged, 100%
     Thermal 1: active[2], 52.0 degrees C
     Thermal 2: ok, 45.0 degrees C
     Thermal 3: ok, 16.0 degrees C
  AC Adapter 1: on-line
And when i move the mouse to the applet,it display System is running on AC power Battery charged (100%)
i use the apci ,not apm.
Good luck!:)

---

### Post by sigma2805 on 2005-10-26
was anyone able to resolve this?

---

### Post by Snowcat on 2005-10-26
I also had this problem (applet only showing that the computer is on battery power). I fixed it by setting the property no_hal to true (or 1 or whatever) in the configuration. There's instructions on how to do that in the applet's helpfile.

Not sure if it's any help, but for me it fixed everything :)

---

### Post by sigma2805 on 2005-10-26
i tried the no_hal thing but it didn't work. I'm pretty sure i don't need a new DSDT because it worked fine in hoary but it doesn't work in breezy...very odd...

---

### Post by hughsient on 2005-11-27
[QUOTE=sigma2805]I tried installing the gnome-power package and it still doesn't show that the laptop is plugged in....When i run the mouse over the applet it says "System is running on battery power Unknown time(98%) remaining[/QUOTE]

You need to update g-p-m to a newer version. There have been lots of improvements recently, and the tooltip and icon logic has improved substantially.

Please report problems to gnome-bugzilla and I can track them there.

Thanks, Richard Hughes, g-p-m maintainer.

---

### Post by sigma2805 on 2005-12-05
Hello,
Thanks for the suggestion. I went ahead and installed the new version of gnome-power-manager after converting the RPM available at [http://gnome-power.sourceforge.net/data/yum/](http://gnome-power.sourceforge.net/data/yum/) to a deb file.

when i try to run gnome-power-manager, i get the following error

gnome-power-manager: error while loading shared libraries: libwnck-1.so.16: cannot open shared object file: No such file or directory


currently, i have libnotify(version 2.1) and hal (version .5.3). Do i have to upgrade libnotify to get this to work because if i uninstall the current version that will effect ALOT of gnome applets...

---

