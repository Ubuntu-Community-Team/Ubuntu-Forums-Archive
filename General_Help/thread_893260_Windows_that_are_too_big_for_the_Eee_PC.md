---
title: "Windows that are too big for the Eee PC"
date: 2008-08-18
forum: General Help
---

### Post by wersdaluv on 2008-08-18
Some apps' windows (like compizconfig-settings-manager) are too big for the Eee PC 701. I am trying to drag those windows up so that I can see the lower part of the windows but I cannot drag the up because the upper panel stops me from doing that. I believe that if I can make windows pass through the gnome panels, this would be fixed.

Is there a fix for this?

---

### Post by Vivaldi Gloria on 2008-08-18
> **wersdaluv said:**
> Some apps' windows (like compizconfig-settings-manager) are too big for the Eee PC 701. I am trying to drag those windows up so that I can see the lower part of the windows but I cannot drag the up because the upper panel stops me from doing that. I believe that if I can make windows pass through the gnome panels, this would be fixed.

Is there a fix for this?

Press and hold ALT and now you can move windows around with your mouse.

---

### Post by sdennie on 2008-08-18
You should also be able to resize windows using Alt-Middle Click.  By default, pressing both mouse buttons simulates a middle click.

---

### Post by wersdaluv on 2008-08-18
@Vivaldi Gloria

That's what I do but the upper panel still won't let windows pass through it.


@Vor
I can't because those windows can't be made smaller.

---

### Post by Vivaldi Gloria on 2008-08-19
> **wersdaluv said:**
> but the upper panel still won't let windows pass through it.


I tried it and you're right. Don't know what you can do though.

---

### Post by mcduck on 2008-08-19
How about enabling the hide buttons on top panel (from right-click menu -> properties)? That way you could hide the top panel to either side of your screen to gain more desktop space, and that should also allow you to move the windows over the top of the screen..

---

### Post by cszikszoy on 2008-08-19
This should be what you're looking for:

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```


I'd also suggest checking out the EeePC page on Ubuntu's wiki for tweaks to the Ubuntu desktop.

[https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using)

---

### Post by 1337hippo on 2008-12-14
> **cszikszoy said:**
> This should be what you're looking for:

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```


I'd also suggest checking out the EeePC page on Ubuntu's wiki for tweaks to the Ubuntu desktop.

[https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using)

thanks!

---

### Post by Overide189 on 2009-05-11
Hi,
I know this thread is old but i came across it in my efforts to solve the same issue for myself but came up with another workaround that people might be interested in.  

Basically, it is making use of the expo plugin in Compiz fusion to see windows that are too large for the screen on an Eee pc. If you haven't heard of expo or compiz fusion you can see video of it in action here: [http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)  

Now, i think compiz was already installed to some degree before i installed a few extras and figured out this workaround. So, you may already be able to access the expo plugin. If its not available let me know and i will post in detail what i have installed. For now i will try to save me some typing and you some reading.  

First, you will need to set visual effects to at least normal mode. To do that go to: **system> preferences> appearance** then the **visual effects** tab. Once you select normal or extra mode it will take a few seconds to activate the new settings and then ask you if you want to keep the new settings.  

Instead of 4 horizontal desktops (like the video) we are going to tile them in a square 2 by 2 pattern.  

For this go to: **system> preferences> advanced desktop advanced settings** then go into the general settings **desktop size** tab at the top and select 2 horizontal and 2 vertical. Once that is done return to the main window and make sure the addon Expo under desktop addons is checked. 

Now **<special>e** should activate expo allowing you to see both desktops and select which one you want to view. A double left-click or single right-click on any of the desktops will select it and zoom back in.  

There is another way you can activate expo if you go into the expo settings and select the **bindings** tab. Expo edge can be activated so when you move your mouse to a specified edge or corner it will zoom out as if pressing **<special>e**. I tend to use a travel mouse instead of the touch pad so flicking the wrist to activate is a little easier and faster than performing a key combination. 

Photo of Expo in action on my Eee PC: [http://g.imagehost.org/view/0329/expo_screenshot](http://g.imagehost.org/view/0329/expo_screenshot)

I'll also note that i am still fairly new to Ubuntu and especially new to Ubuntu Eee and is my first post in these forums. hopefully this came across as helpful instead of confusing.

---

