---
title: "Mouse thumb buttons question"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by dlpfmVfH on 2005-06-17
I have a logitech mx510...and have a few questions about the button configurations...

do I use the imwheel variant...: with imwheelrc...and xmodmap as described in the how to?
[http://www.ubuntuforums.org/showthread.php?t=3828&highlight=thumb+buttons](http://www.ubuntuforums.org/showthread.php?t=3828&highlight=thumb+buttons)

or do I use the evdev method??
[http://blog.blackdown.de/2005/04/03/logitech-mx1000-configuration/](http://blog.blackdown.de/2005/04/03/logitech-mx1000-configuration/) or
[http://www.ubuntuforums.org/showthread.php?t=3828&page=5&pp=10&highlight=mx510](http://www.ubuntuforums.org/showthread.php?t=3828&page=5&pp=10&highlight=mx510)
with a xbindkeysrc

and what's the real difference?

On the website of Konqueror it is adviced not to use imwheel...

so can anyone explain this to me..

---

### Post by foobar on 2005-06-17
this is my mouse setup, didnt need to install anything
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

---

### Post by dlpfmVfH on 2005-06-17
does it work with konqueror...??
 and no imwheel...and no evdev??

and the thumb buttons / extra buttons work... in firefox???

---

### Post by foobar on 2005-06-18
[QUOTE=aboe]does it work with konqueror...??
 and no imwheel...and no evdev??

and the thumb buttons / extra buttons work... in firefox???[/QUOTE]

it works perfect in firefox not sure about konq.
and i did _not_ install imwheel, evdev or anything to get the extra buttons(forward/back) to work... just had to restart X.

*im using a logitech cordless

---

