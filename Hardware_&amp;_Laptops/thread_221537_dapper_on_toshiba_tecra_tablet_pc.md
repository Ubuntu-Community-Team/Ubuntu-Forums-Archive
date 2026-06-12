---
title: "dapper on toshiba tecra tablet pc"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by tukster on 2006-07-23
hello ppl.

i've recently bought a used tecra m4 tablet and of course its already running dapper. i've got some questions since its my first linux on laptop:p 

this will probably be for tablet users.

what app are u using to rotate the screen?
xrandr isn't working for me. when i try:
> xrandr -o left
nothing really happens.

i've got stylus working for pointing and clicks but i miss rightclick option (press & hold) for opening context menus, ](*,) 

and last but not the least TEXT INPUT.
is there any alternative to GOK, with handwritting recognition?

thx 4 all your replies :)

---

### Post by drdrewusaf on 2006-07-26
For the right click w/ your stylus button (**not** the hold and wait feature), look into the xsetwacom command.  Personaly, in windows, I liked my right click to happen w/o having to touch the screen.  I liked being able to hover and right click.  After many hours (I am a complete noob) of fiddling around I finally came up with this:

[FONT="Lucida Console"]xsetwacom set stylus button2 3

xsetwacom set stylus TPCButton 0[/FONT]

If you run these two commands at startup (every time) your right click will work when hovering and when touching the screen.  To run them every start up and because I am a noob and don't know any other way to run scripts at startup, I added them to the top of the rc.local file.  Contrary to popular belief, this file doesn't not run on its own after chmoding it to be able to execute, or if it does, then it loads too soon.  So I just created a new "session" in the session manager like this:

Go to System>Preferences>Sessions
Click the Startup Programs tab
Click Add
Type this (without the quotes): "/etc/init.d/rc.local start"

If you restart X it should work.  Make sure you chmod the script to be able to execute!

Let me know how it goes!!




Drew

---

### Post by Henrik on 2006-08-02
> **tukster said:**
> 
and last but not the least TEXT INPUT.
is there any alternative to GOK, with handwritting recognition?

SOK is designed to work with tablets: [https://wiki.ubuntu.com/Accessibility/Projects/SOK](https://wiki.ubuntu.com/Accessibility/Projects/SOK)

---

