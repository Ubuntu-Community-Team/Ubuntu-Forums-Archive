---
title: "Broken login window"
date: 2008-07-17
forum: Hardware
---

### Post by gagnon88 on 2008-07-17
Hello 

I recently installed kubuntu on my Dell Inspiron 6000 laptop and the kubuntu login window is unreadable. All fonts are enormous and I can't see the fields to enter my password, nor anything... I managed to get around this by typing my password and hitting enter, but I cannot choose between KDE3 and KDE4.

Once the login window is passed, the resolution is just fine, but I wish the login window would display properly.

Any ideas?
Thank you

EDIT: My graphic card is the Intel 915G chipset and I have a 15.4" WXGA display.

---

### Post by ProbablyX on 2008-07-17
Try getting into a console and run (if you are on Kubuntu KDE4):
> 
sudo dpkg-reconfigure kdm-kde4


If that doesnt help:
> 
sudo aptitude --purge reinstall kdm-kde4


---

### Post by gagnon88 on 2008-07-18
Doesn't work.

What I need is to set the login window resolution to 1280x800. Any clues on this ?

---

### Post by vancedus on 2008-07-24
I am having the exact same problem with Ubuntu 8.04.  any suggestions anyone?

---

### Post by SurferGTO on 2008-07-30
im also having the exact same problem. i think ive tried every possible workaround suggesting from editing this and that and what not. the same thing was happening to my splash screen but now ive just disabled it. im using 1024x800. the session screen res is absolutely fine and right where i want it, but the login window (and priorly the splash screens) were not the same res. 

(technically right now, due to trying to fix this, my session res is wrong and im in a virtual window, but i know how to fix this. i hope)

---

### Post by SurferGTO on 2008-07-31
bump. it clearly has something to do with just using the themed login windows since going into login window>local tab and setting it to plain runs fine, using the same screen resolution as the session. editing the virtual screen resolution doesnt do anything.

---

### Post by SurferGTO on 2008-07-31
figured this out! you do have to edit /etc/X11/xorg.conf

> sudo gedit /etc/X11/xorg.conf

than go to the section titled "screens", should be directly under the secion titled "monitor". in the screen section, completely delete any and every reference to a resolution that ISNT what you want, specifically the line titled "modes" should have a list of resolutions. delete all of them or at least make the resolution you want to use first in the list. also, make sure that the "virtual" screen resolution matches the resolution you now have for "mode". 

that should work.

credit to [http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/]("http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/")

im gunna see if this also fixes the splash screen resolution problem. im guessin it should.

---

