---
title: "How to hibernate on low battery?"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by mfyahya on 2005-11-15
I have a dell 6000 inspiron. Is there a way to make the system hibernate at say 3% battery power instead of shutting down all of a sudden (and losing data) ?

---

### Post by vasdee on 2005-11-15
install gnome-power-manager. I don't actually use it but i think it has the capability to do what you want judging from the screens here
[http://www.gnome.org/projects/gnome-power-manager/gpp.html]("http://www.gnome.org/projects/gnome-power-manager/gpp.html")

---

### Post by mfyahya on 2005-11-17
I installed it, but it doens't show most of the options shown on those screens. Also it gives this error:

"You have not got DPMS support enabled in gnome-screensaver. You cannot change the screen shutdown time using this program."

What is DPMS? I looked in the screensever settings utility but couldn't find any reference to it.

---

### Post by Lambert on 2005-11-17
DPMS is display power management signaling. When you click system>pref>screensaver; open the advanced tab. enable display power management.

In the gnome-power-manger; on the advanced tab you should have a section other options. Here you can set the percentages when it's considered low or critical. On the options tab you should be able to set the action when battery gets to the critical percentage.

---

### Post by mfyahya on 2005-11-18
thanks for the reply
enable display power management was already checked, and I'm still getting the error message. So I can't adjust the display brightness.
But I did set the action when battery is critical and I'm hoping that will work now.

---

### Post by hughsient on 2005-11-27
You need to update to a newer version of g-p-m (which doesn't have the warning), or install a fairly recent version of gnome-screensaver, as the DPMS functionality is done with that, rather than the now-obsolete XScreenSaver.

Richard.

---

### Post by ozorba on 2005-11-27
How do I get gnome-power-manager applet displayed in the first place? I have installed gnome-power-manager bot the only applet I have is battery charge monitor. I have installed gnome-screensaver as well. Am I missing something?

Thanks

---

### Post by ispiked on 2005-11-28
ozorba, it should be in System > Preferences > Power Preferences.

---

### Post by GoodPanos on 2005-11-28
[QUOTE=hughsient]You need to update to a newer version of g-p-m (which doesn't have the warning), or install a fairly recent version of gnome-screensaver, as the DPMS functionality is done with that, rather than the now-obsolete XScreenSaver.[/QUOTE]

Where can you get the latest gnome-screensaver?  Can you install if via Synaptic?

---

### Post by GoodPanos on 2005-11-28
Never mind that I got it.

The gnome-screensaver though, is so limited.  Where's the pizazz?

---

### Post by prizrak on 2005-12-07
Hmm gnome-screensaver didn't have any options for activating APM for me and gnome power manager didn't have any of the options for power management. I remember that the battery applet used to have an option to run a program when battery got to a certain level but I don't see it in Breezy anymore otherwize I'd just have it run the Hibernate script. My laptop does hibernate however.

---

### Post by prizrak on 2005-12-07
Nevermind, I installed the new gnome manager from the backports and it has all the functionality.
Well that did nothing, the hibernate command issued by it doesn't do anything.

---

