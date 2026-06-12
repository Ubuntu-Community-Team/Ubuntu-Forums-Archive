---
title: "Mapping Multimedia Keys?"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by am7146 on 2007-07-22
Okay.  I'm out of ideas.  

I've got this IBM USB keyboard with a bunch of spare buttons on it-- Lock Desktop, My Documents, Word Processor, Spreadsheet, Calculator, E-Mail, Internet, Access IBM--and I want to hook them up to do things in Gnome.

Here's the problem.  The only place they show up at all is if I do showkey in a real console.  Here's what I get:

when I press, Lock Desktop, for example, I get:

0x00 0x82 0x81
0x80 0x82 0x81

First line is press, second is release.

Next over is My Documents:

0x00 0x82 0x82
0x80 0x82 0x82

Every other tool I use to try to see the keycode or scancode gives me nothing.  xev shows lots of good stuff for the keys found on normal keyboards, but does not respond at all to the extra keys.

I have no idea what 3 codes on output means, or where to go next.  I'd like to map them up to run scripts or execute programs in Gnome, or map them over other keyboard shortcuts in programs like thunderbird or firefox.  I know how to do that with keys like F9 that give responses in xev, but I'm stuck on these.  Thoughts?  help?

Andy-

---

### Post by MrHippocampus on 2007-07-22
Believe it or not, the fact you get those 0x.. numbers is good news :) the laptop im on at the moment has keys which don't even do that :(.

Theres a nice [page]("https://help.ubuntu.com/community/MultimediaKeys") on the wiki which should sort you out, theres a program called keytouch which should make your life easy, but if it doesn't work there are in depth instructions on how to set the keys up manually. Ive had to do the manual set-up myself for my logitech keyboard (which has ridiculous amounts of extra buttons), it takes time but its worth it :)

---

### Post by am7146 on 2007-07-22
I'd read that page and downloaded keytouch and keytouch-editor before posting (I did a lot of googling before posting...).   No luck.  event2 and event3 are "Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )" but pushing buttons has no effect.  keytouch-editor doesn't see the events at all.  event0 is the internal keyboard on the laptop, and keytouch-editor responds the way I'd expect it to.

So, having the 0x## numbers are good?  Cool! :) How do I use them?  The examples like:
   setkeycodes e01e 120  
are for setting one single scancode to one keycode.  How do I use 3?  0x00 0x82 0x81?

Andy-

---

### Post by MrHippocampus on 2007-07-23
the examples are for the output from dmesg, heres the end of mine if I press the brightness up key on my laptop:

```

atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

now, dumpkeys says that code 128 is free

```

keycode 128 = nul             
        altgr   control keycode 128 = VoidSymbol      
        shift   alt     keycode 128 = VoidSymbol 

```

So now the code can be set

```

setkeycodes e059 128

```
Remember to add all of these lines to /etc/init.d/bootmisc.sh if you want them to work after you restart :)

And for the xmodmap stuff you should be able to follow the wiki.

---

### Post by am7146 on 2007-07-23
Cool.  Thanks.   I read that Wiki page and was hopeful it would work.

My problem is I get nothing in dmesg.  Nothing from atkbd.c (which might be because it's a USB keyboard, unlike the PS/2 keyboard built-in to your and my laptop).  Aside from showkey in a real console I get no response from any software at all.  And showkey returns three codes for one action (press or release) instead of just one like every normal key does, and I haven't found any documentation on how to use setkeycodes with more than one byte or unicode word.

Andy-

---

### Post by MrHippocampus on 2007-07-23
at a guess, the three keycodes look like there organised in the following way, 0x00 0x82 .. for key down, and 0x80 0x82 .. for key up. So maybe you could try just using the last hex value and see if you get any luck (you could also try holding down one of they keys and see if any particular number is repeated again and again).

The only other thing ive found is [here]("http://keytouch.sourceforge.net/howto_keyboard/node4.html"), but it seems to use a program from keytouch so I dont know how much success you will have.

---

### Post by am7146 on 2007-07-24
i tried these setkeycodes in /etc/init.d/bootmisc.sh and xev still shows nothing....  

	# ANDY Add setkeycodes for the IBM keyboard
	setkeycodes 0x80 128
	setkeycodes 0x81 129
	setkeycodes 0x82 130
	setkeycodes 0x83 131
	setkeycodes 0x84 132
	setkeycodes 0x85 133
	setkeycodes 0x86 134
	setkeycodes 0x87 135
	# END SETKEYCODES

any thoughts?

---

### Post by jliebau on 2007-08-26
I have a different keyboard (Dell Enhanced Performance USB Keyboard) that sends the multimedia keys in the same format: a three digit string (eg, 0x00, 0x82, 0x81), as seen with showkey in console window.  However, running evtest in a terminal window displays a list of events corresponding to the extra keys but with event codes > 255 (eg, event code 256 is Btn0, 257 is Btn1, etc--yes, evtest lists numerous event codes it knows about with their names).  Unfortunately, setkeycodes apparently does not accept codes > 255.  The site keytouch.sourceforge.net (undated) says the problem lies in the USB input driver and suggests changing to a PS/2 connection (ugh!). 

Anyone have any suggestions for getting USB event codes > 255 working and integrated into ubuntu (w/o rewriting kernel USB driver)?

Thanks,
Jim

---

