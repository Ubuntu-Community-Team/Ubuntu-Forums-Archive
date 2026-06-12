---
title: "Brightness adjustment not work - Samsung X360"
date: 2009-01-05
forum: Hardware
---

### Post by yetiicom on 2009-01-05
My laptop is SAMSUNG X360 and main system Ubuntu 8.10.
I have found that brightness adjustment buttons not work, more over gnome panel -> brightness adjustment too. After few hours I repaired it and wrote short tutorial, may someone find right name of brightness arrow short-cuts (FN + Up/Down Arrow), because I have to use alternative combination ShitKey (WinKey) + Arrow. This tutorial set right parameters for native console (ex. tty1-9), running by Ctrl+Alt+(F1-9) - they not work properly before (not work at all...). So let's go:


> 
Update for Ubuntu 10.04 users by [Joe Fleming]("http://joefleming.net/2010/03/30/samsung-x360-backlight-control-with-ubuntu/")
---------------------------------------------------------------------
Seems KMS is enabled by default for a certain chipset, specifically the Intel i915 chipset. I found out that KMS (Kernel Modesetting) disable BACKLIGHT_CONTROL parameter, so we have to turn off that future:

```
sudo gedit /etc/default/grub
```
Change: GRUB_CMDLINE_LINUX=""
To: GRUB_CMDLINE_LINUX="nomodeset"

Then run:
```
sudo update-grub
```



**I. Set brightness control and change console display.**

Add this command to System->Preferences->Sessions->> +Add (or System->Preferences->Startup Application->> +Add)
```
xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto
```

this command allow adjust LCD brightness by gnome brightness applet, and set about 40% brightnes default (180 set to 70%). Parts "--output VGA --auto" set graphic mode for console - check it by press Ctrl+Alt+(F1-9)

Check actual parameters, all changes should be list:
```
xrandr --prop
```


**II. Look for right keycode to set.**

```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

```

This will only output pressed keycode and currently assigned keysym, for example:

160 XF86AudioMute
174 XF86AudioLowerVolume
176 XF86AudioRaiseVolume


**III. Set short-cuts and right command to change brightness.**

install xbacklight:
```
sudo apt-get install xbacklight
```

check if you can change backlight from console (command repeated few times should take visible effect):
```
xbacklight -inc 10
xbacklight -dec 10
```


after test, type in terminal:
```
gconf-editor
```

A config editor window will open. Browse to apps -> metacity ->> global keybindings

Here you'll see "run_command_#" text boxes. Type the short-cut in the value box, if you still don't know right short-cuts try alternative <Super>Up / <Super>Down which cause change on press WindowsKey and Arrow Up/Down.  

To set the commands, browse to keybindings_command and type the command ("xbacklight -inc 10" or "xbacklight -dec 10", remember to leave apostrophes). All hacks will work if you have desktop effects disabled. If you have compiz enabled then you have to install ccsm package to edit short-cuts.

---

### Post by washakie on 2009-01-14
Just an ammendment...

This solution worked for me overall, and it seems that now things such as the powersave dimming, brightness screenlet, and perhaps others are working. Thank you!

One note for some who may have troubles:

For some reason I could not get the command to run at session login, so rather I created a shell script and added that shell script to the session login:

1) Create shell script (brightnessfix.sh):
```
#!/bin/sh
xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto

```

2) make executable:
%chmod +x brightnessfix.sh

3)Add this command to System->Preferences->Sessions->> +Add
Browse to your brightnessfix.sh file.

4) follow steps per remainder of original post.

---

### Post by avilella on 2009-02-09
Hi,

I took the liberty of creating a Linux Launchpad team for the people who own or develop for the Samsung X360 series laptop, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~samsung-x360](https://launchpad.net/~samsung-x360)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~10 users I've identified so far.

Cheers,

Albert.

---

### Post by FelixFBL on 2009-03-20
Hi

I'm kind of new in this Linux and OS business, so maybe some one could guide me a little more. 

yetiicom wrote

Add this command to System->Preferences->Sessions->> +Add
xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto

this command allow adjust LCD brightness by gnome brightness applet, and set about 40% brightnes default (180 set to 70%). Parts "--output VGA --auto" set graphic mode for console - check it by press Ctrl+Alt+(F1-9)


this is very helpful - I can easyli follow these directions.... I also understand how to run the gconf-editor in the terminal - and I found "global keybindings"....

 but then things get technical.. I have no idea what to do with the following directions........

Check actual parameters, all changes should be list:
xrandr --prop


II. Look for right keycode to set.

xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

This will only output pressed keycode and currently assigned keysym, for example:

160 XF86AudioMute
174 XF86AudioLowerVolume
176 XF86AudioRaiseVolume


III. Set short-cuts and right command to change brightness.

install xbacklight:
sudo apt-get install xbacklight

check if you can change backlight from console (command repeated few times should take visible effect):
xbacklight -inc 10
or
xbacklight -dec 10

Is it possible if someone can help me out!

/Felix

---

### Post by fojo on 2009-10-25
Hello, this is not working with the Karmic Koala (9.10RC) .

I remember having to roll back the driver for the INTEL in 9.04, does it have any relationship? Should we think it will be corrected in the 9.10 final version and/or with the 2.6.32 kernel?

Thank you in advance,

uname -a
2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

---

### Post by ariismail on 2009-10-29
> **fojo said:**
> Hello, this is not working with the Karmic Koala (9.10RC) .

I remember having to roll back the driver for the INTEL in 9.04, does it have any relationship? Should we think it will be corrected in the 9.10 final version and/or with the 2.6.32 kernel?

Thank you in advance,

uname -a
2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

Also, for me, it does not work with Ubuntu 9.10. Any suggestions?

---

### Post by iggus on 2009-11-01
Found some info here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617)

which worked for me on my X360... Quoting from that post:

> first : find the device address (here 00:02.0)
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 second :
setpci -s 00:02.0 F4.B=66 (a value between 00 and FF, where FF is 100%)
No idea what it does exactly but better than nothing as long as it works...

---

