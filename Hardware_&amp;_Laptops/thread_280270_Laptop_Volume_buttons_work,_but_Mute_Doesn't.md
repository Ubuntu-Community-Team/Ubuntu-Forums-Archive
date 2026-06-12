---
title: "Laptop Volume buttons work, but Mute Doesn't"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by kingkookie on 2006-10-19
My issue is with a HP Pavilion ZE4547WM Laptop.  I've managed to configure KDE with a keyboard setting that gets my volume buttons working, but oddly enough, the third button, "Mute," doesn't work.  It's one that is supposed to light up when pressed, but for some reason it's not recognized.  I've tried various keyboard layouts, but no such luck. ](*,) 

Any ideas would be great.  Thanks in advance.

---

### Post by new_user_00 on 2007-10-23
sorry for diggin this thread out, but ...

i have the exactly same problem. os is kubuntu 7.10.
i just bought my new dell d630 with sigmatel 9205 audio controller. got sound working with this solution i found in the forums here

> 
...
the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
...


so i am happy since before that, sound didnt work at all. 
volume up and down work perfectly fine, but mute doesnt at all!

any help / ideas?

---

### Post by CheshireMac on 2008-01-05
I'm experiencing a similar issue, except that my mute light is stuck on. The computer senses that I press it, because it shows up on-screen. But the light won't go out, and sound doesn't work. 
I tried the above solution, but it did nothing. I'm running a HP nc8000 lappy.
Any thoughts would be appreciated.

---

### Post by jaz.spb on 2008-01-06
This solution is for ubuntu and kubuntu, and how can I configure my xubuntu to use volume buttons on Dell Inspiron 6400?

---

### Post by ugm6hr on 2008-01-06
> **jaz.spb said:**
> This solution is for ubuntu and kubuntu, and how can I configure my xubuntu to use volume buttons on Dell Inspiron 6400?

This might help: [http://ubuntuforums.org/showpost.php?p=2998469&postcount=2](http://ubuntuforums.org/showpost.php?p=2998469&postcount=2)

Off course, your volume may not be "Surround" - you will have to see which volume "channel" controls your speakers in *alsamixer*.

---

### Post by jaz.spb on 2008-01-06
thanks, but it didn't help me. True hotkey theme is already installed. But system does not responding when I'm pressing keys.

---

### Post by palec on 2008-03-05
I have a Dell Latitude D630 and after a successful installation of Ubuntu Gutsy and a bit of solving nosound issue I was glad to have the other two buttons (vol up/down) working out of the box but this one has not. Well, after a while looking for a solution I checked up *Preferences > Keboard shortcuts* and there was no shortcut for Volume mute (the very first item in the preferences). So I clicked on it to add a shortcut, pressed the mute button and that was it. Now it works.

---

