---
title: "Compaq evo N1015V and ps2mouse"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by Noiano on 2007-02-23
Hello everybody
I was given an old laptop, aged 4, a compaq evo n1015v and I have a little problem with the ps2 mouse. On the back of the laptop there is a ps2 port useful to connect an external keyboard or an external mouse. I want to connect an external mouse in order not to use the touchpad which I consider uncomfortable. 
When Ubuntu is running I plug the mouse but nothing happens; this is the output of dmesg | tail

```

[17180358.364000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180358.368000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180358.368000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180358.408000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180358.412000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180358.412000] psmouse.c: issuing reconnect request
[17180359.892000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
[17180359.964000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17180360.588000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180360.588000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180360.592000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180363.880000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180363.880000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17180363.880000] psmouse.c: issuing reconnect request
[17180365.368000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x9d48b1, caps: 0x914713/0x14006
[17180365.440000] input: SynPS/2 Synaptics TouchPad as /class/input/input4

```

I really do not know what to do....I also tried to edit xorg.conf
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

```
changing /dev/input/mice to /dev/psaux but nothing. I have run out of ideas...Help :confused: 

PS: I attached the full xorg.conf

---

### Post by Noiano on 2007-02-24
up.....please help....if any additional info is needed please ask!

---

### Post by skuggeboy on 2007-03-01
This might work. Open the file /etc/modules with a text editor. When you get it open there should be a line psmouse. Make the line look like this psmouse proto=bare. After that save the file (before doing any changes you should make a backup) and after saving reboot and the mouse should work. Hopefully.

---

### Post by Noiano on 2007-03-01
there was no ps2mouse line in the /etc/modules file just "lp" and nothing more. I tried to add what you advised but nothing, same dmesg messages....what else can I do?

I also have problems in rebooting...it powers off correctly but doesn't reboot...the screen always displays something like:

[number.other number] Rebooting your system

Nothing happens! :confused:

---

### Post by skuggeboy on 2007-03-02
You can also try adding this line to a file in /etc/modprobe.d/options

options psmouse proto=imps

After that restart your computer and hopefully it works this time.

---

### Post by Noiano on 2007-03-02
Great! now the external mouse works properly...strangely the touchpad is not disabled. If It can be disabled I would be happier but if not I'll happy nonetheless.

Thanks for your help

PS: where can be set the number of line to scroll using the mouse wheel? I cannot find such parameter in gnome.

---

### Post by C00Lgardie on 2007-04-24
I spent the last three days trying to fix this problem. And now everything works! I am so happy, and all thanks to you!

I'm running Feisty on a Compaq Presario 700

---

