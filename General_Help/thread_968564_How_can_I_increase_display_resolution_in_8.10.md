---
title: "How can I increase display resolution in 8.10?"
date: 2008-11-02
forum: General Help
---

### Post by snakyjake on 2008-11-02
I just upgraded to Kubuntu 8.10 Intrepid.  Prior, I was able to get a resolution higher than 960x600.

I went to "\Applications\System\System Settings\Display" to try and change the resolution, but the maximum option is 960x600.

I think my video card is SiS, not sure of model.  Monitor is ViewSonic PT775.

Thank you.

---

### Post by Civaus on 2008-11-03
I changed my Gnome resolution to a setting too high using the GUI and this caused the screen to be completely unusable until I dropped to command line.

Use pico to change Ubuntu 8.10 screen settings in the monitors.xml file.  It is in a hidden folder in the user directory.  ~/.config/monitors.xml

1) Drop to command line (Alt+F2)
2) "cd .config"
3) "sudo pico monitors.xml"
4) Change vertical and horizontal resolution to something your monitor supports (e.g. 1280x1024)  




[http://ubuntuforums.org/showthread.php?t=969066](http://ubuntuforums.org/showthread.php?t=969066)

---

### Post by snakyjake on 2008-11-04
Thanks for the help.  Unfortunately I do not have a monitors.xml file.

---

### Post by umzRV on 2008-12-01
So I found the monitors.xml file, but when I try to run cd.config in the command line (Alt+F2) it says directory not found; even when I enter the full file path.
So I thought this is stupid and did -sudo pico monitors.xml- in the command line thinking whats the worst that could happen anyway, and when I click run nothing happens... am i doing something wrong? :confused:

---

### Post by jagnikam on 2009-04-02
Follow these steps 
ALT + F2
type xterm
cd ~/.config
vim monitors.xml
press [COLOR="Magenta"]i[/COLOR] for insert
make changes
save by using [COLOR="Magenta"]:wq[/COLOR] 



> **umzRV said:**
> So I found the monitors.xml file, but when I try to run cd.config in the command line (Alt+F2) it says directory not found; even when I enter the full file path.
So I thought this is stupid and did -sudo pico monitors.xml- in the command line thinking whats the worst that could happen anyway, and when I click run nothing happens... am i doing something wrong? :confused:

---

