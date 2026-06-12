---
title: "Toshiba L655 and Terminal Questions"
date: 2012-05-08
forum: Hardware
---

### Post by vaccix on 2012-05-08
First of all sorry if I posted this in the wrong place but I'm new here.

   I have been trying to use this to fix the problem with my battery so that I can monitor it ([http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)) and I got to the point where I am supposed to edit the file, however, I can use my delete key to delete the text, but I can not input new text. 

   Also, my webcam, It works with photobooth aps and whatnot, but when I try to use it on Facebook or another site I get the Allow or Deny pop-up and flash just freezes. I even tried (at my own discretion) to use my webcam on chat roulette and had the same problem.

EDIT:
I also forgot to mention that my Search/Find option in Terminal does not work for me.

   I've searched around quite a bit lately and haven't solved my issues yet. Any help is greatly appreciated. :/

---

### Post by vaccix on 2012-05-09
bump

---

### Post by Toz on 2012-05-09
Looks like its asking you to use vi to edit the file. vi is no an easy editor to use. Try replacing **vi** with **nano** (console text editor) or **gedit** (gui text editor) for an easier to use editor.

---

### Post by ahallubuntu on 2012-05-09
You've got several questions in one thread.  It might be best to start separate threads about the webcam and about basic Terminal questions.

FYI, the article you link to mentions using the ancient "vi" text editor which predates Linux itself.  Old-time Linux hackers use vi as a safe standby but it's a terribly unfriendly text editor.  All you are trying to do is edit a text file, and you can do that with other text editors.  Instead of vi try

gedit

which is much more friendly than vi.

(so instead of "vi DSDT.dsl" you'd type "gedit DSDT.dsl ".)

FYI, this article you link to is an advanced change in my opinion, not something I would recommend to someone who isn't comfortable using a terminal.  The author of that post created a custom kernel for Ubuntu 11.10 just to add the changes; maybe he has or will do the same for Ubuntu 12.04 LTS for you?

---

### Post by vaccix on 2012-05-12
Thanks for the replies guys!
Yeah sorry for so many questions, I'm just new with linux and I learn better with somebody showing me how to do things in person and nobody I know uses linux. TYVM for the info too! Hopefully this makes it easier.

---

