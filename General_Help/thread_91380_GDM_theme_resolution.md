---
title: "GDM theme resolution"
date: 2005-11-17
forum: General Help
---

### Post by wereks on 2005-11-17
i just want to know how to change the resolution size of a gdm theme jejeje please help me jejeje :)

---

### Post by the_it on 2005-11-17
Gnome should have something like a Display menu item or Resolution menu item in the System Preferences.  The dropdown menu inside will let you pick from differing screen resolutions that have been autodetected previously by your installer to match your video card AND monitor.  You can change resolutions there.

However, know that the autodetecter isn't perfect, so in some cases you may want to specifiy a specific resolution to be detected.  In which case, you'll want to run *sudo dpkg-reconfigure xserver-xorg* and go through the menu to enable resolutions beyond the previously autodetected.

If you STILL aren't satisfied with the guided resolutions detected by the menu, you can manually edit your /etc/X11/xorg.conf file to ensure that your chosen resolution is in the list of resolutions on your default monitor.  Take care that you dont mistype as this is an important file, and take note of the format.

You can restart your gdm environment using <ctrl><alt>Backspace from within gdm, or you can kill it via terminal by using *ps -ax|grep gdm* then sending a *sudo kill ####* where #### is the number of the gdm process, then issuing a *sudo gdm* afterwards to restart gdm.

---

