---
title: "why do i need to hold shift to use numpad?"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by delfick on 2006-06-03
hi all

currently i have to hold down shift to use any of the numbers in the numpad....why? and how can this be fixed?

and while i'm at it, how can i set up my mouse to use the two side buttons and the sidescroll capability? and set up all the extra functionality of my keyboard

I have Ubuntu Dapper and a Microsoft Wireless Optical Desktop Elite
[http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=016](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=016)

thnx for help, it will be greatly appreciated!

---

### Post by QuickFire on 2006-10-18
I have the same problem and I wasn't able to fix it yet!

Did you managed to fix it?

Thanks :)

---

### Post by wislon on 2006-10-18
I had a similar problem. I am away from my Ubuntu installation right now, but I seem to remember an option for it under the Settings / Preferences | Keyboard menu on the main panel (assuming you're using Gnome).

Have a look around the keyboard settings, there's a tick box that says something along the lines of "behave like Windows". Turn that off (or on, depending) and hopefully that will solve your problem.

Not to be facetious, but what happens if you turn your numlock on/off? Does it make a difference?

---

### Post by agesto on 2006-10-24
I have the same problem, I couldn't fix it.
Not even reconfiguring XKB

---

### Post by Lapeth on 2006-10-24
Well, I don't have that kind of problem, but I found that when Numlock is off, the numbers are accessible by holding down shift. Not holding shift -> nothing happens. Turning numlock on activates the numbers.

---

### Post by Wilb on 2006-10-24
I had a similar problem once. Try turning the option to boot with num lock enabled off in your BIOS, see if that helps.

---

### Post by agesto on 2006-11-02
I've discovered that the problem (in my case) is that the locking keys are not working, no caps locks, no num locks, no scroll locks. this apparently is a missconfiguration of xkb, but having tryed everything in mind as a configuration profile, i've no idea.

Please help!!! (sorry for my bad english, though i'm not a native speaker)

---

### Post by agesto on 2006-11-02
After fighting for a while, I've mannaged to SOLVE IT!!!!
It was far easier than I thought.

The problem was on my xorg.conf file, wich has an ambiguous definition of my keyboard rules.

So I started taking options out, until I found the ruleset that allowed me to continue the configuration via the ubuntu keyboard options (system->preferences->keyboard)

My keybard section on xorg.conf now look like this

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver			"kbd"
	Option			"CoreKeyboard"
#	Option			"XkbRules" "xorg"
#	Option			"XkbModel" "pc105"
	Option			"XkbLayout" "es"
#	Option 		"XLeds" "1 2 3" 
#	Option			"XkbOptions"	"lv3:ralt_switch,altwin:super_win"

Notice how I commented the xkbmodel, xkboptions, xleds and xkbrules directives so now i can mannage the keyboard configuration through the gnome-keyboard-mannager which is lot easier.


Hope this helps.

Greets from Argentina

---

### Post by 1ONE on 2007-08-04
Hello,

This is my first post here :)

I have managed to solve this problem on Ubuntu 7.04

Go to System > Preferences > Keyboard

Now go to tab "Layout Options"

Under "Miscellaneous compatibility options" you must turn on **Numpad keys works as with Mac**

---

