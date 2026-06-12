---
title: "Toshiba Satellite M65-SP811 --&gt; Issues"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by Daiver on 2006-01-29
Hi all, brand new Kubuntu user here.

I'm having a couple of issues though, which I will procede to detail below:

1) TOP PRIORITY.  My vid card fan does not stop.  Under normal Windows usage, it never came on, now it's constantly on.  Does anyone know how to solve this?

2) STUCK WITH VESA.  This laptop comes with an ATI x600 128MB and a 17" Widescreen.  I simply cannot get it to display 1440 x 900 on it.  I've tried everything on wiki, including the installation of the drivers.  Does anyone know how to get past this?

3) EXTERNAL AUDIO CARD.  I have a SoundBlaster MP3+ external USB audio card which doesn't seem to work, even though I've seen it recongized in Kubuntu.  Where can I set is as the default audio device?

That's all for now.

Any help is greatly appreciated. :)

Laptop Specs:

2.0 Ghz Centrino processor
512 MB RAM
128 MB ATI x600 video card
17" Widescreen
100 GB Hitachi HD


Regards,
Daiver

---

### Post by Daiver on 2006-02-05
Just wanted to note that this issue was never resolved.  It was impossible for me to move away from the VESA driver and get things done.  Unfortunately, no Ubuntu on this laptop :(

---

### Post by Daiver on 2006-02-12
Update for those who search:

The problem *apparently* has nothing to do with the driver, it's the screen.  Ubuntu (and other distros) doesn't detect the screen and that's why it can't start X with the fglrx driver.  It works on VESA though.

I just finished testing PCLinuxOS and it had the exact same problem.

Here's a link to other threads I've made.  If I ever resolve this issue, you can probably navigate to the soultion through them.  I hope you never run into this kind of trouble.  It's going to take me forever to find a solution...

Links:

[http://www.pclinuxos.com/forum/index.php?topic=730.0](http://www.pclinuxos.com/forum/index.php?topic=730.0)
[http://www.linuxquestions.org/questions/showthread.php?t=414040](http://www.linuxquestions.org/questions/showthread.php?t=414040)

Cheers.

---

### Post by Daiver on 2006-02-17
The display issue has been completely solved.  Apparently, the fan was solved with it.

Steps:

[LIST=1]
[*]Do everything that's in here [http://ubuntuforums.org/showthread.php?p=423584](http://ubuntuforums.org/showthread.php?p=423584)  DO NOT SKIP ANY PARTS. If you do, it won't work.
[*]Logout of KDE.  The GUI will not start after you do so, so do "sudo nano /etc/X11/xorg.conf" and change the display driver from "vesa" to "flgrx".  Save the document and type "startx" at the terminal.
[/LIST]

After that, you're home free!

Cheers!

---

