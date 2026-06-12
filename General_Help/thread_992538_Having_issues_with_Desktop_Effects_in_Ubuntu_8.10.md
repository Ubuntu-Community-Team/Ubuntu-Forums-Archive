---
title: "Having issues with Desktop Effects in Ubuntu 8.10"
date: 2008-11-24
forum: General Help
---

### Post by mmilitia9 on 2008-11-24
I just did a fresh install of Ubuntu 8.10.  I had effects with compiz in every other version that I could get it in, except for this one.  

I have a Nvidia Geforce FX 5500
I have the driver activated. (Version 173)


My xorg.conf is: 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

What can I do to make it work?

---

### Post by mmilitia9 on 2008-11-25
Aww man.. Anyone?  I have a feeling my xorg.conf shouldn't be so blank.  Back on 7.04 I had to edit the xorg manually and add like,


Driver "nvidia"

and other things I can't remember because I havent had to do it in such a long time.  I just feel the xorg file is way to blank compared to past xorg configurations.  Anyone?

---

### Post by CatKiller on 2008-11-25
Having the xorg.conf mostly empty is because of the new automatic X configuration methods, and is normal.

Running either ```
compiz --replace
``` or ```
gnome-appearance-properties
``` in a Terminal might give you some error messages to indicate where you should start to look to find what the problem is.

---

### Post by mmilitia9 on 2008-11-25
__________________________________________________________________

Running gnome-appearance-properties gave me
```
dominick@dominick-desktop:~$ gnome-appearance-properties

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

(gnome-appearance-properties:7174): Gtk-WARNING **: libQtCore.so.4: cannot open shared object file: No such file or directory

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:7174): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",
/usr/share/themes/MurrinaBleu/gtk-2.0/gtkrc:85: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/MurrinaBlue/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.

```

and running compiz --replace gave me
```
 

dominick@dominick-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

```

=\ Any more ideas? 


-Dominick

---

### Post by cicatrix1 on 2008-11-25
Looks like your card is on the blacklist.  Probably means it's not supported.  Do you know what card  you have?

---

### Post by CatKiller on 2008-11-25
> **mmilitia9 said:**
> running compiz --replace gave me
```
 

dominick@dominick-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

```

According to Google, that's some kind of integrated Intel thing that's been blacklisted. Instructions on how to tell Compiz to ignore the blacklist are described [here]("http://wiki.compiz-fusion.org/Hardware/Blacklist").

---

### Post by mmilitia9 on 2008-11-25
I think that's going to work. I haven't tried it yet, but I think it's right because I read on a website about the command compiz-check. The compiz-check gave me an error that it had two displays and it was to much to handle or something along those lines.  

When I had 7.04, I didn't know I had to disable in the BIOS the intel chip.  Once I figured it out, Ubuntu has always been a breeze to install and use.  Before that, display error after display error.  I wonder why compiz is picking up the intel now.. hm

---

### Post by elias.delatorre on 2008-11-27
> **mmilitia9 said:**
> I think that's going to work. I haven't tried it yet, but I think it's right because I read on a website about the command compiz-check. The compiz-check gave me an error that it had two displays and it was to much to handle or something along those lines.  

When I had 7.04, I didn't know I had to disable in the BIOS the intel chip.  Once I figured it out, Ubuntu has always been a breeze to install and use.  Before that, display error after display error.  I wonder why compiz is picking up the intel now.. hm
Hi there, Sorry, I have a Dell XPS 1330, with an Intel Graphics Card. First time I installed Ubuntu (7.10) the desktop effects worket pretty neat. Then, when I upgraded to Ubuntu 8.04 the screen resolution when using an external monitor stopped working, but the effects remained fine. Then this last time, I upgraded to Ubuntu 8.10 and the external screen resolution, along with the desktop effects stopped working. Do you still have this problem? Thanks.

---

