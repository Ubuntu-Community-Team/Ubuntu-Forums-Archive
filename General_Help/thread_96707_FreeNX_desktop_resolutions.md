---
title: "FreeNX desktop resolutions"
date: 2005-11-29
forum: General Help
---

### Post by MrFahrenheit on 2005-11-29
I have a laptop with a maximum resolution of 800x600 that i'd like to use FreeNX on to connect to a Desktop that runs at a resolution of 1024x768

If i connect to the Desktop computer via FreeNX,the desktop is cropped and I can't see the menus and panels.

If, in the FreeNX session, I set the resolution to 800x600, It works fine on the laptop, but then the Desktop computer uses that as its resolution.

How do I set it up so that the Laptop can connect to the Desktop at 800x600 but when I just use the Desktop, it defaults to 1024x768?

---

### Post by MrFahrenheit on 2005-11-29
Or are there any programs besides FreeNX I should be using?

---

### Post by ScreemingBlue on 2005-11-30
Try using VNC.

---

### Post by Roman27 on 2005-11-30
I use FreeNX everyday.  I connect from my work PC (Windows XP) to my home computer (Ubuntu 5.10) with the [NoMachine Windows client]("http://www.nomachine.com/download_client_windows.php") almost everyday.  My home computer runs at 1280x1024.  My work PC is set to 1280x1024 too, but I have the NoMachine client set to put my Ubuntu session in a 1024x768 window.  It works great.  I don't have any problems with my home PC resolution being effected at all by the resolution that I set the NoMachine client to.

Hmmm...  That just gave me a thought.  When you say, "If, in the FreeNX session, I set the resolution to 800x600...", does that mean you're setting the resolution with the Ubuntu resolution tool?  If so, that's not really the best way to do it.  You want to set your FreeNX/NoMachine client so that it negotiates the resolution you want.  Here's a screenshot of how I'm setup:

[[IMG]http://img291.imageshack.us/img291/446/nomachine4rk.th.png[/IMG]](http://img291.imageshack.us/my.php?image=nomachine4rk.png)

I hope that helps you.

---

### Post by matthewv on 2005-11-30
ditto.. exactly the same here, except I use 1024 x768 at home and just available area at school..

---

### Post by MrFahrenheit on 2005-11-30
[QUOTE=matthewv]ditto.. exactly the same here, except I use 1024 x768 at home and just available area at school..[/QUOTE]

The problem I'm running into, is that if I use 1024x768 at home, then 'available area' when the resolution is 800x600 on the client, then I get a window with only the center of the desktop in it, the menu bar is off screen.  

I'd like to use fullscreen mode at 800x600 without having the edges of the desktop cropped off.  Is that even possible with FreeNX?

---

### Post by Roman27 on 2005-11-30
Well, I did a few tests.  I can't get 800x600 or 640x480 to work correctly either.  It must be too low.  ???  Both of the lower resolutions just gave me portion of the center of the desktop.  I couldn't see either of the menu bars.

---

### Post by MrFahrenheit on 2005-11-30
[QUOTE=Roman27]Well, I did a few tests.  I can't get 800x600 or 640x480 to work correctly either.  It must be too low.  ???  Both of the lower resolutions just gave me portion of the center of the desktop.  I couldn't see either of the menu bars.[/QUOTE]

Woo Hoo!  I'm not crazy!

seriously though, thanks for trying that out.  This community is really great and it's one of the reason that I've switched all of my personal computers over to linux.

So anyone have any idea how to fix this?  Or should I try out VNC? (haven't tried that yet)

---

