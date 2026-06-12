---
title: "Forcing active VGA port (laptop)"
date: 2008-09-28
forum: Hardware
---

### Post by epitaph on 2008-09-28
Dell Vostro 1000
Ubuntu 8.04
Integrated ATi Xpress w/ fglrx

Greetings!

I use the external VGA port on my laptop quite often and it's a nuisance to have to reboot the machine with a vga cable plugged in each time I want it to detect and allow the use of an external monitor. Is it possible to just force the laptop to always just output to the VGA port no matter what?

For now, the best solution I have is to ctrl+alt+backspace once a VGA cable is plugged in, but this kills all active applications. At least this drastically reduces the time it takes to get an external screen.

Thanks in advance for any suggestions.

---

### Post by epitaph on 2008-09-28
Looks like I should have spent more time investigating it but I found a much easier way to use the external port.

All that's needed is:

```
aticonfig --enable-monitor crt1,lvds
```

And I have a cloned output of the desktop on both the external monitor and the laptop!

To get the brightness buttons on my laptop to work I used someones script that echo'd in the values and then was mapped to the function shortcut keys.

I'm pretty new to most of this still, but how would I go about mapping the Fn+F8 (crt/lcd switch) key to a script (and what should the script contain) that will toggle between:

```
aticonfig --enable-monitor crt1,lvds
aticonfig --enable-monitor lvds
```

Also, in each toggle I'd like to be able to change the display resolution (from 1280x800 when only using lvds to 1024x768 when I'm using the crt1 and lvds).

I think this is all doable, I just don't have the know-how or experience to do it, hopefully someone will be kind enough to give me a hand. Thanks in advance!

---

### Post by epitaph on 2008-10-03
I figured I should maintain this for anyone else who comes across this thread.

By using the following script (I modified the resolutions) I got my Fn+F8 crt/lcd key to work on the Dell Vostro 1000!

[http://www.thinkwiki.org/wiki/Script_for_Dynamic_Display_Management_with_fglrx](http://www.thinkwiki.org/wiki/Script_for_Dynamic_Display_Management_with_fglrx)

Either replace /etc/acpi/videobtn.sh or have it simply call the script like the author of the tutorial did. And remember to change the resolution/refresh to suit your monitor(s).

Pretty happy that's settled now!

---

### Post by fkeidjn on 2008-11-19
Will this work on Ubuntu 8.10 Intrepid?  Or will I need to do something else?

---

### Post by epitaph on 2008-11-20
I did not upgrade to 8.10 and I don't intend to. I tend to stick with what works until I need something provided in a new version.

I imagine it is either the same or very similar. As long as the aticonfig tool still works I don't see why this wouldn't either.

Using aticonfig to enable or disable monitors should work on any laptop that's using fglrx unless there is a hardware issue with outputting to the external VGA port.

I also only ever use this to clone my desktop, I never set things up as two separate monitors.

---

