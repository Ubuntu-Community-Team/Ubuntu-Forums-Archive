---
title: "[SOLVED] Swapping CAPS and Ctrl"
date: 2008-08-14
forum: General Help
---

### Post by victor.zamanian on 2008-08-14
Hello there!

I've grown accustomed to the caps lock key acting as the control key, and I'd like to set that up on this old laptop that has **Xubuntu** (see version below) installed on it.

```
$ lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
```

I know this can be done in the /etc/X11/xorg.conf file, but my fiancée is using this laptop as well and I'd like to set it up on a per-user level. I figure this would be done somewhere under my home directory.

How would I go about **swapping caps and ctrl on a per-user level**? Thanks for any assistance, may it be just a link to somewhere else. :-)

---

### Post by unutbu on 2008-08-14
Click System>Preferences>Keyboard, then click the Layout Options Tab. 
Then click the Ctrl key position triangle. This allows you to configure Ctrl/Capslock behavior on a per-user basis.

---

### Post by victor.zamanian on 2008-08-15
> **unutbu said:**
> Click System>Preferences>Keyboard, then click the Layout Options Tab. 
Then click the Ctrl key position triangle. This allows you to configure Ctrl/Capslock behavior on a per-user basis.

Those instructions are for Ubuntu. My keyboard settings are already configured on my Ubuntu computer. ;-) This one has **Xubuntu**.

In Xubuntu, there's an "Applications" menu, which leads to Settings->Settings Manager->Keyboard->Layouts, but there's nothing in there that I understand to have anything to do with Ctrl key behavior.

---

### Post by unutbu on 2008-08-15
Hey,:roll: it didn't say Xubuntu when I first posted. :)

Put this in a file name ctrlcapswap 
```

!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

```

(The above comes straight out of the xmodmap man page). Then the command 
```

xmodmap ctrlcapswap 

```
will swap your capslock and left control keys. 
There should be an Xubuntu way of running "xmodmap ctrlswap" at the beginning of your X sessions on a per-user basis.

For more options/info type "man xmodmap" and/or check out 
[http://c2.com/cgi/wiki?RemapCapsLock](http://c2.com/cgi/wiki?RemapCapsLock)
[http://www.manicai.net/comp/swap-caps-ctrl.html](http://www.manicai.net/comp/swap-caps-ctrl.html)

---

### Post by victor.zamanian on 2008-08-15
It did, I just think you missed it. ;-)

Thank you very much! I will try this later on the laptop and get back to this thread with an update if it worked.

/ Victor

UPDATE: It works like a charm. These are the steps I took to make this work:


[LIST=1]
[*]Create a text file containing the following text:
```
!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L
```
[*]Save it somewhere where you'd like it to be. I put mine in my home directory because most (all?) user configuration files are there, and I saved it as ".swapctrlcaps" with a "." at the beginning because that makes it "invisible" so you won't have to see it all the time if you browse your home directory.
[*]In Xfce, go to your Applications menu and navigate to Settings->Settings Manager->Autostarted Apps.
[*]Click the "Add" button and configure it as you wish, just make the command field say "xmodmap /path/to/file/.swapctrlcaps" (or whatever your file's name is) without the quotation marks. Make sure that the full path to the file is there (not "~" for your home dir!), otherwise it won't work (I tried).
[/LIST]
If you would like this to take effect immediately, just run
```
$ xmodmap /path/to/file/filename
```In any case, this will take effect next time you log in.

Thanks unutbu for the help.

---

### Post by unutbu on 2008-08-15
Thanks for the very nice write-up.

---

### Post by talmage on 2009-04-17
There is an easier way to do this using _setxkbmap_ and _xfce4-autostart-editor_.  You don't have to edit _/etc/X11/xorg.conf_.

First, to swap the control and caps keys, use _setxkbmap_:

```
setkxbmap -option "ctrl:swapcaps"
```

You can do that in an xterm.

To make it persist, use _xfce-autostart-editor_ to create an entry for it in _~/.config/autostart_.

You can find other options in _/usr/share/X11/xkb/rules/xorg.lst_.  Look for the entries following the line "! option".

---

### Post by unutbu on 2009-04-17
Thank you for this, talmage!

---

### Post by MountainX on 2009-11-06
> **talmage said:**
> There is an easier way to do this using _setxkbmap_ and _xfce4-autostart-editor_.  You don't have to edit _/etc/X11/xorg.conf_.

First, to swap the control and caps keys, use _setxkbmap_:

```
setkxbmap -option "ctrl:swapcaps"
```You can do that in an xterm.

To make it persist, use _xfce-autostart-editor_ to create an entry for it in _~/.config/autostart_.

You can find other options in _/usr/share/X11/xkb/rules/xorg.lst_.  Look for the entries following the line "! option".

There's a small typo in the command. It should be
```
# setxkbmap -option "ctrl:swapcaps"
```

I do not understand how to make this persist....

```
# xfce-autostart-editor
xfce-autostart-editor: command not found
```

Can I just create the file manually? What would I put in it?

---

