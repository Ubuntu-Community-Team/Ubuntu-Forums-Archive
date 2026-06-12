---
title: "New user, a few questions please"
date: 2008-07-31
forum: General Help
---

### Post by OJX on 2008-07-31
Using Ubuntu 64bit. Total linux noob.

1. My E4500 (oced from 2.2 to 3.0) is only showing up at its defult speed. Does linux get in the way of overclocking?

2. Fonts. They are pretty bad. Is there an easy way to make Ubuntu and Firefox use all the windows fonts?

3. Mouse settings. Where can I change how many lines the mouse scrolls. 

3.5 Also, I have the MX510 mouse with the buttons on the side where in windows I was able to go back and forth with the thumb (it still works with firefox going back and forth between pages) how do I make it work with the OS (going back and forth between directories)

4.Whats the best MSN - like client I can use, I dont really like the default one that comes with ubuntu.

5. I have an HD3870, are there any drivers for it, especially ones that would enable powerplay so that it can slow down in 2d mode to save energy and prevent overheating?

6. Is there any temperature monitoring software I can use to monitor CPU/GPU

7.Any other useful tips for a linux noob?

Thanks a lot in advance, if you cant answer all the questions, pls answer the ones you can.

---

### Post by Potatoj316 on 2008-07-31
4. pidgin is the best one (that i know of)
2. you can install the windows fonts (i think) try searching in synaptic for "font"

---

### Post by Darkade on 2008-07-31
> **OJX said:**
> 
2. Fonts. They are pretty bad. Is there an easy way to make Ubuntu and Firefox use all the windows fonts?

In your home make a .fonts folder and copy all your windows fonts there, remember that a folder which name starts with "." will be a hiden folder, you can see it again in nautilus by pressing CRTL+H
> 
4.Whats the best MSN - like client I can use, I dont really like the default one that comes with ubuntu.

You can try aMSN, tough it is kind of slow. Also emesene, it's a great project I use it myself and it's really fast, you should feel at home with it. Both can be installed from your main menu Applications>add/remove
or
```
sudo apt-get install emesene amsn
```
> 
6. Is there any temperature monitoring software I can use to monitor CPU/GPU

Conky is a monitor for your whole system, you can see some screenshots [here]("http://ubuntuforums.org/showthread.php?t=281865") and [this]("http://conky.sourceforge.net/") is the official site
> 
7.Any other useful tips for a linux noob?

check this threads:
[Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683")
[HOWTO: functional eye-candy with Avant-Window-Navigator]("http://ubuntuforums.org/showthread.php?t=762363")
[The Great Desktop Effects FAQ of 2008]("http://ubuntuforums.org/showthread.php?t=809695")
[Is Ubuntu for You?]("http://ubuntuforums.org/showthread.php?t=63315")
[TOP Ubuntu/Linux/Windows games]("http://ubuntuforums.org/showthread.php?t=427205")

---

### Post by YaroMan86 on 2008-07-31
> **OJX said:**
> Using Ubuntu 64bit. Total linux noob.

1. My E4500 (oced from 2.2 to 3.0) is only showing up at its defult speed. Does linux get in the way of overclocking?


No, but if you're overclocking using a specialized control panel on one operating system, then the overclocking would not carry on to the other operating system, since the overclocking would result from a setting being loaded at boot, not by way of the BIOS or a physical overclock which would take effect system-wide.

> **OJX said:**
> 
2. Fonts. They are pretty bad. Is there an easy way to make Ubuntu and Firefox use all the windows fonts?


Type the following in the terminal:

```

sudo apt-get install msttcorefonts

```

Myself, I actually really like a lot of the Linux fonts, especially monospace.

> **OJX said:**
> 
3. Mouse settings. Where can I change how many lines the mouse scrolls. 


I'm not entirely certain this is a setting, but you can check **System -> Preferences -> Mouse**

> **OJX said:**
> 
3.5 Also, I have the MX510 mouse with the buttons on the side where in windows I was able to go back and forth with the thumb (it still works with firefox going back and forth between pages) how do I make it work with the OS (going back and forth between directories)


I'm not sure how this is done. You might wanna search this forum for a HOWTO on configuring extra mouse buttons.

> **OJX said:**
> 
4.Whats the best MSN - like client I can use, I dont really like the default one that comes with ubuntu.


Use Pidgin. Its capable of doing just about every IM service out there. **Applications -> Internet -> Pidgin Internet Messenger**

> **OJX said:**
> 
5. I have an HD3870, are there any drivers for it, especially ones that would enable powerplay so that it can slow down in 2d mode to save energy and prevent overheating?


I don't know what an HD3870 is. Is that a video card? If so, you might wanna check the Restricted Driver Manager in **System -> Administration -> Hardware Drivers**. You might also need to Google it.

> **OJX said:**
> 
6. Is there any temperature monitoring software I can use to monitor CPU/GPU


There's several. There's a widget for the NOME panel called computertemp. Just search for programs for this in Synaptic. :)

> **OJX said:**
> 
7.Any other useful tips for a linux noob?


Be patient, be ready to learn. Google and these forums are your best friend when seeking support. And most of all, have fun.

> **OJX said:**
> 
Thanks a lot in advance, if you cant answer all the questions, pls answer the ones you can.

You're welcome.

---

### Post by silkstone on 2008-07-31
2. Install **msttcorefonts** from synaptic. You can easily install any additional TrueType fonts - please ask if you need to.

3. In Firefox, type **about:config** and scroll down to **mousewheel.withnokey.numlines**. In the Value column, enter the number of lines you want each click of the wheel to scroll. The default is 3 - I have mine set to 6.

6. Install **sensors-applet** from Synaptic. You can then add this to the panel (it's called Hardware Sensors) and it will display CPU and GPU temps.

7. Read the tutorials on these forums, especially this one...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by geirha on 2008-07-31
7. Read through the pages about Ubuntu 8.04 at [http://help.ubuntu.com](http://help.ubuntu.com) if you haven't allready. They contain alot of useful info. Also see [http://screencasts.ubuntu.com](http://screencasts.ubuntu.com) for alot of nice videos showing you how to do specific tasks.

---

### Post by OJX on 2008-08-01
[http://skiesofazel.deviantart.com/art/imetal-for-gnome-53789181](http://skiesofazel.deviantart.com/art/imetal-for-gnome-53789181)

How do I go about installing something like this
and does anyone know of a good font setup in appearance menu? just post a screenshot of yours please

---

### Post by Sef on 2008-08-01
> You can try aMSN, tough it is kind of slow. Also emesene, it's a great project I use it myself and it's really fast, you should feel at home with it.

Another difference is is that Amsn can do video, while emesene cannot.

---

### Post by Darkade on 2008-08-01
> **Sef said:**
> Another difference is is that Amsn can do video, while emesene cannot.

True, didn't mentioned it because I don't use video conferencing that much LOL I just forgot :lolflag:

---

### Post by chris4585 on 2008-08-01
> 2. Fonts. They are pretty bad. Is there an easy way to make Ubuntu and Firefox use all the windows fonts?

install the following package in the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

> 
4.Whats the best MSN - like client I can use, I dont really like the default one that comes with ubuntu.

I use emesene, which has no webcam support so for that i use amsn

> 6. Is there any temperature monitoring software I can use to monitor CPU/GPU


conky does that and way more.. howto set it up

```
sudo apt-get install conky
```

then open gedit and paste the follow into it:

```
use_xft yes
update_interval 0.7
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
alignment top_right
gap_x 10
gap_y 27

#colors
#D61B16 red
#00E15C green
#FFFFFF white
#000000 black
#D7B460 gold
#99082C other red like debian

TEXT
${color #FFFFFF}
$nodename $sysname $machine
Processes ${running_processes}/${processes}
CPU 
${cpu cpu1}% ${cpubar cpu1 15,200}
CPU
${cpu cpu2}% ${cpubar cpu2 15,200}
RAM 
$memperc% ${membar 15,200}
${exec acpi -t }
${color}
```

save the file as .conkyrc in your home folder

that might work

note thats my conkyrc config with some tweaking, feel free to edit it

---

### Post by Diabolis on 2008-08-01
Another IM client that I came to like is [emesene]("http://www.emesene.org/")

Its in the repository.
```
sudo apt-get install emesene
```

Tons of conky examples:
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+gui](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+gui)

---

### Post by chris4585 on 2008-08-01
> **OJX said:**
> [http://skiesofazel.deviantart.com/art/imetal-for-gnome-53789181](http://skiesofazel.deviantart.com/art/imetal-for-gnome-53789181)

How do I go about installing something like this
and does anyone know of a good font setup in appearance menu? just post a screenshot of yours please

you mean make ubuntu look like a mac? [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/")

---

### Post by Darkade on 2008-08-01
If you want your computer to look like a Mac check this site
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

there you can find the documentation and a full manual to do it :D

---

