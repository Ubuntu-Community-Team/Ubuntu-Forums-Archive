---
title: "No GUI in Ubuntu 9.10!"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by johannes.morfeldt on 2009-11-12
Hi!

I upgraded from 9.04 to 9.10 thinking that the OS would improve. I was wrong!
I've spent quite a few hours trying different solutions but nothing works!

When I boot the computer everything works until it tries to start X, even the new splashscreen. The screen shuts off and the on again and just stay blank. If I use ALT-F2 to reach a shell everything works in text-mode. If I let the computer rest at the blank screen the screen eventually goes into low-power-mode, but switches back on if I touch the mouse.

If I type *startx* in the console it says that an X server is allready started and if I then switch to the console with the X server (ALT-F7) the mouse becomes active, so I can move the classic Linux-cross around. But I can't do anything else.

I have a HP Pavilion ze2348ea with a ATI Radeon Mobility 200M.

I would be grateful for any suggestions, but I've allready tried to change drivers and reinstall drivers (the radeon, ati and fglrx).

I would also like to know if anyone knows how-to reinstall the 9.04 distribution without formating the HDD. I don't have any other drive to put my stuff on and repartitioning is a pain in the ***!!!

I really think that Ubuntu should have waited to release this dist before these problems were resolved. The OS asked me to upgrade when doing the daily search for updated software and then you would think that the upgrade should be safe to do. At least they should include a way to uninstall it if it does not work.

---

### Post by johannes.morfeldt on 2009-11-12
One more thing,
how the hell do you stop the GDM service.
When I try
[I]sudo service gdm stop
[/I]it says 
[I]stop: Unknown instance:

[/I]When I try
[I]sudo /etc/init.d/gdm stop
[/I]it tells me to try the above mentioned syntax.

?????

---

### Post by werdberd on 2009-11-12
I'm not sure why those commands you used to stop gdm didn't work, but I guess if you really wanted to stop gdm you could try ```
sudo killall gdm
```

---

