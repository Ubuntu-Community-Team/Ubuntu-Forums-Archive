---
title: "Mouse Stopped Working"
date: 2008-09-14
forum: Hardware
---

### Post by nick334 on 2008-09-14
My mouse, a Trust MI-2450D, isn't working in Ubuntu. It works perfectly well in XP but not in Ubuntu. It was working but I think I edited the Xorg file to try and make it use the scroll wheel and side buttons.

Here's the mouse section of the Xorg.conf file:

Section "InputDevice"
	Identifier	"Mouse 1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device""/dev/input/mice"
	Option		"Protocol""Auto"
	Option 		"Buttons" "N"
	Identifier	"Configured Video Device"
EndSection

I've been changing things around but I'm not sure how to get it back to how it works. The light is on when in Ubuntu so it must be a problem with the settings.

Any help appreciated.

---

### Post by 1/0 on 2008-09-14
> **nick334 said:**
> 
	Option		"Device""/dev/input/mice"
	Option		"Protocol""Auto"
Put a space between the quotation marks and see if its only that. I.e.

```
	Option		"Device""/dev/input/mice"
	Option		"Protocol""Auto"
```

---

### Post by nick334 on 2008-09-14
Can't believe it was that easy :o Thanks.

---

### Post by 1/0 on 2008-09-14
No problem. Its irritatingly simple sometimes...

---

### Post by nick334 on 2008-09-14
Right some more questions now.

[http://www.trust.com/products/product_detail.aspx?item=15373](http://www.trust.com/products/product_detail.aspx?item=15373)

My mouse has two side buttons, two normal and a scroll wheel. The side buttons work in Firefox but not in the Ubuntu explorer thingy, the file browser. Do they ever work in the file browser? Going forward and back and the like.

The scroll wheel works going up and down fine. I want it to scroll up and down really fast when you press it down, like in Windows. It works for opening links in new tabs by pressing it down but it doesn't do this.

Do I have to edit the Xorg thing again to make the mouse do these things?

---

### Post by 1/0 on 2008-09-14
[This](http://fvue.nl/wiki/Configuring_my_5-button_mouse_in_X_Windows) is probably what you're looking for then. You'll need to add some pointers to xorg.conf. Don't forget the xmodmap afterwards.

---

### Post by nick334 on 2008-09-14
After all my fiddling I've managed to end up with 5 Xorg.confs. Which one is the one being used? The original xorg.conf or one of the others - xorg.conf.1, xorg.conf.2 etc.

---

### Post by 1/0 on 2008-09-14
*/etc/X11/xorg.conf* should be the one.

---

