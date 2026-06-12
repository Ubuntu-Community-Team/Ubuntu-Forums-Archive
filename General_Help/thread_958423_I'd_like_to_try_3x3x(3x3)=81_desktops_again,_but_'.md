---
title: "I'd like to try 3x3x(3x3)=81 desktops again, but 'Number of Desktops' won't change."
date: 2008-10-25
forum: General Help
---

### Post by BryanFRitt on 2008-10-25
I'd like to try 3x3x(3x3)=81 desktops again, but the 'Number of Desktops' won't change in Compiz-Fusion. 'CompizConfig Settings Manager - General compiz Options - Desktop Size'

I used to have Compiz-Fusion running with 3x3 virtual desktops per every desktop and I had 3x3 desktops (total = 81).  The newer version doesn't allow me to change the number of desktops to more than one.  Is there a way to get Compiz-Fusion to allow changes to number of desktops again?

Compiz-Fusion used one background for every virtual desktop on a desktop, and KDE changed the background on each desktop. I could move a window to a different desktop or a different virtual desktop within a desktop.

I could see why people could get confused by the number of desktops vs number of virtual desktops per desktop, but I understood it, and thought it was neat.

Together it created a neat way to organize all my windows, and it certainly helped me feel less claustrophobic.

Any ideas on how to get the desktops option back?

Thanks,

BryanFRitt

p.s. 'Desktop Preview & Pager - Compiz' is needed to do this nicely and not the default 'Desktop Preview & Pager'

p.s. now also posted at [http://forum.compiz-fusion.org/showthread.php?p=67374#post67374](http://forum.compiz-fusion.org/showthread.php?p=67374#post67374)

---

### Post by cl0ckwork on 2008-10-25
im not sure many people would need 81 different desktops, i know my head would hurt if i had to look at that all day

---

### Post by BryanFRitt on 2008-10-25
The desktop that a window is in can be changed (at least with the kde-window-decorator) by right clicking on the title bar and selecting 'To Desktop' and picking a desktop.  It would go to the same number virtual desktop that it was originally in.  The window could be dragged left, right, up, or down to switch virtual desktops within its current desktop. (Desktop Wall Plugin - Edge Flipping - Edge Flip Move) or it could set to switch when the mouse scroll button is used over the desktop.

Virtual desktops basically divide up desktops.  Virtual desktops are sometimes called viewports in some plugins.  Which is probably what they should be called under the 'General Options' sections, or viewports per desktop. That would make more since to me.

KDE (at least the 3.5.10 that I'm using) doesn't really have x*y desktops they have x desktops placed in so many rows(1,2,3 or auto) by the pager.

---

### Post by BryanFRitt on 2008-10-25
The most I've ever used was probably 2 or 3 Desktops with maybe 4 viewports used each.  I liked being able to have the same desktop background for different groups without having to set the background for each individually.  Having an odd number would make it so that the center could be the main thing I'm working on.  Desktops could be like for each class, and viewports like different tasks for each class.  Research one viewport, paper another, ideas and misc another.

---

### Post by BryanFRitt on 2008-11-14
I updated to Compiz .7.9 unstable and
_**The option came back!**_
I believe I got it from adding:
deb [http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/) ./
as given by [http://shame.tuxfamily.org/repo/?cat=11]("http://shame.tuxfamily.org/repo/?cat=11")
To manage repositories, and updating

afterwards for every Desktop I had to run
**dcop kicker default restart**
to get a taskbar
I had Konsole set to a shortcut key so I could do this:
Right-Click on the K-Menu->Choose Menu Editor->Find/Make Your Terminal Window Shortcut->Click on the Button with Current shorcut Key->Pick a Shortcut/Remember or Write Down->Then mess with number of desktops options...
You might have to do this for every desktop every time you change the number of desktops
-
Note: I also added
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-fusion-unstable
compiz-fusion-unsupported

You might have to add compiz-fusion-plugins-unstable BEFORE compiz-fusion-plugins-extra?  Maybe NOT install stackswitch from another repository?
-
p.s. 

for 3x3x(3x3) Set the taskbar size to 47 or 65 pixels to make the Compiz desktop pager look good.*

Some of the plugins that I've tried with the question mark don't work so well, especially with custom shortcut keys.

The pagers sometimes doesn't show some/all of the window previews or the windows on the wrong viewport?

The KDE pager only deals with a vertical virtual desktop size of 1 or desktop size of 1?

Regular Polygon would be a better name for the cube plugin.

The cube only deals with a Vertical Virtual Desktop Size of 1.

The taskbar (at least seams to) ignores the show windows from all desktops option.

If you chose hide icons, you can set the desktop background per viewport instead of per desktop using the wallpaper plugin.

You can make your taskbar panel not as wide as your screen and use that area to drag the cube or use it for the switch virtual desktop with mouse wheel over desktop option.

In Compiz pager mouse wheel will switch desktops instead of virtual desktops . In KDE pager it will switch virtual desktops, but 1st desktop only. (both can get confusing, maybe there should be an option to control this)

*I now have mine set to 3x3 for virtual desktops and 6 desktops using 2 rows (set the row option from the pager) and a taskbar size of 61 pixels (to get rid of weird dots in the pager with this setup of desktops and viewports on KDE 3.5.10, this might be different under KDE 4.2)

---

### Post by BryanFRitt on 2009-02-22
> As long as you have the Compiz 'Wallpaper' plugin disabled, everytime you boot up, login, logout, login again, and you'll be able to switch KDE desktops without the taskbar crashing.
[http://forum.compiz-fusion.org/showthread.php?p=71260#post71260](http://forum.compiz-fusion.org/showthread.php?p=71260#post71260)
#7

---

