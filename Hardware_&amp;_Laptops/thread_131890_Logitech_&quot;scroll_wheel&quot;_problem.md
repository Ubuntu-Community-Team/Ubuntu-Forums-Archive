---
title: "Logitech &quot;scroll wheel&quot; problem"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by Tomlin on 2006-02-17
I've searched the forums and found lots of conflicting settings to xorg.conf.

I have the CHEAPEST ($14.99) Logitech optical corded mouse. I use a USB-PS/2 connector plugged into a KVM switch. This is the pertinent section of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

With this configuration, the wheel works with EVERY app except Firefox. In Gedit, Konqueror, Open Office, the wheel scrolls up and down, but in Firefox, scrolling up takes you BACK one page.

When I replace "ExplorerPS/2" with "Im/PS2", scrolling the wheel up pops up a window as though I'd hit the right button.

I'm SOOOOOOOOO close. Is this a Firefox problem or what?

TIA,

Tomlin

---

### Post by alfonz on 2006-02-17
I think that is a firefox problem

type about:config in your titile bar and scroll down to the mousewheel settings, you might find the answer there.

---

### Post by Tomlin on 2006-02-17
Thanks for your response.

I found:

 /usr/lib/mozilla-firefox/greprefs/all.js

Changed:

pref("mousewheel.horizscroll.withnokey.action",**2**);

to:

pref("mousewheel.horizscroll.withnokey.action",**0**);

UP scroll goes up one 'line' and not up (back) one 'page'.

I'm noticing now, any text 'copied' (or CTRL-c) from within Firefox can be pasted by pressing the wheel as a button. This can be across apps, like Open Office or gedit. Problem is, if you hit the wheel too hard and mistakenly click it instead of rolling it, you paste whatever is in the buffer. You can clear the buffer with a  'cut' (or CTRL-x).

Hmmmm. :-k

---

