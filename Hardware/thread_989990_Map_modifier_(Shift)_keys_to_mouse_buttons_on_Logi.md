---
title: "Map modifier (Shift) keys to mouse buttons on Logitech MX518"
date: 2008-11-22
forum: Hardware
---

### Post by ShawnX on 2008-11-22
I am trying to map the Keyboard Shift and Ctrl keys to the left mouse buttons on my Logitech MX518.  The main reason I want to do this is for use in WoW for my different abilities.  I have my action bars maped 1-0 on bar 1, then Shift+1 - Shift+0 on bar 2 and Ctrl+1 - Ctrl +0 on bar 3.

I am using Xbindkeys and Xmaxcroplay and have had some success but it's not doing exactly what I need.

Here is my .xbindkeysrc so far
```

"echo -e "KeyStrPress Shift_L" | xmacroplay :0.0"
  m:0x0 + b:6
```

This does press the shift key, but it does not release it when I let go of the button. It's acts as though I have pressed the caps lock key and won't let go until I press the actual left Shift key on the keyboard.  

What I need it to do is act exactly like pressing the shift key on the key board.  When I press and hold button 6 on my mouse it should hold shift, and release when I release the button.  I was able to set it up to work like this using the setpoint drivers in Windows so I know it is possible...I just can't figure out how to do it in Ubuntu.

I tried this in my xbindkeysrc but it didn't work
```

"echo -e "KeyStrPress Shift_L KeyStrRelease Shift_L" | xmacroplay :0.0"
  m:0x0 + b:6
```

---

### Post by ShawnX on 2008-11-23
Bump

---

### Post by Dirtneck on 2009-03-20
Have you had any luck with a solution?

I've tried **xbindkeys** with **xte** and **xvkbd**. xbindkeys doesn't work in this situation because I want to hold Shift; it performs the action in one sequence before I can press another key, rather than holding Shift as I intend.
**HIDpoint** (a **SETpoint** clone) doesn't work for me but maybe for you; my mouse, although supported hardware, doesn't get recognized by the app. This seems like a common problem with the app so I say good luck to you should you try it. Note here... if it doesn't work for you... reboot, follow the unistall instructions, and reboot again. 

I've also tried **easystroke** and **xmodmap** but still haven't figured out a solution. 

I play wow as well with the similar usage; keys 1~6, then shift+ keys 1~6, then ctrl+ keys 1~6
So I want Shift and Ctrl as my left/thumb buttons. (**Logitech MX620**)

What I have found is that xbindkeys is sluggish when playing wow; I hit a key and it may/may not respond in wow. I might have to press the key multiple times to acheive what I need. So I've use xmodmap where I could and try not to use xbindkeys as it hinders my purpose.

---

### Post by ShawnX on 2009-03-21
> **Dirtneck said:**
> Have you had any luck with a solution?
Sort of...more of a work around really.

What I did was set up a 1 second delay and map it to the modifier keys.   Here's how it works.  When I push one of the mouse buttons, it pushes the modifier key and holds it for 1 second.  This gives me the time to press the action bar key I want before it is released.  The problem is that I have to remember to press and release the mouse modifier every time I want to use one of those actions lol.  It takes some getting used to, but you get a rhythm with it after a while.

Here is my xbindkeysrc
```

"echo -e "KeyStrPress Shift_L Delay 1 KeyStrRelease Shift_L" | xmacroplay :0.0"
   m:0x0 + b:8

"echo -e "KeyStrPress Control_L Delay 1 KeyStrRelease Control_L" | xmacroplay :0.0"
   m:0x0 + b:9
```



> **Dirtneck said:**
> **HIDpoint** (a **SETpoint** clone) doesn't work for me but maybe for you; my mouse, although supported hardware, doesn't get recognized by the app. This seems like a common problem with the app so I say good luck to you should you try it. Note here... if it doesn't work for you... reboot, follow the unistall instructions, and reboot again.
Thanks for this!  I wasn't even aware of HIDpoint.  I tried it and it works with my mouse, except there is no way to map only the modifier key like I need, so I am back to using xbindkeys + xmacroplay.

The program seems promising though, so I posted in their "wishlist" forum asking for the feature.  [http://www.hidpoint.com/forum/func,view/id,272/catid,14/](http://www.hidpoint.com/forum/func,view/id,272/catid,14/)

---

