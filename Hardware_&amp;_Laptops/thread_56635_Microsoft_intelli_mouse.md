---
title: "Microsoft intelli mouse"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-08-13
Hi guys...

My mouse has 2 extra buttons for back/faorward on the side. however these are not doing it properly. it actually right clicking when I press either one.
how can I setup the mouse buttons? 

thanx again

---

### Post by lithium- on 2005-08-13
Change the mouse section in your /etc/X11/xorg.conf
Important are the Options 'Protocol', 'Buttons' and 'ZAxisMapping'.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
EndSection


``` 

My Intelli Explorer is connected via usb. 
Restart X after saving.

Cheers,
lithium

---

### Post by floyd27 on 2005-08-14
I cant access that file..
when i type it in it says 

roderick@ubuntu:~$ su
Password:
root@ubuntu:/home/roderick # /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
root@ubuntu:/home/roderick # sudo /etc/X11/xorg.conf
sudo: /etc/X11/xorg.conf: command not found
root@ubuntu:/home/roderick #

---

### Post by raghav_p on 2005-08-14
try 

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Louie0228 on 2007-04-23
I have the same mouse and am trying to get the buttons working, I have changed the mouse section in my xorg.conf file and it now says exactly what you have written here but when I reboot I loose the cursor and the buttons don't work either.
Thanks
Lou

---

### Post by Sunflower1970 on 2007-04-23
Look here: [http://ubuntuforums.org/showthread.php?t=246770&highlight=multi+button+mouse](http://ubuntuforums.org/showthread.php?t=246770&highlight=multi+button+mouse)

This guide worked for me and my two 5-button intellibutton mice

---

### Post by Louie0228 on 2007-04-23
Thanks, that guide worked in so much as the buttons on my mouse now work, but when I re-boot I have no cursor, not sure why.
Lou

---

