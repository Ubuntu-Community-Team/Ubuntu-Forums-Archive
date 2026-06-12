---
title: "Can't disable touchpad"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Mandeep on 2006-08-18
I've tried every howto I've come across and I still can't disable my touchpad. I  have a usb mouse attached and I want to disable the touchpad. I can't disable the touchpad via bios so that's not an option. I tried using synclient but I get an error about SHMConfig even though I've added it to Xorg. I can't load qsynaptics and I'm all out of ideas.

BTW, I have a Dell XPS M140 laptop.

---

### Post by Speedboxer on 2006-08-18
Is there possibly a Touchpad Disbale button on your keyboard? Most Notebooks have icons on the F keys which do various things. On most modern Notebooks, there is a Touchpad Disable button. It should work under Linux. So if you find one that looks like it would do it, hold down the Fn key (usually located near Ctrl) and hit the appropriate F key.

---

### Post by gwayne on 2006-08-19
speedboxer, you solved my issue in [http://www.ubuntuforums.org/showthread.php?t=239198](http://www.ubuntuforums.org/showthread.php?t=239198) , so thanks!

---

### Post by Mandeep on 2006-08-19
no touchpad key to use with the fn key

---

### Post by Mandeep on 2006-08-19
ok i found the problem. i had to add some options under the shmconfig = true option. for example i added all those mouse accel etc options and then restarted. and for some reason that abled me to use synclient to turn off the touchpad.

---

