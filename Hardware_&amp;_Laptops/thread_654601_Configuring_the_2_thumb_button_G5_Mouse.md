---
title: "Configuring the 2 thumb button G5 Mouse"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by dethredic on 2007-12-31
I have the newer G5, with 2 thumb buttons and I am having some trouble configuring it.

I have it all working except for the side scroll. Here is my xorg.conf

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	option 		"Protocol"	 "auto"
	option 		"Device" 	"/dev/psaux"
	option 		"Emulate3Buttons"	 "no"
	option 		"ZAxisMapping"	 "4 5 8 9"
	option 		"Buttons"	 "9"
	option 		"ButtonMapping" "1 2 3 6 7"
EndSection

```

Does anyone have this mouse set up fully, or have an idea of what I should try?

---

### Post by dethredic on 2008-01-01
anyone?

---

### Post by dethredic on 2008-01-01
Bump

---

### Post by dethredic on 2008-01-02
Anyone??

---

### Post by farbror_ace on 2008-01-02
Try btnx it worked for me.

---

### Post by Yellow Pasque on 2008-01-02
Tried this? (i.e. using evdev)
[http://forums.gentoo.org/viewtopic-p-4228484.html](http://forums.gentoo.org/viewtopic-p-4228484.html)

---

### Post by dethredic on 2008-01-02
Well, I found out that my side scroll does work. Firefoc just does not support it. I am going to try btnx to see if it will work for me.

---

### Post by Yellow Pasque on 2008-01-02
Did you try Entering about:config in the URL bar?.. and then:
1. Right-click on mousewheel.horizscroll.withnokey.action and change its value to 0
2. Right-click on mousewheel.horizscroll.withnokey.sysnumlines and click toggle to change it to true

---

### Post by dethredic on 2008-01-02
> **Temüjin said:**
> Did you try Entering about:config in the URL bar?.. and then:
1. Right-click on mousewheel.horizscroll.withnokey.action and change its value to 0
2. Right-click on mousewheel.horizscroll.withnokey.sysnumlines and click toggle to change it to true

That did not help. Nothing happens.

---

### Post by farbror_ace on 2008-01-03
Firefox going back on the thumbbutton is a windows thing, you will need btnx or the like to simulate hotkeys for your actions. (Alt+Left) in this case.

---

