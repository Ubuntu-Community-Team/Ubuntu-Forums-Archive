---
title: "[SOLVED] Keyboard Layout Not Remembered On Reboot"
date: 2008-08-10
forum: General Help
---

### Post by bunnyfly on 2008-08-10
Hello - when I go to System - Preferences - Keyboard - Layouts and change to another layout, it works fine, but whenever I reset it returns to "USA."

I'm using the Colemak layout, but it does it with any layouts I've tried. If I totally remove the USA layout so that only Colemak is available, it still does this...then when I go into the settings, it shows Colemak alone, but is actually typing Qwerty, so I have to add and change to USA then change back to Colemak for it to work.

Any suggestions? Fixes? Hacks? I'm kindof shocked that this basic functionality is broken, but it's probably only mine since I doubt Hardy would be released like this and I can't find any other posts about it that are answered.
[bunnyfly]

---

### Post by korvins on 2008-08-11
Same problem here. 

And some other people also noticied the same. Obviously you will not have this problem if you have an US keyboard. But problem is very annoying.

There exists several bugs filled in for that: 
keyboard layout switching combination does not get saved
[https://bugs.launchpad.net/ubuntu/+bug/194645](https://bugs.launchpad.net/ubuntu/+bug/194645)

And the original one:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)

It seems to be a problem of autologin?

---

### Post by DeMus on 2008-08-11
I have the same problem here. It seems there is a bug in the system. Is there somebody who can solve this, because it is very annoying.

Thanks,
DeMus

---

### Post by Elfy on 2008-08-11
I was getting that - changed my xorg, which had us for some reason, to correct keyboard and haven't had problem since.

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "uk"

If you want to edit it

```
sudo nano -B /etc/X11/xorg.conf
```

Ctrl+O, Enter to save, Ctrl+X to exit

---

### Post by DeMus on 2008-08-11
Fantastic man, it worked. I had the US Int'l layout chosen at installation and I wanted to have the normal US layout. The difference is the way it reacts to the ' and " keys.
I erased two lines op options from the file, rebooted and now it's okay. The options had to do with the int'l layout.

Thanks a lot.

DeMus

---

### Post by bunnyfly on 2008-08-15
Thanks for the advice and help everyone, but...

Editing /etc/X11/xorg.conf still isn't working for me. I tried 	```
Option "XkbLayout" "colemak"
``` but that didn't work. Searching around some more it appears that colemak is a sub-layout of US, so I found this line and added it, but this still doesn't work! This is what my xorg looks like now:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbSymbols" "colemak"
EndSection
```

Any ideas? Thanks,
[bunnyfly]

---

### Post by bunnyfly on 2008-08-17
Bump

---

### Post by Elfy on 2008-08-18
Found this maybe it will help, in xorg change your option to 

Option "XkbSymbols" "pc(pc105)+colemak"

---

### Post by bunnyfly on 2008-08-18
That worked Forestpixie - thanks so much! It even loads for the login screen!

Hurray for a working system, but really Ubuntu? Really? All this to get a keyboard to work?
[bunnyfly]

---

### Post by Elfy on 2008-08-18
Well, there you go...

Can you mark thread solved please.

---

### Post by bunnyfly on 2008-08-18
I already had : )

---

### Post by ph0nph0n on 2008-09-19
> Found this maybe it will help, in xorg change your option to

Option "XkbSymbols" "pc(pc105)+colemak"

That worked - however I had to follow the steps (download archive, copying colemak file, and edit xorg.conf) from [http://colemak.com/Unix#Linux.2FUnix_in_graphical_mode_using_xorg.conf_.28X.Org_Server_7.0_or_later.29]("http://colemak.com/Unix"). It wouldn't work without the downloaded colemak file.
Now it looks fine, and it took me ages to type that darn message...

---

