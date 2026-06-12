---
title: "Video Problems.....please help........"
date: 2005-12-01
forum: General Help
---

### Post by Polick on 2005-12-01
SO.....I get through the full install with no problems but then when I get to the log-in it freaks out and isn't in the right res.......

i'm running a Pentium 4 - 3.4
Nvidia 7800GT
1 GB Ram

I'm really stuck on this......

If you have any thoughts/tricks....I would be very greatful.

---

### Post by arnieboy on 2005-12-01
[QUOTE=Polick]SO.....I get through the full install with no problems but then when I get to the log-in it freaks out and isn't in the right res.......

i'm running a Pentium 4 - 3.4
Nvidia 7800GT
1 GB Ram

I'm really stuck on this......

If you have any thoughts/tricks....I would be very greatful.[/QUOTE]
when u say u are not on the right resolution, what resolution are u on? I know u are freaked out, but that doesnt tell me much in terms of troubleshooting details.

---

### Post by Polick on 2005-12-01
i have a wide screen and it's trying to do a square one (not for positive what it's going for).    My friend is doing the install too and his gave him a list to choose from during the install.

It loads all of the ubuntu files but then the log-in screen dies(well freezes)...I'm pretty sure it's not the video card because my friend is running the 7800 GTX and it works fine.

Is there a list of conflicting hardware, I was looking and was having much luck.  Even just a list of certified hardware would be fine.

Thanks

---

### Post by arnieboy on 2005-12-01
[QUOTE=Polick]i have a wide screen and it's trying to do a square one (not for positive what it's going for).    My friend is doing the install too and his gave him a list to choose from during the install.

It loads all of the ubuntu files but then the log-in screen dies(well freezes)...I'm pretty sure it's not the video card because my friend is running the 7800 GTX and it works fine.

Is there a list of conflicting hardware, I was looking and was having much luck.  Even just a list of certified hardware would be fine.

Thanks[/QUOTE]
alright try the following:
log into rescue mode from the boot options (GRUB) where u will logged in as root.
then do the following:
```
apt-get install nvidia-glx
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
nvidia-glx-config enable
```
reboot and try logging in the usual way.

---

### Post by Polick on 2005-12-01
The update is not being found...

All the nvidia updates can't be found either...

Yes, glory...

The Nvidia enable is invalid too....

I'm running a wireless microsoft keyboard and mouse and it's not liking some of the key command sometimes....but i did get the update to key in.

Any ideas?

---

### Post by akiro.yamamoto on 2005-12-01
I don't think that the nvidia files are even on the install CD and unless you already have your internet connection set up apt-get ain't gonna work...
So use recovery mode then try the following:

CODE: 
dexconf

That should reconfigure your xorg.conf file to safe settings and give you a usable X11 )Gui) session... :smile:
Hope that helps...
Regards

---

### Post by Polick on 2005-12-07
YAY, I got it solved....after enabling the ethernet.  I feel like a genius...Thanks for all the help guys.

---

