---
title: "Inspiron 3500 Choppy Refresh When Scrolling"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by patryn on 2005-07-11
Hello all, i have an Inspiron 3500 with the NeoMagic nm2200 (256av) chipset for video, it seems that everything is working fine, but the refresh when scrolling on a web site, or anything else (like system menus) is very choppy and slow to refresh...any ideas?

---

### Post by oliver123 on 2005-09-08
By default Ubuntu sets the screen bit depth to 24. But the neomagic driver doesn't support hardware acceleration for 24 bits, so you have to set bit depth to 16 bit. To do this, edit the file /etc/X11/xorg.conf : go down to ' Section "Screen" ' and change the line 'DefaultDepth 24' to 'DefaultDepth 16'. That should do it (I haven't found a way to do this via a GUI).

Btw. for more info on your graphics driver, run 'man neomagic' in a terminal. There is also explained how to enable hardware acceleration of DVD-sized movies.

Oliver

---

### Post by mlord on 2005-09-09
[QUOTE=oliver123]By default Ubuntu sets the screen bit depth to 24. But the neomagic driver doesn't support hardware acceleration for 24 bits[/QUOTE]

Very odd -- the man page claims that 24-bit accel is supported for the nm2200 and higher, and the original poster has a nm2200.  But that old notebook is so slow, that it will run much better in 16-bit regardless -- only half the memory to shuffle around.

Cheers

---

### Post by vortec42 on 2005-11-17
[QUOTE=oliver123]By default Ubuntu sets the screen bit depth to 24. But the neomagic driver doesn't support hardware acceleration for 24 bits, so you have to set bit depth to 16 bit. To do this, edit the file /etc/X11/xorg.conf : go down to ' Section "Screen" ' and change the line 'DefaultDepth 24' to 'DefaultDepth 16'. That should do it (I haven't found a way to do this via a GUI).

Btw. for more info on your graphics driver, run 'man neomagic' in a terminal. There is also explained how to enable hardware acceleration of DVD-sized movies.

Oliver[/QUOTE]
Can someone give me a pointer on how to do this? I can't do it in a terminal window, as the file is read only - even when I boot into terminal only mode... 

I'm extremely inexperienced so I might be missing something obvious...

---

### Post by oliver123 on 2005-11-18
You probably have to become root to edit the file. To do that, do
```
sudo su
```
, which will give you a root shell. Then you should be able to edit the file.

When you're done with editing, leave the root shell! It's not meant for normal work! Using a root shell makes it easy to get your Ubuntu into an unbootable state. You can log out of the root shell with "exit".

Good luck,
Oliver

---

### Post by relevantrhino on 2006-05-11
I have the same problem.  I have tried editing /etc/X11/xorg.conf as stated above but it will not let me overwrite it.

I opened up terminal and ran SUDO SU but don't know where to go from there.  If anyone can point me in the right direction I would appreciate it!

---

### Post by oliver123 on 2006-05-11
Do this to get root permissions:
-Open a terminal
-run "sudo su"
-enter your password
-then the "prompt" (the short text that appears in the terminal where you can type your commands) should end with a # (this shows that you have root permissions). With these root permissions, you now have the permissions to edit system files and system configuration (that's a bit dangerous, so you should only get root permissions if you really need them - like now).

To edit the config file, do this (after you got root permissions):
-run "gedit /etc/X11/xorg.conf"
-in the text editor that opens, scroll down to the line where it reads 'Section "Screen"'. Below that line, look for a line which reads "DefaultDepth 24". In that line, change the "24" to "16" .
-Save the file (with menu "File" -> "Save").
-Exit the editor (with menu "File" -> "Quit")

-Drop the root permissions you got: in the terminal, just run "exit" .

Regards,
Oliver

---

### Post by rcatman on 2006-06-09
I have a Dell Inspiron 3200 D266XT and I installed Hoary on it to begin with. This happened with 5.10 aswell. I installed the base server then installed icewm, xserver-xfree86, x-window-system-core, xdm, numlockx and xterm which got me a basic system. I had the bit depth at 24 and the resolution was horrid! So I tried out editing the xorg.conf file, changing the Default Depth to 16, restarted, and it looks perfect! No more choppy scrolling!

Also installing two 64mb modules a minute ago helps :) Now I can install all the goodies.

---

### Post by Kjellvis on 2006-06-09
[QUOTE=mlord]Very odd -- the man page claims that 24-bit accel is supported for the nm2200 and higher, and the original poster has a nm2200.  But that old notebook is so slow, that it will run much better in 16-bit regardless -- only half the memory to shuffle around.

Cheers[/QUOTE]

What I've found is that it doesn't accelerate video in 16bit, only 24.  And it doesn't "accelerate" the 2d desktop in 24bit, only 16.  So you have to choose between choppy desktop or choppy video.   Maybe there is a sollution on the man page, but I removed Ubuntu and installed PC-BSD instead because I just couldn't get the sound working on the Inspiron 3500.

---

