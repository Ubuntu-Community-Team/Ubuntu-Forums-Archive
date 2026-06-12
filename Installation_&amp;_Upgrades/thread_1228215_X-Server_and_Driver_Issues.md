---
title: "X-Server and Driver Issues"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by lukem33p on 2009-07-31
Hello, I am Luke M, and I am new to the Ubuntu forums.
I am writing this because I have had problems with my legacy Vanta Graphics board from NVidia. I already have the correct driver in .run form. However, I run it (from terminal with root authority) and it tells me I must turn off the x server.  If needed, I can give screenshots.
My biggest issue is that once I turn off the x server, instead of GNOME being blown away, the computer does one of three things: one: shut down entirely, two: have a mixture of colors with generic code underneath (like the start-up code) or three: do the same as 2 without the colors.

Help!

Additionally, I try to run code I saw to run a program from terminal, (with number three) and it did nothing. My driver did not run. Weird, because it is a .run file.

---

### Post by lykwydchykyn on 2009-07-31
Hi luke

When you hit ctrl-alt-f2, are you presented with a text-mode login, or is the screen garbled in some way?

Regarding the .run file, you have to give it permission to run before it can be run.  You can do this through the file's properties dialog in GNOME, or a terminal like so:
```

chmod +x filename.run

```

But if you're getting an error about needing to shut X down, it seems like you've run it already?

---

### Post by ajgreeny on 2009-07-31
If post number 2 has not helped, to stop the xserver, go to Ctrl+Alt+F2 and login with username and password (not shown on screen) then type ```
sudo /etc/init.d/gdm stop
```Now run the file which you should already have made executable.  When the file has hopefully worked its magic, you can use ```
sudo /etc/init.d/gdm start
```to get back to a GUI, though you may need to use Ctrl+Alt+F7 to get back to it as well, I just can't remember.

---

