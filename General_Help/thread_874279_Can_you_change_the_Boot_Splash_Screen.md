---
title: "Can you change the Boot Splash Screen?"
date: 2008-07-29
forum: General Help
---

### Post by Breetai on 2008-07-29
I haven't been able to find any threads on the subject and I'd like to change the Ubuntu Splash screen with the scrolling orange bar.  Is that doable or can you not change that?

---

### Post by eximius1 on 2008-07-29
Think this is what your looking for:

[http://ubuntuforums.org/showthread.php?t=11478](http://ubuntuforums.org/showthread.php?t=11478)

---

### Post by UbuntuNerd on 2008-07-29
you can check here there are a few options 

[http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html")

---

### Post by Locutus_of_Borg on 2008-07-30
the previous posts in this thread seem to deal with grub splash screens, whereas you seem to be wishing to change the usplash

you can create your own usplash, however it is difficult, but there are tutorials on google

an easier method is to download other already created usplashes and use one instead

i used:
[http://www.gnome-look.org/content/show.php/MacX+Usplash+Theme?content=73611](http://www.gnome-look.org/content/show.php/MacX+Usplash+Theme?content=73611)
when i was using ubuntu...

---

### Post by Mark Phelps on 2008-07-30
Actually, if you install startupmanager, it provides a fairly simple way to designate a variety of screens.

---

### Post by NoobuntuUser on 2008-11-09
I'm very new to Ubuntu, and am currently running Ubuntu 8.10 Intrepid Ibex. I decided I wanted to modify my splash screen, so I installed the startup-manager using "sudo apt-get install startupmanager". Now, when I try to run it, it shows a small loading screen saying "performing pre-configuration tasks", then closes after a couple of seconds. What do I need to do to get it to work?

---

### Post by darolu on 2008-11-09
It seems to be a bug on 8.10, I can't change my usplash either, very very few usplash themes work; the only solution I've found so far is to change usplash to splashy (different boot image application), but splashy themes are not so great, but at lest they work. If you want to do this first you need to uninstall usplash:
```
sudo apt-get remove usplash --purge
```
And then install splashy:
```
sudo apt-get install splashy
```
Then update your grub:
```
sudo update-grub
```
I had no problem with this but I've read some people need to add vga=791 to the end of their kernel boot options with:
```
sudo gedit /boot/groob/menu.lst
```
And edit this line:
```
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3dca6051-5877-438c-94c5-f5ff7803d851 ro quiet splash **vga=791**
```
NoobuntuUser, run it from terminal and tell us what error does it show there.
```
sudo startupmanager
```

---

