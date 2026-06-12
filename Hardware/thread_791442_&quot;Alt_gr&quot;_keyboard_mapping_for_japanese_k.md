---
title: "&quot;Alt gr&quot; keyboard mapping for japanese keyboard on a Kohjinsha SH6"
date: 2008-05-12
forum: Hardware
---

### Post by monti on 2008-05-12
Hi.  

I recently bought a [Kohjinsha SH6](http://www.kohjinsha.com.sg/products/outline-sh.htm) on a trip to Japan.  It's a great piece of hardware, and the [japanese keyboard layout](http://en.wikipedia.org/wiki/Keyboard_layout#Japanese) doesn't really bother me.  

What does bother me, is that I am unable to define and use an **AltGr** key.  In a norwegian keyboard mapping, the **@** key is reached with **AltGr-2**. Using xev, I see that my designated alt gr key ([two steps to the right of space bar](http://pocketables.typepad.com/photos/uncategorized/kohji_key1.jpg), I'll call it The Key) has keycode 208.  I assign AltGr to The Key with xmodmap:
```
$ echo keycode 208 = Mode_switch | xmodmap -
```
I can verify that The Key sends Mode_switch (aka AltGr) by using xev again, but pressing **The Key-2** does not give me **@**.  I can force the 2 key to really return @ when using the alt gr modifier like this:
```
echo keysym 2 = 2 quotedbl at at | xmodmap -
```
That still doesn't give me @.

My InputDevice section for the keyboard in xorg.conf is nothing fancy, maybe it should be fancier?
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105" #I've also tried jp106
	Option		"XkbLayout"	"no"
EndSection
```

Does anyone know what I'm doing wrong?

---

### Post by monti on 2008-05-12
I see now that when I press The Key while monitoring with xev, the KeyRelease event is sent immediately even though I haven't released the key yet.  Maybe that's why it won't work as a modifier?  How do I remedy this?

---

### Post by monti on 2008-05-12
I might just as well keep talking to myself.  I discovered two things:
- the key just right of the space bar (keycode 129) does not send KeyRelease immediately, which makes it useable as a modifier.
- Mode_switch is fairly ancient, the kids use ISO_Level3_Shift for AltGr today.

By doing a **xmodmap -e "keycode 129 = ISO_Level3_Shift"**, that key now works as AltGr!  

Next step: making this work without using xmodmap, since that's ancient as well.

---

### Post by monti on 2008-05-25
I got rid of xmodmap, here's how:

[http://lists.freedesktop.org/archive...ay/035154.html](http://lists.freedesktop.org/archive...ay/035154.html)

There's info here as well: [http://ubuntuforums.org/showthread.php?t=961736](http://ubuntuforums.org/showthread.php?t=961736)

---

### Post by monti on 2009-05-10
.

---

### Post by LepeKaname on 2009-05-17
Sometimes I do monologue too... :)

I have a Japanese keyboard and I'm trying your post to enable AltGr.. .still no luck. In my case, xev codes are different of those you posted. I will keep trying. 

Thank you.

---

### Post by monti on 2009-05-18
> **LepeKaname said:**
> Sometimes I do monologue too... :)

I have a Japanese keyboard and I'm trying your post to enable AltGr.. .still no luck. In my case, xev codes are different of those you posted. I will keep trying. 

Thank you.

Yes, the key codes might be different on your machine.

Anyway, I've gone back to using xmodmap since that was the easiest solution.  I've added this to a script which runs on login:

```
xmodmap -e "keycode 102 = ISO_Level3_Shift"
```

I've selected the "105 key international keyboard" (not the "106 key japanese"), by the way.

---

