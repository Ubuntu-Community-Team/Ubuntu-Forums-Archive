---
title: "Customize buttons on USB remote control (xbmc)"
date: 2009-05-14
forum: Hardware
---

### Post by bogoliubov on 2009-05-14
Hello. I have connected an old laptop to my TV to use with Xbmc, which works OK. Now I also have an usb remote control (radio signal) that I wish to use. 

The remote has only very basic functionality, such as volume up/down, play/pause, next/prev etc.
The problem is that I want to reassign all the buttons so I get something that is more suitable for a multimedia remote. 
This is how I want it:
Volume Down => Escape
Volume Up => Shutdown
Mute => Up
Prev => Left
Next => Right
Stop => Enter
Play/Pause => Down

Now, I tried xev to get the keycodes for the remote. But only some buttons actually produce a keycode, at least what I understand. So I don't know if I can use xmodmap...?

Or perhaps I can do this within Xbmc? That'd be ok as well, but I haven't found any info on how to do this for my kind of remote control (usb)...

So, how can I make this work the way I want? Any help is greatly appreciated!

---

### Post by bogoliubov on 2009-05-15
Perhaps I can reassign the keys that the remote control "presses" instead? 

For instance, I want the Stop button to be "Enter". So can I reassign the Stop button (also on the keyboard) to be Enter instead? The keyboard on the laptop doesn't have to work very well, and it's only the multimedia buttons that we'll reassign...?

---

### Post by bogoliubov on 2009-05-16
It seems that if I remove some shortcuts for multimedia keys in System->Preferences->"Keyboard Shortcuts" the remote control at least report some keycodes. But I still can't get it to work with xmodmapping...?

---

