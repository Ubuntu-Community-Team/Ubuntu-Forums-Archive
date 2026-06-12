---
title: "Touchpad sensitivity"
date: 2010-05-15
forum: Hardware
---

### Post by Oliv' on 2010-05-15
Hello,

on Ubuntu 8.04 on a Sony Vaio, and currently on a Eeepc 1008HA with Ubuntu 9.04 and now 10.04 I have this crazy problem :
each time &#304; do so typing (with Firefox, openoffice, gedit...) at one time or another my touchpad will wake up and the cursor will move/click alone. So you can imagine paragraphs or even whole documents being selected without my will and being replaced by what &#304;'m currently writing. Or the cursor will go on another line and all my writing becomes messed up, pieces of sentences being mixed up all over my document.
:mad:[COLOR="Red"]&#304;t freaks me out.[/COLOR] ](*,)
&#304;n the Mouse Preferences there is this 'Disable touch pad while typing' which annoyingly ineffective.

What can I do about it? 
&#304;f &#304; want to post a Bug Report on Launchpad what package is concerned ? &#304;s there some config file somewhere I can tweak ? 

Thanks,

Oliv'

---

### Post by Oliv' on 2010-06-18
&#304; looked further at this problem.
The solution is quite forward :
/usr/bin/syndaemon -i 2 -k -d

it disables the touchad for 2 seconds when &#304; use the keyboard.

Now &#304; have to find a way to execute this command at the start of the computer.

1) &#304;n some doc &#304; found that I should put it in
~/.xinitrc 

Unfortunately it has no effect.

2) And I found that syndaemon is effectively called at some time during the boot, but by /usr/lib/gnome-settings-daemon-2.0/libmouse.so
but whith this parameters :
syndaemon -i 0.5 -k

Except modifing the binary file &#304; didn't find anywhere how to mod&#305;fy this parameter...


Help please !

Oliv'

---

### Post by sikity on 2010-06-24
I have a similar issue. 

Since the other syndaemon was also owned by my user I added a 

killall syndaemon

This is a bit of a brute force approach

An alternative to modifying your .xinit is to create a ~/.xprofile and add the lines there.

So my ~/.xprofile has

killall syndaemon
syndaemon -d -k -i 3

---

### Post by Oliv' on 2010-06-25
Thanks, I'll try this, seems to be a good idea.

What's the difference between .xprofile et .xinitrc ?

I'll keep looking for a more definite solution. I don't understand why they 'hardwired' a call to syndaemmon in libmouse.so without giving the possibility to modify the settings...

---

