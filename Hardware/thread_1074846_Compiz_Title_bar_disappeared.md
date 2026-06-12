---
title: "Compiz: Title bar disappeared"
date: 2009-02-19
forum: Hardware
---

### Post by threepwood960 on 2009-02-19
Hi, I have Ubuntu 8.10 on a Laptop Dell D430 with graphics intel 945GM. Initially Compiz worked ok, but 2 days ago I plugged the laptop in a dock with a 20'' screen and now the windows title bar has disappeared.

I have installed emerald, reinstalled intel drivers, modified xorg.conf..... But it is impossible. I now have to use metacity and can't recover the 3D effects.

Please help!

---

### Post by SketchyClown on 2009-02-19
My guess would be to go into Synaptic Package Manager and make sure that you have not installed or uninstalled anything that would have removed "gnome-panel". Search for that and make sure it is still installed.

Failing that, if you have the Compiz settings manager installed and have enabled transparency on the panel, make sure you have the transparency set so the panel is still somewhat visible.

Also if you are using a external display are you mirroring the displays or extended desktop.

I think unless you mirror them, the panel may only be visible on one of the displays at a time. At least thats how I remember it from OSX days.

Good luck.

---

### Post by Triggerhapp on 2009-02-19
ALT-F2 and then try either of these
```
gtk-window-decorator --replace &
```
```
emerald --replace &
```

---

### Post by threepwood960 on 2009-02-19
Thanks for the quick answer, the gnome-panel is installed and 'gtk-window-decorator --replace &' and 'emerald --replace' don't work. I think it is because now the graphics card is not recognized.

I now have to sleep (in here is late ;)), but tomorrow I will try to recover it. I passed all day trying...

Any more idea?

---

### Post by threepwood960 on 2009-02-20
Nothing... It is impossible recover my compiz. I have tested it with and without the external screen...

---

### Post by Kevbert on 2009-02-20
See if anything under Appearance-Visual Effects is ticked. If it is then you won't get compiz to work.

---

### Post by threepwood960 on 2009-02-20
It is checked 'none'. And when I try activate the effects it says me that it is impossible. Chipset configuration, isn't it? But I can't configure it.

---

### Post by threepwood960 on 2009-02-20
At last!!!!!!!!! It'll repair by itself. I don't know why. The last I made it was:
[COLOR="Navy"]sudo aptitude remove nvidia-settings[/COLOR]

And my xorg.conf is the same. I don't understand, but it works!

---

### Post by knit.manish07 on 2009-08-24
hiii 
i m having problem with title bar
it just disappeared and now it is creating a great deal of difficulty in windows management 
i found the answer too and it worked too but i have lost it
it was something starting from 
**gtk-**
can anyone please tell me that command

---

