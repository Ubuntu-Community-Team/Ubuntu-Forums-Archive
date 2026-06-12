---
title: "sounds easy? i need to run a command at startup as root, after X + GNOME have started"
date: 2008-09-01
forum: General Help
---

### Post by CC_machine on 2008-09-01
right now I'm trying to set up joystick control for the mouse. there have been many topics on this, and i finally got it working. I'm using a software device node that's updated by "joymouse"... to use my joystick, all i have to do is type "joymouse" in a root terminal.

so, i added it to /etc/rc.local. Didn't work, as X hasn't started yet and the display can't be opened... (i know this as i used "joymouse > /home/ccmachine/rclocaljoymouse" and read the file... joymouse can only be run once the display is active.

suggestions? i tried system -> prefs -> sessions, but the commands there aren't run as root >_<

---

### Post by eldragon on 2008-09-01
im sure you could add joymouse to the sudoers file but i do not know how to do this. maybe someone can help on this area?

---

### Post by gali98 on 2008-09-01
I also need to know how to do this for a different reason.
I just need to have an easy place to put commands so that they run after gdm is started.

Kory

---

