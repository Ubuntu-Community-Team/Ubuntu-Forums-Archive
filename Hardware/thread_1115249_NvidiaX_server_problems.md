---
title: "Nvidia/X server problems"
date: 2009-04-03
forum: Hardware
---

### Post by BananaUnicorn on 2009-04-03
Im having a nightmare with Nvidia drivers, all started when I tried to install the latest drivers and after tweaking for hours they worked.


Turned on PC next day and they didnt, it booted up in safe graphics mode, NO drivers working. Only error is that it couldnt detect graphics card properly


All I want now is to get it back to the default drivers but no matter what I do it it boots into safe mode. Uninstalled Nvidia drivers and editted the xorg.conf file and it'll boot up normally (first an error aout an Xserver being detected and do I want to try another level), if I select yes it works but without drivers, but then go back to safe mode if I restart again


I was messing around with X server settings when installing the drivers im thinking maybe I messed something up. Just need to go back to the default settings and I dont want to reinstall Ubuntu but its starting to look like the only way, no matter what I do to the xorg it seems to automatically boot into safe mode upon restarting with an error saying card and moniter cant be detected/configured, and I need to restart to get drivers working!

---

### Post by logic++ on 2009-04-03
I suppose you still have the driver downloaded to some folder.

I had the same problem but managed to figure it out:

1>Uninstall the driver:
```
sudo sh NVidia-blabla.sh --uninstall
```
2>Reboot:
```
sudo reboot
```
3>Reinstall the driver:
```
sudo sh NVidia-blabla.sh
```
When asked, allow nvidia installer to fix the xorg.conf file.

---

### Post by BananaUnicorn on 2009-04-03
I followed first 2 steps and uninstalled it again, and afterwards deleted the file.


But I dont want to try reinstall NVIDIAS drivers, I just want the default Ubuntu ones from the repo, and when I try install them it boots back into safe mode.



Edit: and last time I tried install them it kept saying it detected an active Xserver, even after sudo typing 

/etc/initid/gdm stop

---

### Post by BananaUnicorn on 2009-04-03
After another attempt at installing repo drivers and rebooting I noticed some errors that popped up as it flashed to safe graphics mode


Not Starting K Display Manager it is not default display manager (or something like that)

then said

Running Local scirpts /etc/rc.local


I use GNOME so no idea what its saying something like that


I looked at rc.local and its about default startup level or something, so again its coming back to that.

Already tried reinstalling Xserver, didnt seem to do much maybe I didnt do it right, just run a sudo apt get install line

---

### Post by norwoods on 2009-04-03
when you boot up, press the Esc key when grub says Press 'Esc' to enter the menu
then press the down arrow to highlight the menu entry ending with (recovery mode)
press Enter
you should get the Recovery Menu
repeat pressing the down arrow to highlight the menu entry xfix Try to fix the X server
press Enter
reboot

---

