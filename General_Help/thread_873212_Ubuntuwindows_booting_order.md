---
title: "Ubuntu/windows booting order ???"
date: 2008-07-28
forum: General Help
---

### Post by JnMrno on 2008-07-28
Hi, I just installed Ubuntu on a second hard-drive. I want to have it as second choice boot, but, when I turn on the pc, even though it asks me which OS I want to login in, after several seconds if I don't move the arrow down it logs into Ubuntu automatically since it is first in the list. How can I change orders, and make Windows the one to login automatically? (my dad won't know how to use Ubuntu or choose between OS) (I have to share this PC)

Thnks

---

### Post by kuja on 2008-07-28
option 1) edit /boot/grub/menu.lst and comment out the "delay" line. 
option 2) edit /boot/grub/menu.lst and add a line "default #" where # is the one you want to load first, count down the options in the menu.lst, if windows shows up third, do "default 3" (I think .... unless it starts counting at 0)

---

### Post by geirha on 2008-07-28
Hit Alt+F2 to get the run command dialog or open a terminal and run ```
gksudo gedit /boot/grub/menu.lst
```

That's the file that determines the boot menu. You should see a section of about 5 lines at the end corresponding to the windows entry. 
E.g.:```
title       Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader +1

```
Move those lines just above the line that reads ```
### BEGIN AUTOMAGIC KERNELS LIST
``` It's important that you put it above that line, and not below it.

After that, windows will be listed first in the boot menu, and will also be the OS chosen if you don't hit any keys

---

### Post by Spaceman9 on 2008-07-28
The easy way is to install StartUp-Manager from Synaptic. Then you can pick out the kernel you want grub to boot up with by default as well as pick a wallpaper for grub, change the color of the text, change the time out in grub and more. StartUp-Manager will even make a bootable back up of grub on a floppy disk with just one click or your mouse.

---

