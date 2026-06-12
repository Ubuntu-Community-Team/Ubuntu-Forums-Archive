---
title: "problems setting up xkb"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by nekr0z on 2006-03-02
Well, maybe there's already a solution for my problem somewhere in thi forum, but I have not found it although trying really hard.

What I am trying to do is set xkb so that I have 2 keyboard layouts available, english with deadkeys and russian winkeys. I also want them to be switched using ctrl+shift.

Using xubuntu I actually have no graphical tool for this, but ok, I modified /etc/X11/xorg.conf so that the section reads like:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
 	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us_intl,ru(winkeys)"
	Option		"XkbOptions"	"altwin:meta_win,grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

Then I restarted X-server and -- nothing works: my keyboard seems to be US-english and doesn't switch to anything else. I enabled the "Xkb Layout Switcher" in the Xfce panel, it says that my keyboard layout is "UNI" and doesn't switch it.

Is there something I'm doing wrong?

---

### Post by branco on 2006-03-12
> Option "XkbLayout" "us_intl,ru(winkeys)"

Try:

```
Option "XkbLayout" "us,ru"
```

instead and see if this works. The layout plugin will probably not display the correct layout, but you'll figure it out soon enough. I don't know of an workaround for using the variants (like ru+winkeys) of the symbols files, yet...

Using the above option, you can only use country codes that have the corresponding symbols file located in /etc/X11/xkb/symbols.

---

### Post by nekr0z on 2006-03-12
Thank you branco, but I seem to have already figured the way it works:

The problem was there's no "us_intl" layout in Ubuntu. There is one in Debian, to indicate the US layout with deadkeys, and I thought it was the same in Ubuntu. Instead, Ubuntu only uses "us" with the "intl" subversion. So the line should read:

 Option "XkbLayout" "us(intl),ru(winkeys)"

And this works.

---

### Post by branco on 2006-03-12
Thanks for the tip.

BTW, have you tried the XFCE 4.2.3.2 w/ graphical installer? I've found it at the [www.xfce.org](www.xfce.org). It compiled OK w/ ALSA disabled, but no Composite support (i.e, no drop shadow and transparency). Any luck?

---

### Post by nekr0z on 2006-03-12
Nope.

I still think that for most stuff the .deb packages should be used for installation. The reason is security, which is quite important for me here on my system. So I'm of little help here...

---

### Post by branco on 2006-03-13
Yup, that and the fact that I got stuck with the install of the XFCE that is 1. broken, and 2. cannot be uninstalled... Well, that what you get when... Moreover, the XUbuntu version of XFCE *does* support transparency, which is broken anyway in the official XFCE as well. :-k Or... maybe it's the ATI driver thing...

Thanks again for the tip. It worked flawlessly.

---

