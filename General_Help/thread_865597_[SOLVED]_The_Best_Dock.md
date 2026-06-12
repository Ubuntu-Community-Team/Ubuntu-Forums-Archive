---
title: "[SOLVED] The Best Dock"
date: 2008-07-20
forum: General Help
---

### Post by jkyahoo101 on 2008-07-20
Where can I find a really good dock that I can use with Ubuntu 8.04? A dock like rocket dock for windows. That is the one thing I had in windows but don't have in Ubuntu right now.

---

### Post by poofyhairguy on 2008-07-20
> **jkyahoo101 said:**
> Where can I find a really good dock that I can use with Ubuntu 8.04? A dock like rocket dock for windows. That is the one thing I had in windows but don't have in Ubuntu right now.

I think the best is: 

avant window manager

It is easily installable through the add-remove program process.

---

### Post by kidux on 2008-07-20
The only problem with AWN is you need to be running compiz for it to work, and some people don't like to do that because of the resource hit on older machines.

---

### Post by poofyhairguy on 2008-07-20
> **kidux said:**
> The only problem with AWN is you need to be running compiz for it to work, and some people don't like to do that because of the resource hit on older machines.


Agreed. For them there is always the popular gdesklets (can be installed same way).

---

### Post by moonbeam on 2008-07-20
> **kidux said:**
> The only problem with AWN is you need to be running compiz for it to work, and some people don't like to do that because of the resource hit on older machines.

Most compositors will work.  Including the new metacity composite support (available in Hardy), xfwm4 composite support and eveb xcompmgr.  Compiz is definitely not required.  From the Ubuntu Hardy perspectve the metacity compositor is more than adequate if enabled.

---

### Post by kidux on 2008-07-20
> **moonbeam said:**
> Most compositors will work.  Including the new metacity composite support (available in Hardy), xfwm4 composite support and eveb xcompmgr.  Compiz is definitely not required.  From the Ubuntu Hardy perspectve the metacity compositor is more than adequate if enabled.

I hadn't realized metacity had compositor capabilities, that's really cool.

---

### Post by jkyahoo101 on 2008-07-20
Having compiz enabled is no problem anyway. The effects are nothing for my computer and I always have them enabled.

Is there any way to get it to the top of the screen and stop making it display open windows?

---

### Post by kidux on 2008-07-21
> **jkyahoo101 said:**
> Having compiz enabled is no problem anyway. The effects are nothing for my computer and I always have them enabled.

Is there any way to get it to the top of the screen and stop making it display open windows?

At the moment, there is no way to make it just a launcher, it only operates as both. That supposed to be something included in a future release.

As far as placement, I don't know if you can change it or not. I don't see any modification entry in AWN Manager, though it could be a matter of editing a text file.

---

### Post by Tim Sharitt on 2008-07-21
As of now, there is no way to move awn from the bottom of the screen. Cairo-dock has an option to move it to the top or sides, and there is an option not to show current running applications.

---

### Post by jkyahoo101 on 2008-07-21
Do you have any download links for Ubuntu 8.04?

---

### Post by stldirty on 2008-07-21
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by flytripper on 2008-07-21
how do you enable it for metacity then? when ever i disable compiz, my awn dissapears.

---

### Post by stldirty on 2008-07-21
> **flytripper said:**
> how do you enable it for metacity then? when ever i disable compiz, my awn dissapears.

in a terminal type

```
sudo apt-get install xcompmgr
```

then go system > preferences > sessions and add a new entry to ur startup list with the command xcompmgr -c -f -n so it loads everytime u restart.

---

### Post by Tim Sharitt on 2008-07-21
> **flytripper said:**
> how do you enable it for metacity then? when ever i disable compiz, my awn dissapears.

Open gconf-editor and goto apps > metacity > general. Check the box by compositing_manager.

---

### Post by jkyahoo101 on 2008-07-21
Thanks for all the help but I have one problem with Cairo Dock. (see pic) How can I make it so maximized windows cover it?

---

### Post by conundrumx on 2008-07-21
A quick google search yields [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

---

### Post by moonbeam on 2008-07-21
> **kidux said:**
> At the moment, there is no way to make it just a launcher, it only operates as both. That supposed to be something included in a future release.


If you have a repo that enables the vala applets it's just a simple matter of removing the Launcher/Taskmanager applet and adding as many simple-launcher applets as desired.  Note that awn will likely exit when removing the Launcher/Taskmanager so I suggest:

1) start awn-manager.
2) exit awn.
3) remove the Launcher/Taskmanager Applet.
4) start awn.

After adding a simple-launcher it's just a matter of dragging and dropping the desired desktop file into the applet.

The awn-testing ppa has the applets in question (reacocard's does not):  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by Tim Sharitt on 2008-07-21
> **jkyahoo101 said:**
> Thanks for all the help but I have one problem with Cairo Dock. (see pic) How can I make it so maximized windows cover it?

On the 'Position" tan of the configuration screen, uncheck the box beside 'Reserve space at the edge of the screen for the dock?' and check the box beside 'Keep the dock below other windows?'

---

### Post by jkyahoo101 on 2008-07-21
Ya I figured that out a little bit after I posted. But thank you for all of your help.

---

### Post by mc4100 on 2008-07-21
> **Tim Sharitt said:**
> Open gconf-editor and goto apps > metacity > general. Check the box by compositing_manager.
Yep, or, in a terminal type:
```
gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  true
```
which will enable it, and to disable:
```
gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  false
```

I love the GNOME Devs for implementing this, compiz broke (as per usual;)), and this was need to keep AWN going strong.

---

### Post by chavanak on 2008-07-22
it is just my opinion that cairo dock is better than awn. May be the number of applets is less but the look and feel of cairo dock is great and ofcourse its more customizable

---

### Post by jkyahoo101 on 2008-07-22
> **chavanak said:**
> it is just my opinion that cairo dock is better than awn. May be the number of applets is less but the look and feel of cairo dock is great and ofcourse its more customizable

I agree.

---

