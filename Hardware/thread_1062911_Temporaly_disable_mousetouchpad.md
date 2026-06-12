---
title: "Temporaly disable mouse/touchpad"
date: 2009-02-07
forum: Hardware
---

### Post by olejorgen on 2009-02-07
Not sure where to post this really. I think this forum is missing a "Software/utility discussion" section.

I just found out about xsetpointer today (after hacking together a c program that did about the same thing :))

```

$ xsetpointer -l
0: "Virtual core keyboard"	[XKeyboard]
1: "Virtual core pointer"	[XPointer]
2: "Generic Keyboard"	[XExtensionKeyboard]
3: "cursor"	[XExtensionKeyboard]
4: "stylus"	[XExtensionKeyboard]
5: "eraser"	[XExtensionKeyboard]
6: "Configured Mouse"	[XExtensionPointer]
7: "Synaptics Touchpad"	[XExtensionPointer]
8: "AlpsPS/2 ALPS GlidePoint"	[XExtensionPointer]
$ xsetpointer -c "Synaptics Touchpad"
# disable touchpad
$ xsetpointer +c "Synaptics Touchpad"
# enable touchpad

```

I'm not sure but I think the synaptic driver has a similar functionality. I actually wanted this for the mouse. (pointer go everywhere when I use the laptop in bed :P )

PS: wtf? I must select a prefix? What about defaulting to [other] at least?

---

