---
title: "How to remove (for ever) a layout keyboard"
date: 2011-06-23
forum: Hardware
---

### Post by junix on 2011-06-23
Hi all,

The question is very simple:

How to remove (for ever) a layout keyboard ?

I change my keyboard physically and now I have 2 layouts... I've tryed to remove Brazilian Layout, but after rebooting, it comes again and again...

BR,

Junix

---

### Post by junix on 2011-06-24
I suppose that the problem is not in Gnome environment, because when I check in gconf, there is only one keyboard layout.

[IMG]http://img11.imageshack.us/img11/3883/configurationeditorkbd0.png[/IMG]

When the gnome session is loaded, it gets in somewhere the information about another old keyboard layout.

I guess.

Somebody ? Some tips?

BR,

Junix

---

### Post by junix on 2011-06-27
Anybody?

---

### Post by grahammechanical on 2011-06-27
Have you tried the Keyboard utility in System Settings? That has a tab to install and un-install keyboard layouts. We have a system where there are more than one way of doing things or more than one utility for making changes to configuration files. Could it be that a setting in one utility is not showing up in another utility? Just a crazy guess.

Regards.

---

### Post by junix on 2011-06-30
Hi grahammechanical,

As you see I don't have a tab to install and un-install keyboard layouts:

[[IMG]http://img810.imageshack.us/img810/5540/keyboardpreferences001.th.png[/IMG]](http://img810.imageshack.us/img810/5540/keyboardpreferences001.png)

I agree with you, but I suppose that Gnome is always getting the keyboard information from /etc/default/keyboard:

```
XKBMODEL="abnt2"
XKBLAYOUT="br"
XKBVARIANT=""
XKBOPTIONS=""
```

This is my old keyboard and I'm not using anymore, but every reboot, I have 2 keyboard layouts in my keyboard settings.

I've tried:

```
$ sudo dpkg-reconfigure keyboard-configuration
```

And my /etc/default/keyboard is this:

```
XKBMODEL="applealu_ansi"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS="terminate:ctrl_alt_bksp"
```

Until here, ok, but after of reboot I got:

[I][B]Error activating XKB configuration.
It can happen under various circumstances:
 &#8226; a bug in libxklavier library
 &#8226; a bug in X server (xkbcomp, xmodmap utilities)
 &#8226; X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
11001000

If you report this situation as a bug, please include:
 &#8226; The result of xprop -root | grep XKB
 &#8226; The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/B][/I]

---

### Post by junix on 2011-06-30
The problem was solved!

=)

Looking for to the new error, I found this:

> Richard Greenwood wrote on 2011-05-05:	 #9
Changing the keyboard model from "Apple Aluminium Keyboard (ANSI)" to "Apple" in the Keyboard Preferences solved this error for me.

Now, everything is OK.

Thank you.

---

