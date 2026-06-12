---
title: "Fujitsu Lifebook T4210 tablet buttons help"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by bongtothesoo on 2007-11-15
hello i am a complete noobie to linux and decided that ubuntu (gutsy) may be cool to install on my tablet pc. currently i am dual booting with gutsy as my primary os along with vista.

i am happy with most everything. adding/removing programs is a breeze and i think i am used to the synaptic package manager to some extent. i have also managed to get my stylus to work after reading through the forums.

one thing that i cannot figure out, however, is to get the tablet buttons and the brightness adjust keys (fn+f6,f7) to work. i've ran goolge searches and found out i needed the fsc_btns driver. i went to the website and read through the instructions but i cannot figure out what to do. i ran "modprobe fsc_btns" but i don't get any response and my buttons do not work.

when i type in the command "lsmod" i get "fsc_btns                9828  0"

i need help... i think it might be easier if someone could guide me through step by step starting from the beginning of downloading the driver instead of fixing it from here on... i'm afraid i am not knowledgeable about linux enough to follow...

---

### Post by bongtothesoo on 2007-11-15
can anybody help me please??? :(

---

### Post by mad9 on 2007-11-16
Hello! I have the same problem. 
I tried the gutsy packages on: [http://fjbtndrv.wiki.sourceforge.net/packages](http://fjbtndrv.wiki.sourceforge.net/packages) 
but it didn't work. (i have gnome not kde)

Try xmodmap!

[http://wiki.ubuntuusers.de/Xmodmap](http://wiki.ubuntuusers.de/Xmodmap) (german)

Type 
         ```
  xmodmap -pke > .Xmodmap 
```

into a terminal in your home-directory. 

Open it:
        
           ```
  gedit .Xmodmap 
``` 

Choose Functions ... 
(the keycodes for the buttons are: 143 / 220 / 203 / - / 158 )

and type 

           ```
   xmodmap .Xmodmap 
``` 

into the terminal.

It will be saved for the next sessions.



Now i can use the buttons for simple keybord functions...

But screen rotation, brightness control, acpi, microphone(of the display) doesn't work.

If you find something new, please tell me...

---

### Post by bongtothesoo on 2007-11-17
thank you so much. i'll be sure to check this out =)

---

### Post by khnz on 2007-11-19
> **mad9 said:**
> But screen rotation, brightness control, acpi, microphone(of the display) doesn't work.

You need a daemon or something that rotate the screen, fsc_btns only reports if the laptop in tablet mode or not.
Is the gnome brightness applet working on your tablet? If not, I think hal doesn't support your device. Do you have a brightness file in /proc/acpi/video? Please check the path in /usr/lib/hal/scripts/hal-system-lcd-[sg]et-brightness-fjbtn.

---

### Post by mad9 on 2007-11-20
> **khnz said:**
> 
Is the gnome brightness applet working on your tablet? If not, I think hal doesn't support your device. 

No gnome brightness applet doesn' t work.

> **khnz said:**
> 
Do you have a brightness file in /proc/acpi/video? Please check the path in /usr/lib/hal/scripts/hal-system-lcd-[sg]et-brightness-fjbtn.

No, but there are brightness files in:

./GFX0/DVI/brightness
./GFX0/TV/brightness
./GFX0/LCD/brightness
./GFX0/CRT/brightness

and i have only 

hal-system-lcd-get-brightness
hal-system-lcd-set-brightness

files.(without -fjbtn)

---

### Post by khnz on 2007-11-21
> **mad9 said:**
> ./GFX0/LCD/brightness

Looks good. Can you please send me the content of this file and the output of lshal (for your video card), and I will try to add support for your card.

> **mad9 said:**
> and i have only 

hal-system-lcd-get-brightness
hal-system-lcd-set-brightness

files.(without -fjbtn)

The files with -fjbtn are part of the fscd package (fjbtndrv repository). Currently it only supports the 85xGM chipset (of my Lifebook T4010).

---

