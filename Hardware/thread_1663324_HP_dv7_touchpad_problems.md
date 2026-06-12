---
title: "HP dv7 touchpad problems"
date: 2011-01-09
forum: Hardware
---

### Post by 3602 on 2011-01-09
Well i just went and exchanged my Gateway with this computer. You may see the specs in sig.
Now here's the problem(s). The touchpad has no right-click. Well, if I tap and click frantically at the bottom-right corner, the right-click menus do come up occasionally.
So I installed gpointing-device-settings from apt-get. I disabled tapping in it. However, when I try to re-open it (through System - Administration - Pointing devices), it will not start. I have purged and re-installed it, no avail.
Also, multi-touch or some sensing is wrong. When two fingers are placed on the touchpad the cursor will be crazy. So I cannot hold down the scroll bar with one finger and move with the other.
The system is Maverick 64-bit.
Thank you very much.

EDIT: Just purged gpointing again and rebooted (didn't reinstall). This time tapping works but still no right-click and cursor flies crazy.

---

### Post by 3602 on 2011-01-09
Alright. I "solved" (partially, keep reading) the flying-around problem by doing:
```
echo 'options psmouse proto=exps' >> /etc/modprobe.conf
```
Remember you need to *sudo su* first.
What it fixed was the erratic flying patterns and right-click. What it broke was everything you'd enjoy on a touchpad: multi-gesture, edge scrolling and whatnot. But I surfed through ID59C using bare-bones touchpad so I can live with this.
Also doing that will slow down (a lot) your pointer. To "solve" this, put sensitivity to minimum and greatly increase your acceleration. It won't have the same "feel", but at least it is fast enough and has a fixed and stable flight path.

---

### Post by larrybalz on 2011-04-03
I tested this on Ubuntu 10.10 on HP Pavilion dv7-4170us Entertainment Notebook.

I had the problem of right click not work and the mouse pointer erratically flying around. Also i cannot drag a window with out the pointer of if i have my mouse clicked, the window flying around. Also issue with scrolling, the same pointer flying around issue

This helped but did not entirely solve the problem but so much better and will get me by for now for now until a more permanent solution arrives.



Thumbs up to 3602 above and Lawford @ [http://forums.techarena.in/hardware-peripherals/1374809.htm](http://forums.techarena.in/hardware-peripherals/1374809.htm)


Partial Solution used..
Open your terminal 
```
Sudo gedit /etc/modprobe.conf
```

I do not know if other values should be present in there but mine was empty

Add 
```
options psmouse proto=exps
```
or```

options psmouse proto=imps

```
I do not know the difference but they gave me the same result but now i am currently using "options psmouse proto=exps"

Do not forget to restart your machine

I noticed remarkable changes where the flying pointer seem to reduce but the mouse was kinder slow. To make it faster goto System --> Preference --> Mouse.. Under pointer speed option increase the acceleration and other things to suit you.

---

