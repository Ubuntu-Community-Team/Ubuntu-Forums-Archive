---
title: "dual screen in intrepid - default monitor?"
date: 2008-11-03
forum: Hardware
---

### Post by magiver on 2008-11-03
Hi

I installed intrepid today, and was glad to see that I was, finally, able to handle a dual screen setup between my dell inspiron 1420 and my 32" sony lcd tv.
There's just a little problem. The "default" monitor is the tv...
By default I mean the monitor that shows the menu bar and the monitor where every open application is shown.
I will like to use the tv for things like skype, email o video files (secondary stuff) and use the laptop display for actual work (web browsing mainly =) ).
Does anyone know how to do this? What I want is to able to select what is the display that will show the programs that I run.

Thanks for the help and excuse me for the weird redaction. I'm from south america

---

### Post by mark2741 on 2008-11-03
Same here. I love the dual-display support in 8.10, but the one thing I would like that I haven't been able to figure out how to solve is how to switch the displays so that the gnome menubar and such is on the other display.

---

### Post by mark2741 on 2008-11-06
I was able to accomplish getting my other display to be the primary/one with the gnome menu on it. Unfortunately though I had to do it the ultra-hard way...

I have had a lot of problems with Ubuntu (I used to use it as my primary OS for a year, back in 2006, but then bought a mac, then back to windows vista, blah). Never had problems with it before but my current machine doesn't seem to like the install cd of 10.8, so I gave up and installed 8.04. I configured the dual displays properly in there. I'm pretty sure the setting that *looks* like it should do what we wanted is what did it for me - the 'make this the primary desktop' checkbox one. I remember that not working in 10.8 though. Anyways, I did that in 8.04 and then today I did an upgrade to 10.8 (which worked), and it kept my displays setup properly. So, there's hope : )

Now if I can just get Firefox to stop graying out on me on any javascript-heavy pages like Gmail...

---

### Post by mark2741 on 2008-11-07
Due to some other issues (mostly due to Vista and my want to go to Ubuntu as my primary OS), I just did a complete reinstall of 8.04 and then immediate upgrade to 8.10.

This time I didn't enable the nvidia driver in 8.04 before doing the update to 8.10. Once I had 8.10, I enabled the nvidia driver, rebooted, and then tried setting the better of my two monitors as the primary. As we noticed before, it doesn't work. So it's a bug in 8.10 (it worked in 8.04).

HOWEVER....duh.....I then realized that all you need to do is right-click on the gnome bars (you have to do each independently), deselect the "lock this panel" option and then right-click again and select "move" (might be "move this panel", can't recall) and then just move it over to the next monitor! Gotta do it for each. Works fine now!

mark

---

