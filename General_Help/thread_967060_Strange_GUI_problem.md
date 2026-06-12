---
title: "Strange GUI problem"
date: 2008-11-01
forum: General Help
---

### Post by Deatzo Seol on 2008-11-01
I have a strange problem with Ubuntu (8.04; GNOME 2.22.3).
Screenshot:
[IMG]http://i10.photobucket.com/albums/a135/snoeckx/Screenshot.png[/IMG]
See, the minimize/maximize/close buttons and the 'box' (?) have disappeared...
Very, very annoying...
Any ideas?

---

### Post by Woody1987 on 2008-11-01
Try typing in a terminal ```
metacity --replace
```

Or if your using compiz try ```
compiz --replace
```

---

### Post by Deatzo Seol on 2008-11-01
lol, this is what i get when i opened the terminal:
[IMG]http://i10.photobucket.com/albums/a135/snoeckx/Screenshot-1.png[/IMG]
Can't type anything, keyboard doesn't respond (I can paste text, but since <enter> doesn't work, I can't execute it...), ALT+F2 doesn't work either, etc...
Any alternative ways of doing it?

---

### Post by Megatog615 on 2008-11-01
Yes, there is always a way :)! Drop to a console(ctrl-alt-F1), log in, then type metacity --replace --display=:0 &. Make sure you type the & symbol as well.

Basically, you're having metacity launch and replace the current window manager on Display #0, and then run in the background(with the & symbol). To get back to your desktop session, press ctrl-alt-F7. Your window borders should be back and you can troubleshoot your problem easier now.

For now, I would disable desktop effects by going into System -> Preferences -> Appearance -> Visual Effects. Obviously something is screwy with your video card and the effects need to be disabled before you can try to get them to work again.

---

### Post by Deatzo Seol on 2008-11-01
W00t!
The window borders are back! Thank you!

---

