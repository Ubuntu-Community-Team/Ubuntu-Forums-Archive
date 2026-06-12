---
title: "Mouse Back Button in FireFox"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by HarleySteve on 2007-12-05
I had been trying to get my 9 Button Mouse, Microsoft Wireless Laser 6000, to work completly.

The stock config, allowed for all of the button to work except for the side scroll button.  After putting this in as my XOrg.conf:

Section "InputDevice"
        Identifier 	"Configured Mouse"
        Driver 		"evdev"
        Option 		"CorePointer"
        Option 		"Device" 		"/dev/input/event3"
        Option 		"Buttons" 		"9"
        Option 		"ZAxisMapping" 		"4 5"
        Option 		"DialRelativeAxisButtons" "6 7"
EndSection

My side scroll still didn't work, but all the buttons on my mouse were still recognized, to include my side scroll.  But they just didn't do anything for me in Firefox.  Except that now my vertical scroll chaged the font size.  So after some more searching I changed these configs in Firefox:

mousewheel.horizscroll.withnokey.action to 1
mousewheel.horizscroll.withnokey.numlines to 1
mousewheel.horizscroll.withnokey.sysnumlines to true

I also changed this so that I could paste with the middle mutton:
middlemouse.paste to true

Now my scroll works perfect, up/down/left/right as it should.  Even in Evolution.

BUT now my side button no longer does anything.  If I revert my changes to the firefox config then I regain back functionality.

I am by no means figuring this stuff out on my own.  I wouldn't be this far along if it weren't for this forum.  

Does anybody out there have the missing peice to my puzzle?  Or know where I can look for it?

Thanks,
Steve

---

### Post by HarleySteve on 2007-12-09
Anybody?  I changed the ZAxizMapping to "8 9" and the wheel still works, but still function of the back button doesn't.  I am about to remove everything I did to get the back button to work.

I always believed the line 'You can do ANYTHING in Linux'  I guess that's true, except.......

---

### Post by Hopworks on 2007-12-30
> **HarleySteve said:**
> Anybody?  I changed the ZAxizMapping to "8 9" and the wheel still works, but still function of the back button doesn't.  I am about to remove everything I did to get the back button to work.

I always believed the line 'You can do ANYTHING in Linux'  I guess that's true, except.......
Did you find  solution HarleySteve?

I'm working the same issue with my Logitech G5 Laser mouse. I just won back my ability to scroll up and down in pages with the wheel, but it looks like I had to take stuff out that would allow me to "go back one page" with the left side button. I want BOTH! hehehe

---

### Post by HarleySteve on 2007-12-30
Not Yet.  But so far I am just living with it.  Wheel works left/right and Up/Down with no issues.  Just that the mouse is quite sensitive and my thumb button still doesn't work.

---

