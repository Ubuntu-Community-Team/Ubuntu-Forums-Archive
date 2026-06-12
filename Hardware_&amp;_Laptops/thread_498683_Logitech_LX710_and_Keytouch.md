---
title: "Logitech LX710 and Keytouch"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by muecker on 2007-07-11
I just bought a Logitech LX710 and am trying to configure it under Feisty.  I'm using it as a second keyboard for my Thinkpad T60 laptop. It is working great except that I am having problems configuring the FN+x keys.  The FN+F4 key opens the calculator, but I cannot get any other key to work.  The multimedia keys (other than shuffle) work.  I also do not get anything from the zoom and rotate keys.

I tried xev and it doesn't recognize when I press those keys.  I tried keytouch and it also does not recognize those keys.  If I select my receiver, it will open if I click on the FN+F4 key but still does not recognize the remaining function keys.

I did find that if I use my laptop's FN key with the same combination that it opens the expected program.  FN+F2 on the laptop keyboard locks the screen (default combination for the T60 keyboard) and opens Open Office Writer.

Can somebody tell me how to get the FN key combinations to work?  Thank you.

---

### Post by rbprogrammer on 2007-08-09
i have the same exact keyboard, only with a different laptop, and feisty kubuntu..

did you get the keys to work correctly?? b/c i want my keys to do more as well.  i have the same problem; the calculator comes up but nothing else.

the other issue with me is that moon key in the upper right.  i want it to lock my computer instead of putting into hibernation or stand-by, whichever it does.

if you were not able to get the keys working, does anyone else know how we can fix this??

---

### Post by donmiguel on 2007-09-08
well, what about you guys? i didnt find any solution yet

---

### Post by rbprogrammer on 2007-09-10
> **donmiguel said:**
> well, what about you guys? i didnt find any solution yet

unfortunately no, i did not find any solution.  when i used the command "xev" i found that the FN key i think is not sending any data.  as far as i know, when i use the xev command and i press a key, then i am able to configure that key. when nothing happens, then the key is probably dead or something :( ..

---

### Post by donmiguel on 2007-09-11
yeah, i experienced the same.. but it's impossible..
you sure did also get an installation cd vor windows, right... so there a software would be installed, which would recognice those keys, so they should send ANYTHING 

i don't get it.. :) thanks for the reply though

---

### Post by 99bluefoxx on 2007-09-24
i got the same problem as the OP
also the mouse that came with my lx710 has two additional buttons that don't seem to do much
in certain programs they will left click once but don't double click but not much else

---

### Post by rbprogrammer on 2007-09-25
> **99bluefoxx said:**
> i got the same problem as the OP
also the mouse that came with my lx710 has two additional buttons that don't seem to do much
in certain programs they will left click once but don't double click but not much else

i got that too.. for me, one of the buttons is a right click and the other is like pressing the middle button.  i guess it only really came in handy in firefox when i wanted to open something else in a new tab......

:(

---

### Post by 99bluefoxx on 2007-09-25
all they do for me is click
not double, left, back or middle
i cant click and drag with them and they only activate in a few programs
i wanna assign them a function like copy and paste and such

---

### Post by rossmoore on 2008-05-06
I've found a reference to this problem elsewhere. I don't know if it has been fixed in Hardy, but if you run:

showkey -s

as root you can see the scancodes from these keypresses direct from the USB hub. The problem here is that the USB hub is sending the key presses to the kernel, but it doesn't recognise them at all and so it's not getting to xev, which is where you normally see the key press and release events.

You can find a reference about this problem at the bottom of this page (below), although the lineak project this links to appears to be not currently live.

[http://lineak.sourceforge.net/index.php?nav=showdoc&docid=LinEAK_support_HOWTO&doctitle=Keyboard%20support%20HOWTO](http://lineak.sourceforge.net/index.php?nav=showdoc&docid=LinEAK_support_HOWTO&doctitle=Keyboard%20support%20HOWTO)

---

