---
title: "The best on-screen keyboard for Tablet PC you can get by now..."
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by anasofiapaixao on 2006-08-14
**EDIT 2:** _DON'T DO THIS_ until I figure out what is going on that onboard is lauching in ultra micro size.

Tired of all GOK problems, it was about time I finally found the link and have tried [SOK]("http://www.ubuntuforums.org/showthread.php?t=192758") (Simple On-Screen Keyboard, now rebranded [onBoard]("https://wiki.ubuntu.com/Accessibility/Projects/onBoard")), and hell IT MADE MY DAY, week and month altogether! ^_^ But the program "out of the box" does require some serious tweaking/makeup. I have done some things to turn this version of SOK more tablet-friendly, stuff I have been noticing with the use. Try it out and make suggestions! :)

**CHANGELOG:**
*Aug-14*
[LIST=1]
[*] Default window size is smaller (may not be better for people with disabilities but certainly is for tablet PC users)
[*] Added the following keys (please note that this refers to the portuguese keymap... sorry!):
[LIST]
     [*]',' / ';' (comma/comma and a dot);
     [*]'.' / ':' (dot/double dot);
     [*]'-' / '_' (dash/underscore);
     [*] Tab;
     [*] Arrows.
[/LIST]
[*] Rearranged the keys so that they are 'glued' to each other (and so making it easier to type with a stylus)
[*] Altered the colours (to match my theme :P)
*[*] NOT NECESSARY ANYMORE: Commented out the part to choose the layout; it will just load the default (my ubuntu.sok tunning). It can become seriously annoying if you're using it to work normally.*
[/LIST]

*Aug-23*
[LIST=1]
[*] File now is a patch rather than a full install
[*]Stuff altered (i.e. file patchs, etc) to match the new onBoard definitions.
[*] Added the following keys (again, this is the portuguese keymap):
[LIST]
     [*]''' / '?' (apostrophe/question mark);
     [*] Right shift.
[/LIST]

[/LIST]



**INSTALL:**
- If you don't have onBoard, [get it here]("https://wiki.ubuntu.com/Accessibility/Projects/onBoard/dev?action=AttachFile&do=get&target=sok-packages7.tar.gz").
- After installing onBoard, open a terminal and type this:```
wget http://anasofiapaixao.iespana.es/apps/sok/onboard-tablet.tar.gz
tar -xzvf onboard-tablet.tar.gz
sudo sh onboard-tablet.sh
```
The mv command to backup KbdWindow.py doesn't work for the sake of I-don't-know-what, and the secondary panes are acting weird: either the red button to close doesn't appear on one of them or they just swap places. A little help with this would be appreciated.
Also *how do I make the black margins thinner and with another color*? I am totally puzzled on this.


Also, you'll probably have to edit the chars that appear on the key with shift on to match your real keymap. You'll find them right at the beginning of the /usr/lib/sok/layouts/tablet.sok file.

[IMG]http://anasofiapaixao.iespana.es/pics/sok.png[/IMG]

**Note:** In case the legacy SOK tunning is needed (whether because you intend to make make a trip to the past, make you dog ride a pink elephant, or whatever else) you can find it [here]("http://anasofiapaixao.iespana.es/apps/sok/sok-1.htm").

---

### Post by 23meg on 2006-08-14
Looks great. Thanks for the heads up; I've been meaning to try it for a while. I'll test it as soon as I get my tablet repaired.

---

### Post by Henrik on 2006-08-19
Great! Thanks for testing and tweaking! We've only been working on it for 2-3 and have mainly focused on the accessibility aspects, but the tablet PC use has also been in our minds. I'm glad to see that you got it working fairly easily for that purpose. We'll look at whatchanges we might want to integrate into the main version.  

btw, the project has changed name to **onBoard** and is hosted [here](https://wiki.ubuntu.com/Accessibility/Projects/onBoard) (latest source [here](https://launchpad.net/people/onboard/+branch/onboard/main)).

---

### Post by t0rtois3 on 2006-08-24
anasofiapaixao onBoard should remember the size it was when it was last open.  So just resize it and it should stay that size.  

It's going super micro size I think because it saves the new size as one number.  On next start up your patch makes it start smaller and the new size is saved.  Each time you start it, it will get smaller and smaller.

---

### Post by anasofiapaixao on 2006-08-24
Yeah, that didn't happen in the old SOK, and I didn't even consider it... But right now I can't do anything because [my laptop is unusable]("http://www.ubuntuforums.org/showthread.php?t=241691"). Actually this has has stolen a lot of my trust in (Ubuntu) EDIT: TOSHIBA...

---

