---
title: "bash scripts  in terminal (bash/shell scripting?)"
date: 2008-10-10
forum: General Help
---

### Post by a-converted-sparky on 2008-10-10
Hi everyone (i am a n00b)

Im using hardy heron (loving it by the way!)

basically i want to brighten up my terminal, a couple of work colleagues have some bash scripts but aren't very forth coming with "how to"

i have had a fudge about but its not quite how i want it,

so far my terminal looks like:

84% free
(sparky@blue-screen) 

However i would like it to look more aligned and funky (plus some colour wouldn't go amiss! ..maybe show some other kool values/processes) anyone have some examples or shed some help on it for me?

Thanks in advanced,

P.S
So far my config looks like:

df -P | grep gvfs-fuse-daemon | gawk '{printf "%i%% free", 100-$5}'

---

### Post by conundrumx on 2008-10-10
Hi, it sounds like you want to make changes to your PS1 variable, not do shell scripting.  Perhaps I misunderstood.

[http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

Take a look, see if that's of use.

---

### Post by loomsen on 2008-10-10
I hope I understand you right.

I think what you are basically looking for is conky then.
Conky is a Systemmonitor, very highly configurable, and prints anything you can print using fonts.

Plus a transparent terminal, et voila, looks like this for me.
I think this is what you actually want, this way you can still use the terminal for dynamic purpose while conky monitors your system.

Just ask google about conky, the are like 1 mio howtos for conky, tho it ain't too hard to set it up :)

[[img]http://www.ubuntu-pics.de/thumb/4293/screenshot_06_04zzgU.png[/img]](http://www.ubuntu-pics.de/bild/4293/screenshot_06_04zzgU.png)

If this is not what you are after...

cat all > /dev/null

*edit*
very nice hand conun! Thats actually a very good idea, thanks for pointing towards it, wouldnt have thought of this possibility. 
Nice 1, thx again.

---

### Post by a-converted-sparky on 2008-10-10
Yeah i have conky all setup and it looks great,

I think our man conundrumx has hit the nail on the head, yes PS1 variable is exactly what i was after - many thanks!

Its not like for anything pratical as such just want it to look pretty really :0)

Cheers again

---

