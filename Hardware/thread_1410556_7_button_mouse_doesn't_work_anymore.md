---
title: "7 button mouse doesn't work anymore"
date: 2010-02-18
forum: Hardware
---

### Post by schmidtbag on 2010-02-18
so i've been running 64 bit kubuntu 9.10 since its release and i was using the program btnx to configure the extra 4 buttons on my mouse to do whatever i wanted.

well, now, i've changed my repository list to ubuntu 10.04's (yes, i know its risky, but i figure if anything goes wrong, a gradual upgrade is easier to fix than a complete upgrade) and now btnx doesn't work anymore.  i went to go find other solutions, such as xbindkeys, but that program doesn't work either!  i've tried messing with xorg.conf and that doesn't do anything.

i'd like the buttons to act as keyboard shortcuts, so they work the same for everything i use, and so 2 of the buttons will perform different actions than their intention.


does anybody know what still works for ubuntu 10.04?

---

### Post by schmidtbag on 2010-02-20
bump

---

### Post by pi/roman on 2010-02-21
Karmic and Lucid input configurations are completely incompatible with each other. I've used both of them so I know that Karmic requires hal configuration and Lucid requires udev configuration.  If repositories were switched then I would expect some of the devices to just stop functioning altogether.  So as long as you are still getting basic functions out of your mouse I would feel lucky.

---

### Post by Contrast on 2010-03-15
Bump. I'm having this same issue on 10.04 (fresh install). I searched the repos for "mouse button" and the only relevant results were the ones which have already been mentioned - btnx and xbindkeys, both of which are broken.

Edit: As I was starting to set up EasyStroke, I noticed it allows you to use more than one button for gestures. Since it allows you to bind actions to single clicks, this actually does the job quite nicely.

---

### Post by schmidtbag on 2010-03-15
i forgot to post back that xbindkeys did end up working.  i'm not using my kde setup at the moment, but i remember in the xbindkeys gui configuration program, my mouse was set up something like:
b:1 - left click
b:2 - middle click
b:3 - right click
b:4 - mouse wheel up
b:5 - mouse wheel down
b:6 - nothing
b:7 - nothing
b:8 - forward button
b:9 - back button
b:10 - nothing
b:11 - nothing
b:12 - up button
b:13 - down button

i don't remember if thats how you configure the mouse buttons.  just keep going up the list until you reach the button you're looking for.  i'm not sure why my buttons 6, 7, 10, and 11 don't do anything (they must be designed for something else).  i don't remember if something like b:8 is actually the way you type it in xbindkeys-config, its been over a month since i've configured it.  you can check online how to add mouse button events, just keep pushing the number up and you should get the right one eventually.  also, your xorg.conf might have something to do with it

---

