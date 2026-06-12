---
title: "Changing Keyboard Layouts"
date: 2008-09-30
forum: General Help
---

### Post by crimsongrim on 2008-09-30
can anyone give me step-by-step instructions on how to change my layout to Dvorák so that I'm not using Qwerty when I first log in.:(

---

### Post by Elfy on 2008-09-30
Run this from a terminal ```
cat /etc/X11/xorg.conf |grep Xkb
```

You need Option "XkbLayout" "dvorak" I believe, if it's not backup the file and change it - if it causes problems you can revert from a root prompt

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.3009
gksudo gedit /etc/X11/xorg.conf
```

If you are not sure then post the whole xorg.conf here.

If you need to revert, reboot into recovery mode, choose root prompt option in recovery menu then

```
cp /etc/X11/xorg.conf.3009 /etc/X11/xorg.conf
``` and reboot

---

### Post by crimsongrim on 2008-09-30
Thank you for the instructions, I hope I can make it work.

---

### Post by Icebear on 2008-09-30
or you can go to

System>Preferences>Keyboard

then hit the layout tab
then click the +add button

then choose keyboard, most likely you will want the usa keyboard

then click the variants the best one to your liking. 

You should be able then remove your old layout

---

### Post by Elfy on 2008-09-30
Indeed - I read into the op what wasn't there, assumption being that the keyboard layout was already set in Keyboard LAyouts ;)

If that is not the case and the layout is being lost on reboot then chnage as detailed above.

---

### Post by crimsongrim on 2008-09-30
thanks all for suggestions i will try again

---

