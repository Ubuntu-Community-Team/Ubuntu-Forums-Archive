---
title: "multi-keyboard solutions?"
date: 2009-01-25
forum: Hardware
---

### Post by tylerisfat on 2009-01-25
So I run a desktop replacement laptop. I use a external keyboard and mouse when I'm at my desk, and I take my computer to classes and such.

I'm trying to find a way that when my external keyboard is connected, it is my primary keyboard, and my laptop keyboard gets remapped to a secondary set up, but when I unplug my external, my laptop keyboard goes back to default. This would be useful for programming a whole boatload of macros onto the laptops keyboard for gimp editing or just simple short-cuts.

anybody know of a way to do this?

---

### Post by cmay on 2009-01-25
i use an external usb keyboard for my asus eepc since the keys are too small for me to use. when i plug in the usb keyboard it just runs the keyboard with danish keyboard layout like it should. but i figure if you make anohter keymap and switch in keyboard preferences between the two keyboard layouts it could work. not that i am sure it will. i just dont think you can actually make it switch the layouts by it selv that easy. 
good luck finding something out.

---

### Post by tylerisfat on 2009-01-25
> **cmay said:**
> i use an external usb keyboard for my asus eepc since the keys are too small for me to use. when i plug in the usb keyboard it just runs the keyboard with danish keyboard layout like it should. but i figure if you make anohter keymap and switch in keyboard preferences between the two keyboard layouts it could work. not that i am sure it will. i just dont think you can actually make it switch the layouts by it selv that easy. 
good luck finding something out.

but is it possible to have the external and laptop keyboards set on different key maps simultaneously?

---

### Post by cmay on 2009-01-26
> **tylerisfat said:**
> but is it possible to have the external and laptop keyboards set on different key maps simultaneously?
i dont know. i would say i think not. i see the idea and i been trying to find something about it using google but it comes up with nothing. the thing is that the usb keyboard is plugged in and linux knows its a keyboard that should be used as a keyboard with the same layout as you specified with the standard one as far as linux is concerned. so if it was somehow possible then i think some shellscripting or other form of advanced tweaking customizing was needed. 
but i as said have not found anything about the subject on google yet. i could use multiple keyboards sometimes in my studio since some instruments and audi production programs could use a dedicated extra keyboard as controller. so i am very interrested finding something out also. i just dont see it can be done and if so how it could be done .

---

### Post by tylerisfat on 2009-01-26
> **cmay said:**
> i dont know. i would say i think not. i see the idea and i been trying to find something about it using google but it comes up with nothing. the thing is that the usb keyboard is plugged in and linux knows its a keyboard that should be used as a keyboard with the same layout as you specified with the standard one as far as linux is concerned. so if it was somehow possible then i think some shellscripting or other form of advanced tweaking customizing was needed. 
but i as said have not found anything about the subject on google yet. i could use multiple keyboards sometimes in my studio since some instruments and audi production programs could use a dedicated extra keyboard as controller. so i am very interrested finding something out also. i just dont see it can be done and if so how it could be done .

Yeah, i haven't found anything either. The closest i got was a windows application that allowed for multiple mouse and keyboard pairs to simultaneously operate, such as for brainstorm sessions with a group. but nothing for multiple keyboard layouts.

the only think i could think of is to get ubuntu to recognize the external as being something other then a keyboard. but i have not a clue.

---

### Post by cmay on 2009-01-26
i seen a post where a remote control in ubuntu did not work. the reason was that mythbuntu saw it as a keyboard so maybe its possible to somehow cheat ubuntu into believe that the other usb keyboard is not really a keyboard device. 

i dont know how to do that but the post (i lost the bookmark on it now) about how to get remote working by telling mythbuntu the remote is not a keyboard could maybe give a clue or two.

---

### Post by Keith_Beef on 2009-01-26
:-?
You want both the laptop AND the external keyboard to work at the same time?

I think that this should be possible, by declaring two input devices in /etc/X11/xorg.conf.

Maybe something like this:
```
Section "InputDevice"
	Identifier	"External Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd1"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"External Keyboard"
...


```

Note, that I've not tried doing this, but from looking at declarations of multiple input devices for controlling the pointer, a similar approach might work.

---

### Post by tylerisfat on 2009-01-27
> **Keith_Beef said:**
> :-?
You want both the laptop AND the external keyboard to work at the same time?

I think that this should be possible, by declaring two input devices in /etc/X11/xorg.conf.

Maybe something like this:
```
Section "InputDevice"
	Identifier	"External Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd1"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"External Keyboard"
...


```

Note, that I've not tried doing this, but from looking at declarations of multiple input devices for controlling the pointer, a similar approach might work.

would it then be possible to configure each keyboard to send different keymaps? and have the laptop keyboard default when the external is removed?

---

### Post by Keith_Beef on 2009-01-27
> **tylerisfat said:**
> would it then be possible to configure each keyboard to send different keymaps? 
I would guess this to be the case.

Imagine this:
```
Section "InputDevice"
	Identifier	"Keyboard1"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd1"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection
Section "InputDevice"
	Identifier	"Keyboard2"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd2"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"el"
EndSection
Section "InputDevice"
	Identifier	"Keyboard3"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd3"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection
```

Now, I don't know how you would ensure the association between the Greek keyboard and the /dev/input/kbd2 device, but maybe it can be set up somehow...

> **tylerisfat said:**
> and have the laptop keyboard default when the external is removed?

I'm not sure that I understand this question. If we're talking about both keyboards being active when the external keyboard is connected, then it follows that the laptop keyboard is still active when the external keyboard is disconnected.

---

### Post by tylerisfat on 2009-01-27
> **Keith_Beef said:**
> I would guess this to be the case.

Imagine this:
```
Section "InputDevice"
	Identifier	"Keyboard1"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd1"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection
Section "InputDevice"
	Identifier	"Keyboard2"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd2"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"el"
EndSection
Section "InputDevice"
	Identifier	"Keyboard3"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/kbd3"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection
```

Now, I don't know how you would ensure the association between the Greek keyboard and the /dev/input/kbd2 device, but maybe it can be set up somehow...



I'm not sure that I understand this question. If we're talking about both keyboards being active when the external keyboard is connected, then it follows that the laptop keyboard is still active when the external keyboard is disconnected.

well what i'm wanting set up is for the external to be set as the standard, default keymap when it is plugged in, and the laptop keyboard to be set to something i define. but when i unplug the external, i want to laptop keyboard to be able to be easily switched (or automatically) to the standard, default keymap.

---

### Post by Keith_Beef on 2009-01-28
> **tylerisfat said:**
> well what i'm wanting set up is for the external to be set as the standard, default keymap when it is plugged in, and the laptop keyboard to be set to something i define. but when i unplug the external, i want to laptop keyboard to be able to be easily switched (or automatically) to the standard, default keymap.

Right... I understand better now.

I don't have a good idea how you could do that, but usually whatever you can do with a pointy-clicky tool is possible through the command-line, too.

I use the Keyboard Indicator Plugin to layout to change layouts without quitting a session, so if you can find out how that plugin works, you should be able to figure out a command that you can execute in a terminal window to have the same effect.

I think that a good candidate for switching layouts would be setxkbmap. Try reading the man page for that command, and see if you understand it better than I did. (After reading it, I'm convinced it is possible to do what I've described. But I think that my imagined xorg.conf file should probably not list several "CoreKeyboard" lines....)

After that, if you can find a way to detect the event of unplugging your USB keyboard, you can execute the command to change layouts whenever that event happens.

Good luck.

---

