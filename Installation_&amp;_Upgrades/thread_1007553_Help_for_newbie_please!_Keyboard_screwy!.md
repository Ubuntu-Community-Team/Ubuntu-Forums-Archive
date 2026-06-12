---
title: "Help for newbie please! Keyboard screwy!"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by markuswinter on 2008-12-10
Hi all,

sorry if this is something obvious but I'm new to Linux.

I bought a laptop on eBay - on the bottom it says MD02, model MB02 (yes, once D, once B), has a rather nice aluminium enclosure. I can't find much info using google but it might be from FIC.

Anyway it came with a pirated WinXP Pro installation (which didn't recognize all the hardware correctly but the keyboard worked fine). As I didn't want to use pirated software I decided to give Linux a try. Ubuntu seemed to be very popular and very user friendly so I went for that.

Installation seemed to go fine, german language and german keyboard, but when I restarted and tried it more extensively I discovered that some keys are fine (like q, w a, s) but others just don't work right. Hitting the d (or f?) key opens the calculator. Hitting e deletes the previous letter and adds two cyrillic letters.

I tried to change the keyboard in the system preferences (I tried most keyboards) but it doesn't seem to make a difference.

What can I do?

Thanks for your help

Markus

---

### Post by barisurum on 2008-12-10
Open Applications/Accessories/Terminal and try this code:

> setxkbmap de

---

### Post by barisurum on 2008-12-10
Sorry double posted

---

### Post by loboc on 2008-12-10
in a terminal window or on one of the tty screens (CTRL+ALT+F1 to switch to the command line CTRL+ALT+F7 to get back to X windows) type

```

sudo dpkg-reconfigure xserver-xorg

```

One of the questions is about the keyboard variant if you cant find infor on it you can guess and check.

After the dialogue completes 

```

sudo /etc/init.d/gdm restart

```

keep trying to you get the keyboard right

---

### Post by markuswinter on 2008-12-10
Thanks for the advice but I can't type an e or d or c so I can't really follow it

Markus

---

### Post by barisurum on 2008-12-10
> in a terminal window or on one of the tty screens (CTRL+ALT+F1 to switch to the command line CTRL+ALT+F7 to get back to X windows) type

Code:

sudo dpkg-reconfigure xserver-xorg

One of the questions is about the keyboard variant if you cant find infor on it you can guess and check.

After the dialogue completes

Code:

sudo /etc/init.d/gdm restart

keep trying to you get the keyboard right

Yeah better solution

---

### Post by AliTabuger7 on 2008-12-10
copy and paste it into a virtual terminal
you can do all of that with mouse buttons and enter

right click > copy the text
terminal > right click > paste
enter

---

### Post by markuswinter on 2008-12-10
Except the laptop isn't on the internet yet (and I can't plug it in as I'm watching the Champions League via Sopcast on a PC) and I'm writing this on my MacBook Pro.

I'm now in the middle of trying to install Ubuntu once more and am at the stage where I select my keyboard. I set it to German and tried all the different variations (even the once like Dvorak and Macintosh which can't be right), but whenever I test it and press e then I don't get the letter but the contextual menu pops up. I also set it to UK and Ukranian with the same result. So it seems I'm stuck here.

---

### Post by markuswinter on 2008-12-10
Hmm, I just plugged in an external USB keyboard and there the e works fine. Does that mean I have an hardware defect?

Markus

P.S. Just noticed that the keys not working are 3,e,d,c and lie in a line so there might be a problem with just one pin or keyboard cable strand

P.P.S Now trying to install WinXP Home (using my PCs disc) - I just need to know if I imagined it working before ...

---

### Post by loboc on 2008-12-12
hey my dell from 2002 does that to where vertical columns of keys gout out like 7ujm or 6yhn.

 I just smash one of the keys a few times and it comes back.  Its either the "switch under the keys or the cable back to the board.
 its nice to see im not the only one who has extra keyboards stashed around my living room, office and bedroom.

---

### Post by markuswinter on 2008-12-12
Thanks to all for the help - I see the problem in Windows too so it is down to a hardware problem (probably one of the keyboard cable strands or a misbehaving soldering point as some form of signal still gets through). Sorry for any confusion I caused.

Markus

---

