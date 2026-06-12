---
title: "keyboard shortcut to type email address?"
date: 2008-07-13
forum: General Help
---

### Post by stinkinrich88 on 2008-07-13
hello, 

When I was using windows I made a little VB application that would type my email address into whereever my cursor was. I set a keyboard shortcut for the program so I could fill in internet forms well quick. Is there any way I can make a little script to type my email address in linux? 

thanks!

---

### Post by billynomates on 2009-01-01
Get this:
```
sudo apt-get install xmacro
```

Then save the below text in a file called (for example) "emailad" substituting the letters at the end of each line with your email address. Remember to repeat each letter twice, once for KeyStrPress and once for KeyStrRelease. You also need the "Delay 1" on line two to stop it getting confused and writing over itself.

```
MotionNotify 687 627
Delay 1
KeyStrPress y
KeyStrRelease y
KeyStrPress o
KeyStrRelease o
KeyStrPress u
KeyStrRelease u
KeyStrPress r
KeyStrRelease r
KeyStrPress e
KeyStrRelease e
KeyStrPress m
KeyStrRelease m
KeyStrPress a
KeyStrRelease a
KeyStrPress i
KeyStrRelease i
KeyStrPress l
KeyStrRelease l
KeyStrPress a
KeyStrRelease a
KeyStrPress d
KeyStrRelease d
[B]KeyStrPress Shift_R
KeyStrPress at
KeyStrRelease Shift_R
KeyStrRelease apostrophe[/B]
KeyStrPress h
KeyStrRelease h
KeyStrPress e
KeyStrRelease e
KeyStrPress r
KeyStrRelease r
KeyStrPress e
KeyStrRelease e
[B]KeyStrPress period
KeyStrRelease period
KeyStrPress c
KeyStrRelease c
KeyStrPress o
KeyStrRelease o
KeyStrPress m
KeyStrRelease m[/B]
```

Then in your compiz shortcuts (General options > Commands) paste this in the command line part:
```
cat /path/to/script/emailad | xmacroplay -d 0
```
(The -d 0 makes sure it does it as fast as possible)

Then choose your shortcut in the corresponding Key Bindings part, and you're done!

Simple.

---

