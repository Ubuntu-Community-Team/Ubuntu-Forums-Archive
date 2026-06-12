---
title: "window painting problem while mouse over in intrepid"
date: 2008-11-03
forum: General Help
---

### Post by feistybee on 2008-11-03
I had installed, ubuntu 8.10 in my machine. Here is my configuration,

AMD X2 Athlon x64 processor
ASUS M2NPV-VM motherboard with nvidia geforce 6150
1 GB RAM

Since I have nvidia, the drivers are not loaded by default. So I got only 800x600 resolution. After that i installed nvidia-glx-177 package. The screen resolution is fine now. 

But whenever I mouse over the window title bar, the title bar is not painted properly. It fades and displayed in white color. It mostly happens when I mouse over the minimize, maximize and close buttons. Please find the image.[IMG]http://lh3.ggpht.com/_U82VN4-oa1s/SQ6jDGuIw1I/AAAAAAAAABI/OYQUOi9143Y/s576/error1.png[/IMG]

I have uninstalled the nvidia driver and checked. It worked fine. After that I installed again. Same pbm occurs. 

Any solution?

---

### Post by mdurham on 2008-11-03
> Any solution?
I installed Emerald to get rid of this problem. Give it a try.
Cheers, Mike

---

### Post by feistybee on 2008-11-03
I guess Emerald is the theme. I want to use 'Human' theme. I like the 'Human' theme :D.

Any suggestions on using 'Human' theme? Does installing Emerald will work in 'Human' theme?

---

### Post by feistybee on 2008-11-03
I guess Emerald is the theme. I want to use 'Human' theme. I like the 'Human' theme :D.

Any suggestions on using 'Human' theme? Does installing Emerald will work in 'Human' theme?

---

### Post by DrMelon on 2008-11-03
Emerald is a window decoration manager, so you should get the Human theme for it.

Or, in fact, anything. You can get all sorts of cool themes for Emerald!

---

### Post by Ryan Yo on 2008-11-03
I've had this problem too since I installed 9.10. I'd rather not install another program to fix it - is anyone else getting this?

---

### Post by :) Smiley :) on 2008-11-03
I have that same problem.
I tried a different GTK theme (DarkRoom). It seems not to do it as much as Human.

---

### Post by Vanadaar on 2008-11-03
I have the exact same problem. Does it right after a fresh install, enabling compiz effects. Plain clearlooks does not do it.

---

### Post by A. Bimbao on 2008-11-03
It happens to me too. When I set Visual Effects to 'None' the painting of window borders is fine, but when I try 'Normal' they go white when my pointer is above. I have GeForce FX 5200 and use driver version 173.
Anyone?

---

### Post by feistybee on 2008-11-05
I have installed Emerald. Still the problem is there.

And also I tried the 'Dark Room' theme. In 'Human' I got white patches, in this theme am getting dark color patches. So issue remains the same.

Anyone knows the soln for this? Is it a theme problem or nvidia driver problem?

---

### Post by alwayshere on 2008-11-05
disable visual effect and see what happens

---

### Post by mdurham on 2008-11-05
I think it's an Nvidia problem.

---

### Post by outferno on 2008-11-05
I also got the same problem on a fresh install of 8.10 i386 version on my tx1000z.  Everything else works great - just that weird title bar problem.  Also Emerald doesn't let me switch themes, so I just uninstalled it and let it be.

---

### Post by A. Bimbao on 2008-11-05
With visual effects disabled everything is fine. Is there an alternative for 173 Nvidia driver?

---

### Post by alwayshere on 2008-11-06
Try 

gksudo displayconfig-gtk

and if ya driver set to nv change it to nvida ..................

see what that does .

---

### Post by mdurham on 2008-11-06
> **alwayshere said:**
> Try 

gksudo displayconfig-gtk

and if ya driver set to nv change it to nvida ..................

see what that does .

Thanks alwayshere, nice try, but it does nothing to fix the problem.
Cheers, Mike

---

### Post by alwayshere on 2008-11-06
Human theme may be making trouble 
Change the titlebar of the Human theme (eg. to clearlooks)
-or-
Disable Compiz

You could try Compiz swithch  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Worth a go

---

### Post by mdurham on 2008-11-06
> **alwayshere said:**
> Human theme may be making trouble 
Change the titlebar of the Human theme (eg. to clearlooks)
-or-
Disable Compiz

You could try Compiz swithch  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Worth a go

alwayshere, I think you are right. I changed to clearlooks and have no probs (so far anyway). Maybe it's the combination of Human and Nvidia?

---

### Post by A. Bimbao on 2008-11-10
There'a a solution for this, just reinstall and when offered hardware drivers pick Nvidia accelerated graphics driver (version 96). No probs since I installed it.


EDIT. Nope. I didn't get any better really, Wine is a nightmare with version 96 and borders show 50 % improvement but still turn to grey.

---

### Post by wetinwales on 2008-11-10
I have the same problem except that I don't even need to hover the mouse.
Worst cases are in Thunderbird and GIMP but it happens sporadically in all applications.
I run with AMD Athlon XP 2100+ with 1.5Gb Memory and Nvidia GeForce 5900.

It makes no difference how many applications are open.

Also by the way, Cinelerra is a nightmare in IBEX, and Open Movie Editor is no better than it was in Heron (Which basically didn't work)

Is all this a processor issue? Should we be firing up Dual or Triple Cores with mega speed and Graphics cards which orbit the sun?

Daf

---

### Post by feistybee on 2008-11-14
Thanks all for your kind help.

I just disabled visual theme and the title bar problem is not happening now.

---

### Post by SamNSane on 2008-11-14
I think this problem varies in severity from one nVidia card model to another and from one driver version to another. I use several systems running fully configured compiz-fusion setups, and I don't see the problem at all on the systems with Intel video. I saw it on all of the nVidia systems that run proprietary / restricted drivers.

But I did find something that eliminated at least some of the glitches (and particularly the disappearing / corrupting title bar glitch) on the nVidia systems. I switched the window manager from compiz to metacity.

I like to do things the easy (and visual) way when I can. I just installed fusion-icon from Synaptic, then added "fusion-icon --no-start" to the session manager so that I find it in the notification area. (Probably not necessary to do this, but I just like having it handy.) If you right-click the notification area icon there's a selection for choosing window managers.

Once I did this, the title bar disappearing act stopped on my problem nVidia machines.

This could be why installing and selecting emerald works for some folks. Maybe it's just necessary to not let compiz be the window manager.

At least I got to keep my special effects AND my title bars. I just wish nVidia displays would work as well as my Intel displays. They certainly cost me a lot more than the Intels.

---

### Post by feistybee on 2008-11-20
Thanks SamnSane. You did a pretty good analysis.

In my machine compiz is not working. It hangs at starting gtk-window manager.

---

### Post by jml75 on 2008-11-20
Hi all!

I to ahve the same problem. But this is not new with Intrepid. I have two different computers with 7600GTs and I have this exact same problem since 7.10 when I use Nvidia binairy drivers and it is not a metter of window decoration theme. I tried several themes and they all do the same. It does even with emerald so it really is a problem with the nvidia binairy driver.

I hope it will be fixed soon because it is the kind of problem that does not prevent me from working but it just drives me crazy!

Cheers!

---

### Post by tarsius4 on 2008-11-21
It turns out that the "Human" themes cause this problem for me and others.  If you're leery about installing beta drivers or if you'd just prefer to wait for a true solution, you can probably give yourself a temporary fix by changing your theme in System>Preferences>Appearance.

---

### Post by feistybee on 2008-11-21
When I used 'emerald --replace' the command just blinks like

$emerald --replace
__ The cursor is blinking in this line. Thats all.

So I am unable to test with emerald

---

### Post by GH68 on 2008-11-22
I had the same problem, solved by installing the 180.06 NVIDIA driver according to these instructions: [http://www.nvidia.com/object/linux_display_ia32_180.06.html]("http://www.nvidia.com/object/linux_display_ia32_180.06.html")

Good luck!

---

### Post by ryukent on 2008-11-27
180.08 driver is out now. For instructions on installing it (to fix the problem), please see:

[http://ubuntuforums.org/showthread.php?t=993368](http://ubuntuforums.org/showthread.php?t=993368)

---

