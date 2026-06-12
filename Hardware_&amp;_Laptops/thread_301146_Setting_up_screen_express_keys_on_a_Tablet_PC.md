---
title: "Setting up screen express keys on a Tablet PC"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by samba on 2006-11-16
Hi,

I've been trying to set up the express keys (the important buttons next to the screen) on my Tablet PC (Toshiba Portege m405) for quite a while, without success. In fact I'm getting confused with how the linux kernel reads these keys. But these keys are quite important in tablet mode, allowing to scroll up and down etc. So I would really like to be able to use them.

I've read in details the help page on Multimedia Keys, [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) . So here how it goes for my laptop. The express keys are recognized by the kernel. They are given some scancodes, which are then mapped to some keycodes, which is in principle good. But not really.

So first I go to a real console (ctl-alt-F1). Then I want to know what are the scancodes of these express keys, so I type "showkey -s" and try these express keys. What I get are combined codes; for instance, for the scroll up express key, I get the scancode
```

0xe0 0x5c 0x02
0x82 0xe0 0xdc
```
and similarly for other keys. Now the point is that for instance, the scancode of the key "2" is
```

0x02
0x82
```
So in X, when I press on the scroll up express key, it also gives a "2". This is understandable, since the linux kernel associates to the scancode "0x02 0x82" the keycode which is then mapped to "2", and so it does the same thing for the scroll up express key (since the other scancodes 0xe0 etc. assigned to the scroll up key seem to be lost somewhere, only the 0x02 0x82 seems to matter).

In other words, all of these express keys are assigned a scancode (actually a "combined" set of scancodes) by the linux kernel, but these scancodes (at least part of them) are the same as the scancodes of other keys on my keyboard! ](*,) So it looks like I cannot use say "setkeycodes" to set these scancodes to unused keycodes, since that would also set the scancodes of other keys on my keyboard.

So what can I do? How can I tell the kernel to assign **different** scancodes to the express keys? Or can I use these extra scancodes assigned to the express keys (they all have extra things like 0xe0 etc. assigned to them) to change the keycodes and keymaps assigned to these keys?

I'm sorry if this post is hard to follow, I'm really no expert with that and just trying to learn to be able to use these keys. But help would be very much appreciated...

Thanks a lot! :-)
vincent

---

### Post by samba on 2006-11-16
Right, so I got further. Basically, some of these buttons are mapped to "<Super>1", "<Super>2", etc., one is mapped to "Ctrl-Alt-Del" and another one is mapped to something else I forget. So I used these names to set these buttons using gnome-keybindings or metacity, following [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) .

Now my only remaining problem is the following. Basically, "<Super>1", "<Super>2", "<Super>3" and "<Super>4" are the four ends of the little joystick, which should go to scroll-up, scroll-down, scroll-left and scroll-right in order to scroll when in tablet mode; these are in fact the most important buttons. How do I set these? I can't use gnome-keybindings or metacity, as there is no such option. I tried to use gconf-editor for metacity to set these keys to call a script that I created using "xmacro" (as suggested in [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)) that redirect these four keys to the arrow-keys "up", "down", "left" and "right", but that doesn't work. Well, the script and xmacro work, but when I'm in say a web browser window and I hit "<Super>2", it doesn't scroll up.

How can I do that?

Thanks again,
Vincent

---

### Post by samba on 2006-11-17
It's getting better! :-) Following the nice post [http://tuxmobil.org/toshiba_portege_m200_tablet_linux.html](http://tuxmobil.org/toshiba_portege_m200_tablet_linux.html), I created a script 
> 
#!/bin/sh

orientation=`xrandr --query | grep "Current rotation" | awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
	/usr/bin/X11/xrandr --orientation right
        xsetwacom set stylus rotate CW
	/usr/bin/X11/xmodmap -e "keycode 11 = KP_Left"
	/usr/bin/X11/xmodmap -e "keycode 13 = KP_Up"
	/usr/bin/X11/xmodmap -e "keycode 10 = KP_Right"
	/usr/bin/X11/xmodmap -e "keycode 12 = KP_Down"
	/usr/bin/X11/xmodmap -e "keycode 14 = KP_Enter"
else
	/usr/bin/X11/xrandr --orientation normal
         xsetwacom set stylus rotate
	/usr/bin/X11/xmodmap -e "keycode 11 = 2 quotedbl twosuperior oneeighth twosuperior oneeighth"
	/usr/bin/X11/xmodmap -e "keycode 13 = 4 dollar onequarter currency onequarter currency"
	/usr/bin/X11/xmodmap -e "keycode 10 = 1 exclam onesuperior exclamdown onesuperior exclamdown"
	/usr/bin/X11/xmodmap -e "keycode 12 = 3 section threesuperior sterling threesuperior sterling"
	/usr/bin/X11/xmodmap -e "keycode 14 = 5 percent onehalf threeeighths onehalf threeeighths"
fi


and then assigned this script to the screen hotkey (which is <Super>6 ) using gconf-editor for the metacity app. In this script, I basically redefined the keys 1 to 5 to be the arrows and the enter key when the screen is rotated. And it works!

Well almost... it works everywhere, except for some reason in Firefox when the arrow keys do not scroll up and down... Why???

Note that by enabling in System->Preferences->Accessibility->Keyboard the Mouse Keys feature, I can also use the little joystick as a mouse in the tablet mode! Great! :-)

So only Firefox is left!

vincent

---

### Post by samba on 2006-11-17
For the record, this is explained in more details there: [http://www.math.upenn.edu/~vincentb/UbuntuPortege.html](http://www.math.upenn.edu/~vincentb/UbuntuPortege.html) .

---

