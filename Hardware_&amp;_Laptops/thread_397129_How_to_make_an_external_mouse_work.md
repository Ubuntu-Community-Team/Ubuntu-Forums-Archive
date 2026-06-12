---
title: "How to make an external mouse work?"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by okok on 2007-03-30
I have 6.10 on a laptop computer. I installed the OS without a mouse connected to it, using the built-in touch pad. Now I can't make an external mouse work. I use a simple, generic,PS/2 optical mouse.

(and how come that in this day and age, auto-recognition of new connected hardware, and so basic such as simple, standard, mice, still isn't simply working?!)

---

### Post by albesan on 2007-03-30
hello,

have you tried rebooting with the mouse plugged in?

a.

---

### Post by okok on 2007-03-30
Thanks. Yes, of course. But it didn't work.

---

### Post by albesan on 2007-03-30
ok, 

Reboot with the mouse plugged in.
Make a back up copy of your xorg.conf  
then you can try to reconfigure the xserver using 

sudo dpkg-reconfigure xserver-xorg

Follow the onscreen instructions. You'll get to a point were you are asked about the mouse that you are using, select PS/2 mouse.

After doing this, reboot. If you have broken something in the process you will need to restore the backup of xorg.conf that you made earlier

good luck


a.

---

### Post by okok on 2007-04-23
This entry in xorg.conf solved the problem:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

---

