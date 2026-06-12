---
title: "Compiz won't keep settings"
date: 2008-08-25
forum: General Help
---

### Post by blueyelabs on 2008-08-25
Hi,

I just installed a fresh Ubuntu 8.04 os to replace the Windows partition (I'm re-arranging the hard-drives i.e. swapping windows and linux hds) and having installed the system I've tried to set up the right theming &c. for the different users so that the switchover from the old ubuntu installation (also 8.04) to the new one will be seamless.
This worked for all but one user account (my own) for which the compiz and emerald (and actually normal themeing) settings won't stick. They work after I force restart the xserver (ctrl-alt-backspace) but if I log out and then back in or reboot my profile is back to ubuntu defaults as far as looks go. It's unbearably frustrating.

Any help would be much appreciated; thanks in advance.

---

### Post by tuxxy on 2008-08-25
Do you mean emerald wont load up at login? if so you could try adding this command to your system > prefs > sessions

```
emerald --replace
```

---

### Post by blueyelabs on 2008-08-26
> **tuxxy said:**
> Do you mean emerald wont load up at login? if so you could try adding this command to your system > prefs > sessions

```
emerald --replace
```
It's more than that. All the compiz settings get reset (so stuff like "Desktop Cube" is no longer enabled), the normal gnome themes are reset back to default (I'd changed my theme to match the emerald decoration) and the emerald theme isn't working because compiz is no longer configured to use emerald as a decorator (it tried to use its own).
I will try adding "emerald --replace" to the session but I think the problem is a bit deeper because it works for all the other profiles but not mine.

---

### Post by blueyelabs on 2008-08-26
Adding ```
emerald --replace
``` to the session doesn't work. As I said, the problem is that my gnome theme settings aren't retained, nor are my compiz settings. My emerald settings are retained but aren't implemented because compiz isn't doing things properly.

---

### Post by blueyelabs on 2008-08-26
Ok.
I ran ```
compiz --replace
``` and it hangs with the following output:

```
gideon@Dell8400:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:554b (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Since compiz does actually work I'm confused about these problems (when I reconfigure compiz, gnome and emerald and then restart the x-server it's all themes beautifully, if I logout or shut down everything disappears).

```
emerald --replace
``` gives the following output:

```
gideon@Dell8400:~$ emerald --replace
/usr/share/themes/Vorta/gtk-2.0/gtkrc:174: Overlay image options specified without filename
/usr/share/themes/Vorta/gtk-2.0/gtkrc:187: Overlay image options specified without filename

gideon@Dell8400:~$ 
```

Although it doesn't hang, after decorating the windows and waiting for a bit, as soon as the next command prompt appears the decoration (as well and the close, minimise and zoom buttons) disappears.

This has to be a problem with my profile only, however, because all the other profiles work fine.

---

### Post by seriousproblem on 2008-08-26
I have a similar problem, and started a thread, but I'll let that die, because this one is more active. I enter compiz --replace, and get this:
```

tim@tim-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Segmentation fault

```
i see xgl isn't present... could that be my problem?
the thing is, it lets me set the settings, and the screen changes to reflect the different shading settings on my windows, but no animations work, and as soon as i close the compiz configuration box, it goes back to the most basic settings, and if i open it up again, it's reverted to "none" rather than extra or custom.

---

### Post by blueyelabs on 2008-08-26
Ok, I fixed the settings problem by changing the ownership of all the files in my $HOME folder with chown. The problem was when I copied my $HOME directory from the old installation leaving lots of folders with "root" as the owner... argh.

A new problem arose from this, however, in that now the gdm (login) screen is at completely the wrong resolution and I can't, no matter how hard I try, put it to the proper resolution. All the profiles are in 1280x1024 but the GDM screen looks like it's in 1024x768.

Help? Anyone?

---

### Post by blueyelabs on 2008-08-28
Anyone?

---

