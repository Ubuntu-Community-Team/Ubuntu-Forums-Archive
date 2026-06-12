---
title: "graphics problem."
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by sohaibma on 2006-11-26
I have a VIA VN800 built-in graphics processor in my laptop.
i have tried openchrome drivers through the process stated here [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). It is acting same as the vesa driver, the screen becomes scrambled when i run a game and the video playback in any format is very slow:


please help me out here how do i make my Vn800 work.

---

### Post by taurus on 2006-11-26
Would it work if you use vesa?

---

### Post by karlh on 2006-11-27
I had a similar problem with the display on my (VN800) laptop becoming scrambled just as the login manager (KDM/GDM) started.

I switched to the fbdev driver in /etc/X11/xorg.conf and it solved the problem.

Change:

Driver      "vesa"

to:

Driver      "fbdev"

That won't help the speed at all, but it might make the screen garbage go away.

Here's what you can do if you have trouble getting the right resolution with fbdev (like I did):

On my system, the video mode defaulted to 1024x768, but my laptop was 1280x800, so the fonts looked bad. I couldn't find any documentation on how to get a 1280x800 mode framebuffer.

Here's how I fixed the problem:

I booted up with the alternate install cd, although it might work with the regular cd too.

At the grub prompt, I pressed f4 to select the correct display mode.

after it booted, I pressed alt+f2 to open a console (From a graphical login, you would press control+alt+f2.)

At the console, I typed 'export'

You should see something like vga=0x3b0 in the output. (I can't remember the exact string.)

I added that to the boot commant in /boot/grub/menu.lst

(I still have to install a 1280x800 splash screen becuase the old one shows up off center.)

You might not need to do this at all. Only do it if you're having trouble with the resolution, because it's a lot of bother, and there's lots of room for error.

Hope it helps.

Karl

---

### Post by sohaibma on 2006-11-30
ok i got the openchrome driver to work.
the resolution is fine but i still get the scrambled screen during ubuntu loader and logim for a few seconds.

i am fine with this, but when i start many if the games i have downloaded from the repositories. the screen scrambles up and i have to close the game to bring the normal screen.

how do i fix this?

PS: fbdev is not working.

---

### Post by sohaibma on 2006-12-04
ok i just noticed something new.
when i put on the via drivers the videos donot play, but when i switch to vesa driver the videos do play but slow.

can anyone figure out what the problem is?

---

