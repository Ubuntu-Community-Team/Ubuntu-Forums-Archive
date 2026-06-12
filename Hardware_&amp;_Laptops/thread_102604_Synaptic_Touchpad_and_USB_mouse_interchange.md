---
title: "Synaptic Touchpad and USB mouse interchange"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-12-12
I wonder if it is possible to automatically switch a touchpad when a USB mouse is plugged in and vice versa? Every time I type anything on my laptop, I touch the touchpad and a cursor jumps somewhere I do not need it. It is a bit annoying... I mostly use the mouse, but sometimes I need the touchpad.

---

### Post by Mr_Smiley on 2005-12-16
I was also wondering the same thing.

Does anyone know if this is possible?

Thanks.

---

### Post by CaptainMorgan on 2005-12-16
Im not aware of the specifics.. but you may want to read up on **xorg.conf** in case you don't already know about the file. Becareful with it.

---

### Post by migueljacq on 2005-12-16
I don't know if there is an option to switch to and fro. The touchpad always seems to be on, regardless of having an external mouse, unless you switch the touchpad off in the BIOS. I did this because my touchpad was faulty and causing me all sorts of grief. 
But if you want to switch back and forth, this isn't really a practical option.

---

### Post by Raoul Duke on 2005-12-16
If you are using the synaptics driver, you can disable it with the command 

synclient touchpadoff=1

If using the "mouse" driver, disable it with "modprobe -r psmouse"

I put this in a script and can hotkey it via acpi. On my Toshiba laptop this is Fn-F9, so it works according to the symbol on the fn key, just like it used to work with XP.

---

### Post by Mr_Smiley on 2005-12-17
[quote=Raoul Duke]If you are using the synaptics driver, you can disable it with the command 

synclient touchpadoff=1
[/quote]

That's what I was looking for. Thanks!

---

### Post by encinas on 2005-12-17
If you check the synaptic's changelog:

([http://web.telia.com/~u89404340/touchpad/files/changes.txt](http://web.telia.com/~u89404340/touchpad/files/changes.txt))

0.14.2 (2005-05-16)
- Added a hotplug script that disables the touchpad when a USB mouse
  is connected. (And reenables it again when the USB mouse is
  disconnected.) From Joergen Scheibengruber.

But, I've not tested yet.

---

### Post by lmp3 on 2005-12-17
i get the following error when i run synclient on my laptop (HP nc622):

> [mylaptop:~] sudo synclient touchpadoff=1
Password:
Can't access shared memory area. SHMConfig disabled?


any thoughts on how i should proceed?  i'm a relative newbie...

thanks.

---

### Post by Raoul Duke on 2005-12-17
[HTML][mylaptop:~] sudo synclient touchpadoff=1
Password:
Can't access shared memory area. SHMConfig disabled?[/HTML]

I think that means you are not using the synaptics driver...in that case you can
try to disable the touchpad with

[HTML]modprobe -r psmouse[/HTML]

when you want to use it again

[HTML]modprobe psmouse[/HTML]

---

### Post by Mr_Smiley on 2005-12-17
[quote=lmp3]i get the following error when i run synclient on my laptop (HP nc622):



any thoughts on how i should proceed?  i'm a relative newbie...

thanks.[/quote]

I had the same problem.
What I had to do was add the line:

```
Option      "SHMConfig" "on"
```

in the "Input Device" section of xorg.conf.

If you need anymore help just ask :)

---

### Post by lmp3 on 2005-12-19
thanks.  i worked like a charm...

---

### Post by foxy123 on 2005-12-20
[QUOTE=encinas]If you check the synaptic's changelog:

([http://web.telia.com/~u89404340/touchpad/files/changes.txt](http://web.telia.com/~u89404340/touchpad/files/changes.txt))

0.14.2 (2005-05-16)
- Added a hotplug script that disables the touchpad when a USB mouse
  is connected. (And reenables it again when the USB mouse is
  disconnected.) From Joergen Scheibengruber.

But, I've not tested yet.[/QUOTE]
I wonder how to use it? I have not found any docs on it specifically.

However, I read about symdaemon:
>        -t     Only  disable  tapping  and  scrolling,  not mouse movements, in response to keyboard activity.

I think it is what I need. How to load this daemon on startup?

---

### Post by luopio on 2005-12-22
Just put it into the startup programs in System->Preferences->Sessions

btw, has anyone noticed that when you start your laptop with a usb-mouse connected the mouse gets the first mouse-dev-file in /dev/input and touchpad gets the second one. This leads to the problem that the synaptics touchpad is not found by Xorg (it'll work, but poorly with the general mouse driver). 

Could you people check if you have this problem too? Just start the computer with the usb-mouse already connected and once in X run "xsetpointer -l". There you should see the keyboard, the usb-mouse and the touchpad (but I only see my keyb&touchpad).

---

### Post by foxy123 on 2005-12-22
[QUOTE=luopio]Just put it into the startup programs in System->Preferences->Sessions

btw, has anyone noticed that when you start your laptop with a usb-mouse connected the mouse gets the first mouse-dev-file in /dev/input and touchpad gets the second one. This leads to the problem that the synaptics touchpad is not found by Xorg (it'll work, but poorly with the general mouse driver). 

Could you people check if you have this problem too? Just start the computer with the usb-mouse already connected and once in X run "xsetpointer -l". There you should see the keyboard, the usb-mouse and the touchpad (but I only see my keyb&touchpad).[/QUOTE]
```
~$ xsetpointer -l
"Synaptics Touchpad"    [XPointer]
"Configured Mouse"      [XExtensionDevice]
"Generic Keyboard"      [XKeyboard]

```

---

### Post by foxy123 on 2005-12-23
[QUOTE=luopio]Just put it into the startup programs in System->Preferences->Sessions[/QUOTE]
I usually use a couple of DEs depending on my mood :) So I would prefer to have this daemon started before I choose my session...

---

### Post by luopio on 2005-12-24
If you use different DE's, then you can place the command in a ~/.xsession script inside your home directory. Just add the line "/usr/bin/syndaemon" in and make sure the file is executable ("chmod a+x .xsession", if it's not). 

This script gets run by gdm (and i think kdm uses it too) so every DE will use it.

---

### Post by Sef on 2005-12-25
When I had my touchpad active, I solved the problem by folding a wash cloth in half and covering the touchpad unless I needed to use it.

---

### Post by foxy123 on 2005-12-25
[QUOTE=luopio]If you use different DE's, then you can place the command in a ~/.xsession script inside your home directory. Just add the line "/usr/bin/syndaemon" in and make sure the file is executable ("chmod a+x .xsession", if it's not). 

This script gets run by gdm (and i think kdm uses it too) so every DE will use it.[/QUOTE]

thanks a lot. It is /usr/local/bin in my case...

---

### Post by foxy123 on 2006-01-06
[QUOTE=luopio]If you use different DE's, then you can place the command in a ~/.xsession script inside your home directory. Just add the line "/usr/bin/syndaemon" in and make sure the file is executable ("chmod a+x .xsession", if it's not). 

This script gets run by gdm (and i think kdm uses it too) so every DE will use it.[/QUOTE]

actually it does not work for some reason... I still have to launch it manually :(

---

