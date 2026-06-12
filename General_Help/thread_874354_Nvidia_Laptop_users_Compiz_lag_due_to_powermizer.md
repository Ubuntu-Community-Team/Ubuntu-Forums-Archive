---
title: "Nvidia Laptop users: Compiz lag due to powermizer?"
date: 2008-07-29
forum: General Help
---

### Post by conundrumx on 2008-07-29
Hello all,

I have a Thinkpad T61p with Compiz enabled.  A lot of times if I am on one workspace or window for a while my graphics card (Quadro 570M) will go to it's lowest power setting, which is especially good on battery.  However, when I try to change workspaces, windows, or anything requiring compositing there is a very noticeable slow down.

For me this has become one of those things that is just common enough that it becomes a nuisance, especially when I am trying to do something almost immediately after switching.

I'm not looking for a solution to this, not here.  I've seen a few other reports of people experiencing similar slow downs, and wanted to make sure it's not just a handful of oddballs.

[[IMG]http://brainstorm.ubuntu.com/idea/11600/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/11600/)

---

### Post by nfear24 on 2008-07-29
I also have noticed this, but only when using KDE. Really bad with 4.  When I use gnome everything is so fluid and nice.  KDE is better when I make the powermizer run full speed but gnome blows it away for me.  Now I am back to a gnome user just because its so fluid and nice looking.  Never jerky....

---

### Post by conundrumx on 2008-07-31
Bump, the idea on Brianstorm has gained some traction but I'd still like more feedback about the number of people affected.

---

### Post by steveneddy on 2008-08-01
My laptop does really well if I tweak this setting.

open CCSM

General --> Display Settings tab

Pull the refresh rate slider to the right as far as you would like to go.

Anything over 100 really makes a difference.

---

### Post by mrwoody on 2008-08-02
> **steveneddy said:**
> My laptop does really well if I tweak this setting.

open CCSM

General --> Display Settings tab

Pull the refresh rate slider to the right as far as you would like to go.

Anything over 100 really makes a difference.

are you sure that this solutions wouldn't spoil your screen? 
Anyway I have a similar problem: 
 [http://ubuntuforums.org/showthread.php?t=877640](http://ubuntuforums.org/showthread.php?t=877640)

I wonder if these problems are related (I also have a T61P with nvidia quadro FX 570m)

---

### Post by Loutrine on 2008-08-21
> **steveneddy said:**
> My laptop does really well if I tweak this setting.

open CCSM

General --> Display Settings tab

Pull the refresh rate slider to the right as far as you would like to go.

Anything over 100 really makes a difference.
I really think this needs to be <= your monitor's refresh rate.

I just tried upping mine to 100 on my Dell D830 (screen @ 50Hz IIRC) and it caused severe graphical artifacts, then stopped responding when I tried to use the Compiz Expo plugin.

---

### Post by chiccoch on 2008-08-28
I've been locking around for a solution concerning the slow performance of compiz with nvidia cards. I tried all kinds of scripts, xorg options and lots of other stuff.

Finally I found a simple solution. Installing "fusion-icon", starting it, then right-clicking on it and finally activating "Compiz Options"-> "Loose Binding" and "Indirect Rendering", brougth my system back to normal.

I now have plenty of performance, even with 10 movies playing and 30 firefox windows open...

---

### Post by conundrumx on 2008-08-28
I'm curious, you're saying you had poor performance in general before?  I only noticed slow downs when the garphics card was given sufficient time to go to it's lowest power setting.  This would generally only last for the first effect, then be back to full speed.

What do those options do that they would cause a change in performance?

---

### Post by TheMuffinMan616 on 2008-08-29
I have a Nvidia laptop with powermizer as well... and I know what you are all talking about. And I have a solution. I found this site which explained very nicely how to deal with some of the problems that arise when installing Ubuntu on my T61p and one of them was the powermizer lag. The author of the post designed a few scripts which actually turn powermizer off if your laptop is connected to AC power... I have noticed a huge performance increase!!

[http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p")

---

### Post by HanZo on 2008-11-17
hi everybody!
I have an XPS dell m1330 with an nvidia card. Performance has been pretty bad ever since, but especially with intrepid. Most visible when maximizing windows from the taskbar, then the window would appear like an all messed up jigsaw puzzle.
I tried to switch on loose binding, but could not see any real change, tried indirect rendering, got even worse. Last thing, I tried to set the refresh rate to 100... this made it all a bit better... but the thing is still there.
Has anybody had a similar problem?

---

### Post by nfear24 on 2008-11-17
> **TheMuffinMan616 said:**
> I have a Nvidia laptop with powermizer as well... and I know what you are all talking about. And I have a solution. I found this site which explained very nicely how to deal with some of the problems that arise when installing Ubuntu on my T61p and one of them was the powermizer lag. The author of the post designed a few scripts which actually turn powermizer off if your laptop is connected to AC power... I have noticed a huge performance increase!!

[http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p")

Just curious if most of you are using KDE?  I had the same problems with the powermizer, but once I switched to gnome never have had a problem and dont have to set it to max.

---

### Post by loomsen on 2008-11-17
> **HanZo said:**
> hi everybody!
I have an XPS dell m1330 with an nvidia card. Performance has been pretty bad ever since, but especially with intrepid. Most visible when maximizing windows from the taskbar, then the window would appear like an all messed up jigsaw puzzle.
I tried to switch on loose binding, but could not see any real change, tried indirect rendering, got even worse. Last thing, I tried to set the refresh rate to 100... this made it all a bit better... but the thing is still there.
Has anybody had a similar problem?

This is maybe, as many other problems, related to restrictive permissions the nvidia driver ships with.

You need to be a member of the group video, which should have gid 44, and permissions 0660. This will set permissions to acces your drivers direct rendering and other features. If you don't mind other users having access to direct rendering as well, lets say if you're the only user on your notebook or sth, you can set permissions to 0666 as well.

Add this to you xorg.conf. Just append it at the bottom:
```

Section "DRI"
     Group 	"video" 
     Mode 	0660
EndSection

```

Then check if you're in that group with the command groups. Simply open up a terminal and run it, should give you sth like this:
> 
me[~] groups
me adm dialout cdrom [color=red]video[/color] plugdev lpadmin admin sambashare jdown sabayon-admin
me[~] 


Then restart X server, and you should be fine.

---

### Post by jaygo on 2009-01-15
I don't have a group video in Ubuntu Intrepid ... anyone else?

---

