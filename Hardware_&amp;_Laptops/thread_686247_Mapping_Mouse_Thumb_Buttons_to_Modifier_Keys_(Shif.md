---
title: "Mapping Mouse Thumb Buttons to Modifier Keys (Shift/Ctrl) without BTNX (evdev driver)"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Jazzyman on 2008-02-03
As the title says, I have been trying to figure out a way to map modifier keys (specifically Shift and Control) to the thumb buttons on my Bluetooth MX1000.

There are several great advantages to this type of mapping.  For example, in firefox, Shift + wheel = back/forward, Ctrl + Wheel = zoom in/out, Alt + wheel = transparency with Compiz, Shift + click = new window, Ctrl + click = new tab.  In Ardour and many other editing programs, Modifier + wheel/click operations have important functionality too.  I used to have this working in Windoze back in the day with no problems.

I also used to have this working with a MX700 and BTNX, but since I upgraded to the MX1000, I've found the evdev driver to be much more stable, and it produces all the proper mouse events in XEV with no problems, whereas the standard mouse driver does not.  BTNX adds functionality to the standard driver, but I still end up getting duplicated right-click events on the thumb buttons, and I lose some functionality in Compiz without the proper mouse events being generated.

I've tried various combinations of programs including xbindkeys, xautomation, xvkbd, etc., but each of these only allows a modifier to be mapped in combination with another key (e.g. Alt+Left for Firefox Back).  This is not what I want - the modifier key ALONE must be mapped to the mouse button.

Anyone have any ideas?  Please use discretion before posting a response, as I've seen this question asked on other forums, and the standard  xbindkeys + xte/xvkbd response is always posted.  This DOES NOT WORK for what I'm looking for.

---

### Post by stibbons on 2008-02-12
Have you tried using the xmacro package to send the modifier key presses? To send a Control key press, you could bind something like the following to the mouse button press event using xbindkeys:
```
echo -e "KeyStrPress Control_L" | xmacroplay :0.0
```

And the corresponding release event, to bind to the mouse button release:
```
echo -e "KeyStrRelease Control_L" | xmacroplay :0.0
```

xmacro comes with a xmacrorec2 utility, which lets you record macros to see how to represent various key presses/combinations. I haven't yet tried sending pure modifiers like this, but I've had some success using xmacro like this with xbindkeys to send assorted xkeysyms.

---

