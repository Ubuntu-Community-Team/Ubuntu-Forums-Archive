---
title: "Unable to miniimize, expand, close windows"
date: 2008-11-27
forum: General Help
---

### Post by gqstatus05 on 2008-11-27
It only happens when I enable Beryl. Here's a screenshot. Where should I check?  

[IMG]http://img.photobucket.com/albums/v687/BadBoyDiddy/beryl.png[/IMG]

---

### Post by eternalnewbee on 2008-11-27
Press **ALT-F2** and enter ```
metacity --replace
```
In your compiz manager enable the **window decoration** plugin

---

### Post by gqstatus05 on 2008-12-02
> **eternalnewbee said:**
> Press **ALT-F2** and enter ```
metacity --replace
```
In your compiz manager enable the **window decoration** plugin

Ok that didn't work out for me. I opened Compiz Manager when into the Windows Decoration properties and changed the command to: metacity --replace , hit close and refreshed Beryl. 

I still can't X, Minimize or move the window. Any other ideas?

---

### Post by Mahinva on 2008-12-02
I'd like to add that I am also having a similar problem however this occurs with the Emerald Theme Manager. Previously working flawlessly, my windows now resemble the screenshot provided in the first post. This occurred after upgrading from Hardy Heron to Intrepid Ibex. My themes appear in-tact when browsing the theme manager however selecting one does not make it apply.

When I start my computer, I have to launch the Compiz Fusion Icon and have Metacity selected as the window manager in order to get the standard close/minimize/maximize options and applicable boarder to show. Visual Effects revert to None when Metacity is enabled, and are set to Normal when Compiz is enabled. Emerald is selected as Window Decorator in both Metacity and Compiz modes, but this has no differing effect.

I also have Openbox as a Window Manager, however I have done nothing to manually install or modify Openbox - I suppose it was included with the OS upgrade.

I'm certainly at a loss and am unable to figure this out.

---

### Post by loomsen on 2008-12-02
Do you run gnome?

If so, open up gconf-editor and go to desktop/gnome/session/
You'll notice a new Key called required components.

Chose any Filemanager and Panel you prefer, and specify /usr/bin/fusion-icon as your default and required window-manager.

This value will override any other values, unless you have created a startup launcher for metacity.

[[img]http://www.ubuntu-pics.de/thumb/6704/screenshot_01_0QLOMs.png[/img]](http://www.ubuntu-pics.de/bild/6704/screenshot_01_0QLOMs.png)

However, you might as well hardcode fusion-icon to be your default-wm by editing 
**/usr/bin/gnome-wm** 
(I don't recommend this if you think you could forget about what you did)
If you still fancy trying it, add
**WINDOW_MANAGER=/usr/bin/fusion-icon**
above sm-id.
[[img]http://www.ubuntu-pics.de/thumb/6705/screenshot_02_ZZ5IVs.png[/img]](http://www.ubuntu-pics.de/bild/6705/screenshot_02_ZZ5IVs.png)

[color=red]NOTE: This really is not recommended if you don't know what you're doing
NOTE AS WELL: the place where fusion-icon is installed to in your system might differ from mine[/color]
To check where fusion-icon is installed run the which command:
> 
docter[~] which fusion-icon
          /usr/bin/fusion-icon
docter[~] 


Further you might want to take a look at the Howto Intrepid nvidia compiz in my signature. I don't know for sure if the issues I discuss there also apply to other video devices, but this might be the case. Just check if there is a group video with gid=044. If so, add yourself to that group.

Just check my sig, explained it a little more there.

---

### Post by gqstatus05 on 2008-12-03
Yeah thanks I'll take a look at that too. Somehow it's affecting my Windows Vista also. It's weird.  

When I log into Vista I can't minimize, close, move screens around. I have to manually close it from the dock on vista. 

I'll play around with it at work today and see if those steps  will help me out. Thanks.  I'll keep you posted.

---

### Post by Mahinva on 2008-12-05
Loomsen, I appreciate the length of detail you went to for providing possible solotions. After reading the first option, I am thinking that maybe I didn't describe my problem as simply as I should've. I haven't followed your first suggestion just yet because I don't think it'll take care of the exact problem I'm having.

If I run the Compiz Fusion Icon, I still can't get Emerald to work. I do not think it will make a difference if the icon is set as the default window manager because of this fact.

I have the feeling that this problem is rooted in the fact that I haven't reinstalled Envy to find drivers for my nVidia FX 5500 card. Whenever I set the visual effects to Normal, I again lose my title bar (min/max/close). I'm avoiding Envy because I've had a recurring resolution problem after OS updates when using Envy drivers - right now I suppose I am using a default driver.

If Envy/applicable drivers are required, I'll be slow to work this issue out because I've got at least one other post-upgrade problem (KeyTouch) to work out.

If you still think that setting the fusion icon as default will fix Emerald, I will give it a shot. I am not a proficient Linux user and do not really feel comfortable with rolling up my sleeves for the second solution.

Thanks for the input and sorry for the delayed reply.

---

### Post by eternalnewbee on 2008-12-05
gqstatus05.
Do you have **emerald** installed?
If yes, press **ALT-F2**, and enter ```
emerald --replace
```
If not, Go to Synaptic (Main Menu > System > Administration > Synaptic Package Manager) and search for **emerald**. Right-click, and install.
After the installation is complete: press **ALT-F2**, and enter ```
emerald --replace
```.
I believe this this should solve your problem.

---

### Post by Forlong on 2008-12-05
**gqstatus05**, you need to **get rid of Beryl right now. Beryl is dead.**

It is a discontinued project for over a year now, there hasn't been a release since **March 2007**. There is no support whatsoever.

The Beryl project has been succeed by the Compiz Fusion project, which is an enhancement of the Compiz window manager.
Both Compiz and the main components of Compiz Fusion are installed by default in Ubuntu 8.04

The root of your problem is most probably that you are trying to use the window decorators from Ubuntu's repositories. Those can not communicate with Beryl anymore, as they have been rewritten to run with Compiz.

So... un-install Beryl and whatever you installed with it. If you added a repository to install Beryl, get rid of it as fast as you can, because there is no repository for Beryl that works on Hardy.

If you need any assistance with that, just let me know.

---

