---
title: "Tweaking XFCE once installed"
date: 2005-11-13
forum: General Help
---

### Post by j_baer on 2005-11-13
I have xubuntu installed and it is working but I am having trouble with the configuration.

1) System font is very small on my 1028x1024 display. Don't know how to change it.

2) My USB flash drive doesn't appear to be mounted. Don't know how to mount it.

3) My USB printers do not show up?

Any help would be greatly appreciated.

Thanks ...

---

### Post by aysiu on 2005-11-13
[QUOTE=j_baer]I have xubuntu installed and it is working but I am having trouble with the configuration.

1) System font is very small on my 1028x1024 display. Don't know how to change it.[/quote] There should be a place to adjust settings in XFCE settings. Poke around.

> 
2) My USB flash drive doesn't appear to be mounted. Don't know how to mount it. Type the command ```
gnome-volume-manager
```

---

### Post by rplantz on 2005-11-13
[QUOTE=j_baer]I have xubuntu installed and it is working but I am having trouble with the configuration.

1) System font is very small on my 1028x1024 display. Don't know how to change it.
[/QUOTE]
Click on Settings in panel then on User settings. Or Xfce Menu -> Settings -> Xfce 4 User Interface Settings.
> 
2) My USB flash drive doesn't appear to be mounted. Don't know how to mount it.

If you're using rox (Xfce Menu -> File Manager), click on the large up arrow at the upper left a couple of times until you get to the root of the file system. Then double-click on the media folder.

If you're using xffm, click on Fstab icon, then on the root icon, then on media icon.
> 
3) My USB printers do not show up?

I installed both my USB printers under gnome. They are usable under xfce. I assume the installation simply carried through.

By the way, when I upgraded to Breezy from Hoary, I had to remove my printers. Then I plugged both in, turned them on, then rebooted. When I added printers, both showed up.

One is a Samsung laser printer, the other an Epson all-in-one.

Even the scanner part of the Epson works. To test this, I just scanned an image, saved it as a .pmn file, copied that file to my USB flash drive, and opened it from the flash drive.

Bob

---

### Post by kelsey23 on 2005-11-13
[QUOTE=j_baer]I have xubuntu installed and it is working but I am having trouble with the configuration.

1) System font is very small on my 1028x1024 display. Don't know how to change it.

2) My USB flash drive doesn't appear to be mounted. Don't know how to mount it.

3) My USB printers do not show up?

Any help would be greatly appreciated.

Thanks ...[/QUOTE]
You could always use the shell too.
Place yor USB flash drive in you computer. Then type the following into the shell:

$sudo su

$mkdir /media/usb

$umount /dev/sdb1

$mount -t vfat -o rw,umask=0000 /dev/sdb1 /media/usb

$exit

Your USB drive should now be mounted with 777 permissions under /media/usb

---

### Post by j_baer on 2005-11-13
Thanks for all the help ...

I was able to adjust the fonts, but was unsuccessful with the USB.

I followed the xubuntu instructions which called for a server install and then XFCE.

I am going to try a standard gnome install and then load the xubuntu desktop.

Stay tune ...

---

### Post by j_baer on 2005-11-14
Why go a little when you can go alot ...

Decided to place XFCE on top of Dapper ...

No problem and everythings appears to be working. Wow what a nice clean user experience.

The only thing is I am still learning the file manager.

Thanks for the help ...

---

### Post by Kyral on 2005-11-14
What are you using? Rox or XFFM?

---

### Post by j_baer on 2005-11-15
Kyral,

I'm learning ROX at the moment. I have a couple of questions.

1) Can the window auto-resizing be turned off?

2) How do I mount a SMB share?

Thanks,

j_baer

---

### Post by Kyral on 2005-11-15
I actually dislike Rox and want to replace it with XFFM for those reasons. But also Thunar is coming out soon, I hope...

As for Samba, you can browse shares with XFFM by using the XFCE Network Server whatever (its close to that name, can't remember right now)

---

### Post by rplantz on 2005-11-15
[QUOTE=j_baer]Kyral,
I'm learning ROX at the moment. I have a couple of questions.
1) Can the window auto-resizing be turned off?
j_baer[/QUOTE]

Right-click in a ROX window. Select Options... Select Filer Windows.

Bob

---

### Post by j_baer on 2005-11-16
Thanks ...

Under Gnome I load the Beagle Damon with a session startup command. Is there something simular under xfce?

:p

---

### Post by Kyral on 2005-11-16
I don't think so...I really would like to know if there was, I'm tired of activating it manually

---

### Post by telmo on 2005-11-18
Easy! You just have to create a folder called Autostart on your desktop and a start.sh file inside it.

[B]mkdir ~/Desktop/Autostart
vi start.sh[/B]

You can add any programs you want to run on startup. I personally don't use beagle because i find it too slow.
This is my start.sh:

[B]#!/bin/bash
gdeskcal dpi=100 &
ivman &
rox -p=1 &
gdesklets &[/B]

As you can see i use rox filer with icons displayed on the desktop.

Be sure there's no hidden start.sh files on the folder, or the startup programs will run twice, and you'll find yourself 'ramless' ;)

---

### Post by rejser on 2005-11-22
Anyone tried thunar yet? What did you think, I found it to be the missing piece in xfce, though a little bit unstable yet

---

### Post by manicka on 2005-11-22
[QUOTE=rejser]Anyone tried thunar yet? What did you think, I found it to be the missing piece in xfce, though a little bit unstable yet[/QUOTE]

Looks just like nautilus

---

### Post by HunterCo on 2005-11-22
[QUOTE=j_baer]1) System font is very small on my 1028x1024 display. Don't know how to change it.[/QUOTE]
Just curious if that was a typo for 1280x1024 or if you really were running that resolution... ?? :)

---

### Post by Ozitraveller on 2005-11-26
I don't understand the menu maintenance, could someone please tell me:

How do I add Synaptic to the menus?

WOW ! I just did an update and the latest kernel was installed, now I splash is working.

Can anyone tell what the name of the application(s) that are used on the vertical window on the right-hand side of the DSL desktop are? They look like system monitors, I think...

Is there a lighter web browser than firefox 1.0.7, I'm finding it a bit sluggish? Dillo?

Who do I find out how much ram is being used? Is there a utility?

---

### Post by aysiu on 2005-11-26
[QUOTE=Ozitraveller]I don't understand the menu maintenance, could someone please tell me:

How do I add Synaptic to the menus?[/quote] I don't know. I've never gotten the XFCE menu editing to work properly. Synaptic didn't just pop in there? You can create a launcher for it in the panel: ```
gksudo synaptic
```

> 
WOW ! I just did an update and the latest kernel was installed, now I splash is working.

Can anyone tell what the name of the application(s) that are used on the vertical window on the right-hand side of the DSL desktop are? They look like system monitors, I think...

Is there a lighter web browser than firefox 1.0.7, I'm finding it a bit sluggish? Dillo? Sounds as if you just want DSL. Maybe you should use it? It comes with Dillo straight off, I think. But, yes, you can use Dillo or Epiphany or Lynx.

> 
Who do I find out how much ram is being used? Is there a utility? Try typing *top* in the terminal.

---

### Post by Ozitraveller on 2005-11-26
[quote=aysiu]I don't know. I've never gotten the XFCE menu editing to work properly. Synaptic didn't just pop in there? You can create a launcher for it in the panel: ```
gksudo synaptic
``` 
 Sounds as if you just want DSL. Maybe you should use it? It comes with Dillo straight off, I think. But, yes, you can use Dillo or Epiphany or Lynx.

 Try typing *top* in the terminal.[/quote]

No, unfortunately Synaptic didn't add itself to the menus, but I will add a launcher for it.

Yes I have tried DSL, and many others as well. At the moment it's just something to learn from, but just a little too frugal. I want to make my old Dell 300 into a server and Xubuntu would be ideal!

---

### Post by Dr.Who on 2005-11-28
There are some plugins for the panel you can grab from the repositorys, search for xfce4 in synaptic or apt-cache search xfce4. There are ones for showing cpu,ram and swap usage, networktraffic, hdd space, weather and more. After installing you have to add to the panel by rightclicking on it.

Cheers

---

### Post by Ozitraveller on 2005-11-28
[quote=Dr.Who]There are some plugins for the panel you can grab from the repositorys, search for xfce4 in synaptic or apt-cache search xfce4. There are ones for showing cpu,ram and swap usage, networktraffic, hdd space, weather and more. After installing you have to add to the panel by rightclicking on it.
 
Cheers[/quote]
 
Excellent! Thanks Dr. Who.
 
 
 
So, is Who on first?
Sorry, old joke. Abbott and Costello. :-)

---

### Post by rejser on 2005-11-29
Anyone found how to change workspace using win-keys
originaly it is ctrl + F1 for example, I would like Super_L (win key, right?) + F1

---

### Post by beeldings on 2005-12-04
How do I configure my printer under Xubuntu? I searched the forums and I searched Google, but I wasn't able to locate any relevant information. I can easily set up my printer under Gnome and KDE, but I don't know where to start on a fresh Xubuntu installation.

---

### Post by marksi on 2005-12-05
[QUOTE=Ozitraveller]I don't understand the menu maintenance, could someone please tell me:

[COLOR="Blue"]How do I add Synaptic to the menus?[/COLOR]

WOW ! I just did an update and the latest kernel was installed, now I splash is working.

Can anyone tell what the name of the application(s) that are used on the vertical window on the right-hand side of the DSL desktop are? They look like system monitors, I think...

Is there a lighter web browser than firefox 1.0.7, I'm finding it a bit sluggish? Dillo?

Who do I find out how much ram is being used? Is there a utility?[/QUOTE]


I added synaptic to my xubuntu desktop and it came up in the settings menu

---

### Post by steve k on 2005-12-06
i installed the xubuntu-desktop package last week and i've been working with it on and off, thunar looks great, since the existing file manager for xfce is a bit of a dud in my opinion...

my real question is:
my xfce sessions all seem to start with the xcompmgr program running,
this looks nice, provides some nice shadows and transperancy, but it does slow things down.  i'd like to fool around with it a bit, change settings, make things fade in and out or maybe take it out entirely: where do i find the necessary config file to work with that?

my other real question is: 
can i get rid of the xfce task bar? i find that i don't need one really and the notification area can be moved to the panel down below.

on another note i just updated my computer and suddenly the ubuntu bootsplash was replaced by the xubuntu boot splash, any idea where that boot-up graphic is stored and if it's easy to change? that'd be fun no?

anyone know how to do these things?

---

### Post by Basu on 2005-12-06
I have a few questions of my own:
1. I use ROX for icons, but how I can make ROX show the wallpaper beneath? I tried using transset to make it transparent, but it's not too pretty
2. Where are the XFCE startup scripts located? For some reason evolution-exchange and evolution-alarm are also loaded on login, making the load process take abnormally long.

---

