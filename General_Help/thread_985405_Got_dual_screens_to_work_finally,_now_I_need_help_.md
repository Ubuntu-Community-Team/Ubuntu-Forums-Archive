---
title: "Got dual screens to work finally, now I need help fixing the settings for both"
date: 2008-11-17
forum: General Help
---

### Post by PsychedelicWonders on 2008-11-17
Ok I have the 3-D cube effect in place with 4 work stations, they do what their supposed to do on one of the screens, but the other screen just has 2 screens to flip flop and no 3-D cube/sphere etc.  just 2 workstations.

How do I have the new monitor have this?

Also, on my 1st screen my menu tool bar is in the top centered, on the new screen it spans the top and is all broken up, where and how do I make the new screen have it in the middle and only show when I scroll the mouse over it?

I also see that if I try to drag a file from one monitor to the next, it only changes workspaces and not monitors.

Is that because I have it on separate view with workspaces?

Is there any way to drag from monitor to monitor AND have workspaces on separate view?

---

### Post by TeXtonyx on 2008-11-17
I'll mention one thing I did which was recommended to me. 
Use the same resolution on all screens unless there is a big
difference in their size like 17 to 22. 

The individual settings for each screen should be available
for change in nvidia-settings. I don't think that will mess
with the driver. But each time you change the settings, it
has to be saved to xorg.conf. Make a backup of xorg.conf.

If I remember rightly, after you change the settings, one can
preview the settings. One trick was to copy and paste this
content and make a new xorg.conf, since you have the old one
backed up. There used to be a problem with saving to xorg.conf
and I don't know if it has been fixed. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK makes a backup.

gksudo gedit /etc/X11/xorg.conf   , lets you edit xorg.conf
and you can select all the content and delete it, then paste
the content from the 'preview' mentioned above as long as you
have make a backup besides the automatic ones.

You can have one screen which is stretched out across all the
monitors. I don't know that you want that. You can dabble with
the different settings, experimenting to find what you like.
Just remember to keep a xorg.conf backup named xorg.conf.Works
so that if you don't like your changes, you can return to your
safety net of workable settings.

sudo cp /etc/X11/xorg.conf.Works /etc/X11/xorg.conf 
changes or xorg.conf back to the original working one and
preserves your backup. I used to name my xorg.conf file
with descriptive suffixes to keep track of the changes,
like xorg.conf.SameReso

I can't give you very detailed advice because I don't have your
graphic to work with and I have two screens, and it really does
not seem like a lot of fun, tuning these settings. So I suggest
trial and error after you make a xorg.conf backup. Perhaps a
reader with more experience with multiple monitors can make
a better suggestion. Good luck.

---

