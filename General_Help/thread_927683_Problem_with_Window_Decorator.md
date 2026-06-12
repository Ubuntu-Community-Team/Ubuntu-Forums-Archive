---
title: "Problem with Window Decorator"
date: 2008-09-23
forum: General Help
---

### Post by Coldness on 2008-09-23
Hey. I'm sorry if this has been asked and/or answered before (it's so hard to find the answer to your problem when you can't summarize your problem into a keyword search!).

Anyways, I've been playing around with window managers (emerald, compiz, etc) and I think I've wrecked the thing :P

I added somethings at startup, I played with window manager (in ccsm)...

So my problem is that when I start Ubunut, my windows don't have title bars and I don't have compiz-fusion effects!

I tried some commands I dug up on the internet (mostly from here) like, emerald --replace and such..

when I type emerald --replace... nothing happens.
sometimes when I type gtk-window-decorator.. It fixes stuff for me.. But only sometimes!

when I type metacity --replace, it works but apparently without compiz plugins...

lastly, sometime when I type compiz --replace it gives me back my title bars but without the borders... (I think without metacity effects?)..

So help please! I want to have full compiz-fusion effects while having the metacity effect (that is window borders change according to theme)...

PS: When I type compiz --replace I get this:

```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (mag) - Warn: GL_ARB_fragment_program not supported. Fisheye mode will not work.
```

---

### Post by JECHO on 2008-09-23
> **Coldness said:**
> Hey. I'm sorry if this has been asked and/or answered before (it's so hard to find the answer to your problem when you can't summarize your problem into a keyword search!).

Anyways, I've been playing around with window managers (emerald, compiz, etc) and I think I've wrecked the thing :P

I added somethings at startup, I played with window manager (in ccsm)...

So my problem is that when I start Ubunut, my windows don't have title bars and I don't have compiz-fusion effects!

I tried some commands I dug up on the internet (mostly from here) like, emerald --replace and such..

when I type emerald --replace... nothing happens.
sometimes when I type gtk-window-decorator.. It fixes stuff for me.. But only sometimes!

when I type metacity --replace, it works but apparently without compiz plugins...

lastly, sometime when I type compiz --replace it gives me back my title bars but without the borders... (I think without metacity effects?)..

So help please! I want to have full compiz-fusion effects while having the metacity effect (that is window borders change according to theme)...

PS: When I type compiz --replace I get this:

```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (mag) - Warn: GL_ARB_fragment_program not supported. Fisheye mode will not work.
```


first things first...

what did you add at startup?

---

### Post by anotherdisciple on 2008-09-23
Let me try to clear things up a little bit.

Compiz and Metacity are Window Managers. Metacity is the default for ubuntu and it has no special effects. Compiz can be enabled and it includes all of your desktop effects. 

If you type:
```
compiz --replace &
```
It replaces Metacity with Compiz. Meaning you enabled the effects.

If you type:
```
metacity --replace &
```
It replaces Compiz with Metacity. Meaning no effects.


Now Emerald and GTK-Window-Decorator are just that... window decorators. The put the borders on your windows. The default is gtk-window-navigator, emerald must be installed in order to use it.

By typing:
```
emerald --replace &
```
You replace gtk-window-decorator with Emerald.

By typing:
```
gtk-window-decorator --replace &
```
You replace emerald with gtk-window-decorator.

Okay.. that should be clear. Now about your problem. If you want the desktop effects you have to replace Metacity with emerald. If you want the normal gnome window borders, you have to replace emerald with gtk-window-decorator.

Type this into your terminal...

```
compiz --replace &
gtk-window-decorator replace &
```
The "&" is important... so make sure you type it in... it makes the process run in the background.

Also, in your compiz settings manager make sure you have "Window Decorations" checked. That is very important in making this work.

If you are still having trouble let me know!

---

### Post by Coldness on 2008-09-24
> **JECHO said:**
> first things first...

what did you add at startup?

Well first I followed the instructions here.. [http://ubuntuforums.org/archive/index.php/t-463928.html]("http://ubuntuforums.org/archive/index.php/t-463928.html").
Also I added this to start up: ```
compiz --replace
```

> **anotherdisciple said:**
> Let me try to clear things up a little bit.

Compiz and Metacity are Window Managers. Metacity is the default for ubuntu and it has no special effects. Compiz can be enabled and it includes all of your desktop effects.

If you type:
Code:

compiz --replace &

It replaces Metacity with Compiz. Meaning you enabled the effects.

If you type:
Code:

metacity --replace &

It replaces Compiz with Metacity. Meaning no effects.


Now Emerald and GTK-Window-Decorator are just that... window decorators. The put the borders on your windows. The default is gtk-window-navigator, emerald must be installed in order to use it.

By typing:
Code:

emerald --replace &

You replace gtk-window-decorator with Emerald.

By typing:
Code:

gtk-window-decorator --replace &

You replace emerald with gtk-window-decorator.

Okay.. that should be clear. Now about your problem. If you want the desktop effects you have to replace Metacity with emerald. If you want the normal gnome window borders, you have to replace emerald with gtk-window-decorator.

Type this into your terminal...

Code:

compiz --replace &
gtk-window-decorator replace &

The "&" is important... so make sure you type it in... it makes the process run in the background.

Also, in your compiz settings manager make sure you have "Window Decorations" checked. That is very important in making this work.

If you are still having trouble let me know! 

Well, when I tried your last piece of code, it really worked... But I have two questions left...

What should I type in "command" field in "Window Decorations" in ccsm?
Second, how to make this code applicable on start up?

Thanks in advance for both of you!

---

### Post by anotherdisciple on 2008-09-24
Once you replace the window manager and decorator... it should stay consistent even when you reboot... you shouldn't have to do this at login... try it out and let me know if that is true.

About the command in ccsm... I'll have to look it up when I get home tonight.

You may not need to enter anything... that command field may just be an override... If all is working... I wouldn't worry about it.

If your questions have been answered could you mark this thread as solved please? I have directions in my signature. Thanks!

---

### Post by Coldness on 2008-09-25
Nothing would please me more than to mark this topic as "Solved"! But I still have the problem!

I tried what you said. I typed in 

compiz --replace &
gtk-window-decorator --replace &

But nothing happens! I still have to retype those at every login!

I tried typing gtk-window-decorator --replace at ccsm Window Decorations (also compiz --replace, emerald --replace and metacity --replace), but nothing happens!

Can't I edit some configuration file somewhere that tell Ubuntu what is the currently used window manager? That would be much more easier... I'm sorry, but I still need help!

I'll keep on trying different combinations, but please try and find me a solution :)

PS: Isn't there some kind of code I could type to show me what window manager I currently have running? Maybe that would help me somehow...

---

### Post by presence1960 on 2008-09-25
I had the same problem, but i found that the compiz fusion icon under system tools click it and the icon will be in your task bar. Right click on it in your task bar and there are options to choose your window decorator, window manager, emerald etc. In window decorator and window manager choose compiz & emerald. Once I did this my settings stayed through a restart and I have had no problem since.

---

### Post by anotherdisciple on 2008-09-25
Try this.... open a terminal and type:

```
sudo aptitude install fusion-icon
```

That will install the compiz-fusion icon... now... open (System > Preferences > Sessions) and enter a new one.... use the command:

```
fusion-icon
```

... and name it whatever you want. That fusion icon is super handy... keeps you from having to type * --replace all the time... that should fix your issues... if it doesn't... I'll tell you how to make a script that will automatically run those commands at login... cool?

---

### Post by Coldness on 2008-09-26
OK sounds handy, indeed. I'll try it and tell you what happens ;)

---

### Post by Coldness on 2008-09-26
Ok... The problem is partially solved! The window manager (compiz) and window decorator (gtk-window-decorator) kick in at login! But there's one problem! It takes around 5 mins for it to actually work! 

I have to wait 5 mins at every startup before *any* of the startup scripts (the ones at sessions) start (including fusion-icon)! It starts up with only one virtual desktop, no window borders and if I try to run like say firefox, the system kinda bugs down (as in I can't open anything else and I can't function well... I can't even type commands at Terminal) That's weird! How can I fix this problem?! Why do I need to wait like 5 mins at every login?

PS: The fusion-icon is really cool ;)

---

### Post by anotherdisciple on 2008-09-26
hmmm... that's awful slow. Have you tried to do anything to speed up your computer?

For instance, go to (System > Preferences > Sessions) and turn off the stuff that you know you don't need... I always turn off Tracker and Evolution Alarm Notifier, since I don't use either of them.

Also, go to (System > Administration > Services) and turn off whatever you don't need in there. For instance, I don't have bluetooth built into my laptop, so I turn it off.

It shouldn't take 5 minutes though.. that's ridiculous! Try do do some tweaking like that and tell me if it makes a difference.

---

### Post by loomsen on 2008-09-26
[quote="You wrote in your first post"]
...
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present...
...
Checking for nvidia: not present.
Checking for Xgl: not present.
[/quote]

Do this and post your output:
```

wget http://blogage.de/files/3855/download?compiz-check_0.4-1_all.deb
sudo dpkg -i compiz-check_0.4-1_all.deb
compiz-check

```

This will give you, and us, some useful information.

*edit*
and, if you're on your way anyway, please post your xorg.conf as well.

---

### Post by Coldness on 2008-09-28
> **loomsen said:**
> Do this and post your output:
```

wget http://blogage.de/files/3855/download?compiz-check_0.4-1_all.deb
sudo dpkg -i compiz-check_0.4-1_all.deb
compiz-check

```

This will give you, and us, some useful information.

*edit*
and, if you're on your way anyway, please post your xorg.conf as well.

Here's the output:
```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```


I still have this slow-startup problem! I don't know it it's important, but I recently installed Avira antivirus (I'm dual-booting). In the process of installing, following a tutorial (can't remember the link), I had to install something to the kernel... I don't know it it's important or not, but it wouldn't hurt to know, either.

PS: sorry for the late responses, but the PC is not all mine...

---

### Post by Coldness on 2008-09-29
So.... any ideas? I don't wanna be forced to reinstall ubuntu! Please, there's gotta be something missing! Something causing my system to startup slow!

---

### Post by Coldness on 2008-09-30
What?! No replies so far?! C'mon! this problem can't be that hard! I wish I knew more of Ubunut, but then again, that's why I'm here! Please help me!

---

