---
title: "function keys on keyboard"
date: 2016-08-11
forum: Hardware
---

### Post by martin30002 on 2016-08-11
I have a keyboard with the functions (fn) keys for speaker volume, mute sound, suspend, start/stop and new browser tab.
I was surprised that these functions work. How does it work and why?

When I have a keyboard for example without a "mute-sound" key, can I make ubuntu recognize Fn-F12 as mute?

---

### Post by ajgreeny on 2016-08-11
Those keyboard shortcuts work because those key-presses are linked to a keyboard shortcut in your keyboard configuration.  I have set up several in addition to those that were automatically used after installing Xubuntu 14.04.

The command ```
amixer -D pulse set Master toggle
``` will toggle sound on/off so assuming you can use that as the command in a keyboard shortcut with your desktop environment (unity?), the answer to your question is probably "Yes, you can use that key combination, or another, to toggle sound mute/unmute."

If you need volume changes as well you can use commands:-
```
amixer set Master playback 3dB-
amixer set Master playback 3dB+
```
to either raise or lower volume by 3dB; you can change that 3dB to a value you prefer.

---

### Post by martin30002 on 2016-08-11
In the unity keyboard configuration, I have this mapping:
Volume down->Audio lower volume
Volume up->Audio raise volume
Volume mute->Audio mute

So the mapping is not done directly to keys.
There must be another mapping explaining the keys of "Audio lower volume", "Audio mute" ...

Also, I have a Lenovo keyboard with a (working) suspend key, this key is not defined at all in the keyboard config.

---

### Post by deadflowr on 2016-08-11
It just means that the layout for your keyboard has been added to the rather long list of known supported devices within linux.
When you boot Ubuntu or any Linux distribution, the system reads your hardware and notes that it is what it is, and uses a configuration already known for that hardware.

That said:
> When I have a keyboard for example without a "mute-sound" key, can I make ubuntu recognize Fn-F12 as mute?
Of course, you can change the keyboard bindings to anything you want, given any changes should also consider whatever the keybinding you changed have on any other keybindings that might have been used for that keybinding.

If any of that makes sense.

---

### Post by martin30002 on 2016-08-14
Where do I see why the system goes into suspend when I press Fn-Suspend on the lenovo keyboard?

---

