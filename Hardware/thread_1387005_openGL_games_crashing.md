---
title: "openGL games crashing?"
date: 2010-01-21
forum: Hardware
---

### Post by calis1981 on 2010-01-21
ok, i dont know if anyone else has had this problem, but i thought i would post it
first of all i could not play any games that used OpenGL, now i can thankfully, anytime i tryed to play warsow it came up with some error about DGA, i had just done a clean install of easypeasy1.5, i got really ticked off trying to use Karmic9.10, screen brightness flicker and all sort includeing my cpu getting well over the 70C temp mark, so i switch, and now im use 9.04, like i said, DGA errors, no opengl working, even tho glxgears work? and when i did glxinfo it said i had direct renderings and even stated that i have opengl 1.4!
yet no games worked? not ioquake3
not warsow
not quake2
not quake1!!!!!
i thought all hope was lost!
then i found this forum!!! and started searching it!!! i then found lots of info on the problem
(its a netbook with a intelGMA950, yes i know it aint great, but it can run guildwars in winxp at 25FPS)
so i followed these guides, and BANG!!!!!!!!! opengl work!
warsow works!
quake 1,2,3 works!!!!!!!
even got wolfenstein ET working!
nexuiz runs like crap tho?
and all the games i listed crash after about 10 minutes of playing!!! total system freeze!!
power button wont switch my netbook off! not ever ctrl+alt+backspace/del!!!!
only thing i can do then is remove the battery!
i even left it sitting, frozen, for 3 hours, to see if it would just do something! anything!!! but no
well, my netbook still works, quake3 is the only games that doesnt do this to my machine
is it something to do with the audio? as ive seen mixed things about pulse audio
or is it my graphics drivers? im useing xf86-video-intel-2.5.99.1 & Mesa7.5.2

i downloaded the source and compiled the vid drivers, was the only way i could get decent proformance, plus that version lets me use GMABooster, then i get full speed GMA950
anyway, if more info is needed ask, but im more wondering how many other people are going through this?!?!

---

### Post by t4thfavor on 2010-01-21
hook up a second monitor and put a terminal on it with ```
dmesg|tail -f
``` and watch for the last message before it freezes.

And try ctrl-alt-f1 or f2 or f3 and see if it's just the xsession freezing.

---

### Post by calis1981 on 2010-01-21
ok, only thing thats was listed is this

[5397.161705] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0

all other listings were from me trying to use my mouse then i remebered i ran a game! frozen!
but at least it let me get to another terminal
something to do with vsync?

---

### Post by t4thfavor on 2010-01-21
Definately a graphics error, Since I have no idea how to fix it, you have something else to google.

Your saying that you can get to another terminal while the game is crashed?

If so that's much better than a totally locked system.

EDIT:
Go here
[https://bugs.launchpad.net/debian/+bug/350306](https://bugs.launchpad.net/debian/+bug/350306)

They seem to have fixed it.

---

### Post by calis1981 on 2010-01-21
thanks! i googled it and i couldnt find nothing!!! all it showed me was my own post on here, lol
anyways hopefully this will fix up the problem

EDIT:
oo yea sometimes my system is totally locked, other times i can get into a terminal
it's kinda 50/50, half the time im not totally locked out, the other half ive got an expensive paper weight!

---

