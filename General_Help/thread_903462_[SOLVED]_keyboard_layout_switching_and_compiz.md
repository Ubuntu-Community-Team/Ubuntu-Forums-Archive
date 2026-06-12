---
title: "[SOLVED] keyboard layout switching and compiz"
date: 2008-08-28
forum: General Help
---

### Post by hoo2 on 2008-08-28
Hi,

I'm new to Linux and to Ubuntu also. I'm using kubuntu actually. I've just install compiz and the <alt>+<shift> combination stopped working. 
 
In the past i used to change the keyboard layouts with this combination but i haven't installed second keyboard layout. It was there for me from the beginning.When i was pressing alt+shift i was able to switch back and forward to Greek and English.

When i recognized the problem(alt shift), i tried to install the greek layout manually but nothing. I can't assign the alt+shift combination. The only think i get is something like shift+shift_L. If i change the layout from the icon to Greek the <cntl>+[xcv] combinations are gone also. It is like the <cntl> and <alt> keys are something else in the Greek layout.

The funny part, when i switch to kwin manager from the compiz-fusion icon i have no keyboard problems.

Does any one knows how to assign <alt>+<shift> with Greek layout installed or without it? And also how to get <cntl> and <alt> keys to work with the Greek layout like in the English layout in compiz? 

Sorry for my English.

---

### Post by hoo2 on 2008-08-28
**Solved !!!! **

OK.

After a "small" reading in Linux man pages and xkb, i decided to edit the /etc/X11/xorg.conf file manually. I opened this file and it was odd. That's because in the "InputDevice" section, there was no option for XkbModel, XkbLayout, nothing. it was like this:
```

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection 
```
In the same directory was a file named xorg.conf.buckup and another one called xorg.conf.<DATE>. Where <DATE> was a formated number to match the date i have installed nvidia drivers on my Linux system. In this file the InputDevice section for the keyboard was:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,gr"
        Option          "XkbVariant"    ","
        Option          "XkbOptions"    "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
EndSection
```

In that time i realize that **the problem wasn't the compiz but the nvidia drivers. The problem was in the file /etc/X11/xorg.conf**. The solution was simple. I've edit the file to look like this:
```

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,gr"
        Option          "XkbVariant"    ","
        Option          "XkbOptions"    "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
EndSection
```
And bum. after a X server reset everything was perfect.

***A simple How-to:***
1) Disable the keyboard layouts(In kubuntu go Menu-> System settings -> Regional & Languages -> Keyboard layouts)
2) Backup the settings 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nv

```
3) Open the /etc/X11/xorg.conf.<DATE> file
```

kate /etc/X11/xorg.conf.<DATE>
or
gedit /etc/X11/xorg.conf.<DATE>

```
    copy the following part to clipboard
```

        Option          "XkbModel"   xxxxxx  
        Option          "XkbLayout"  xxxxxx    
        Option          "XkbVariant" xxxxxx
        Option          "XkbOptions" xxxxx

```
     *NOTE: i haven't copy the 
```

Option          "XkbRules"      "xorg" 
```

4) Open the /etc/X11/xorg.conf file as superuser
```

kdesu kate /etc/X11/xorg.conf
or
gksudo gedit /etc/X11/xorg.conf

```
    paste the clipboard contents in order to have something like this 
```

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbModel"      xxxxx
        Option          "XkbLayout"     xxxx
        Option          "XkbVariant"    xxx
        Option          "XkbOptions"    xxxx
EndSection
```

5)Save and exit

6) pres <Alt>+<Ctrl>+<Backspace> to reset the X server

If this isn't working login in a console and type:
```

sudo mv /etc/X11/xorg.conf.nv /etc/X11/xorg.conf
startx

```


Sorry for my English.

---

