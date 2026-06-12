---
title: "5 button mouse and multimedia keyboard"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-05-30
How can I set the buttons to work like I want them to? Especially on the mouse, and volume/track controls on the keyboard? I know how to set the keybindings for GNOME but I'm using XFCE (Xubuntu).

---

### Post by Pragmatist on 2007-05-30
[https://wiki.ubuntu.com/MouseExtraButtons?highlight=%28mouse%29](https://wiki.ubuntu.com/MouseExtraButtons?highlight=%28mouse%29)

[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

---

### Post by malfist on 2007-05-30
> [https://wiki.ubuntu.com/MouseExtraBu...ht=%28mouse%29](https://wiki.ubuntu.com/MouseExtraBu...ht=%28mouse%29)

Doesn't exactly explain how to set the other mouse buttons to a specific behavior.

---

### Post by malfist on 2007-05-30
The faq on getting the multimedia keys to work didn't help much either, it said
> 
Use xmodmap to assign keycodes to your Media keys to make them available for the Xfce shortcut editor:

To determine keycodes of the multimedia keys use the program xev. Create a .Xmodmap file in your $HOME directory containing those keycodes and assign keysyms to them. [quote]
I don't know how to use those two programms.
I did this:
```

touch .Xmodmap
xev | tail .Xmodmap

```
And .Xmodmap showed nothing.
```

xmodmap

```
shows this:
[quote]
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)


---

### Post by Pragmatist on 2007-05-30
If you install the package "hotkeys" that should help you with the keyboard.

You might try installing "xbindkeys" to solve your mouse problem.  xbindkeys will allow you to trigger a command when you press a particular mouse button.  However, if you want to do things that are specific to your window manager (i.e. that don't have specific commands), such as resizing a window, then I'm not sure this will help you.  The ability to map buttons and keys to window behavior is the responsibility of the window manager.  I'd be surprised if XFCE had no such ability.

---

### Post by malfist on 2007-05-31
Well, with the windows driver I had the two extra mouse buttons set to double click, and kill process and I would like to do the same on ubuntu. I'll try what you said.

---

### Post by malfist on 2007-05-31
The keybindings witht the keyboard isn't working, this is my .XmodMap:
> 
keycode 144 = XF86AudioPrev
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 153 = XF86AudioNext
keycode 231 = XF86Refresh
keycode 230 = XF86Explorer
keycode 234 = XF86Back
keycode 233 = XF86Forward
keycode 232 = XF86Stop
keycode 178 = XF86WWW
keycode 236 = XF86Mail
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 223 = XF86Sleep

I set xmodmap to /home/jerome/.Xmodmap and rebooted. It doesn't seem to be working completely. It seems that only the XF86AudioPrev, XF86AudioNext, XF86AudioStop, and XF86AudioPlay are working.

---

