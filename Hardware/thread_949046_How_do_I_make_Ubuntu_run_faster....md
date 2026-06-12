---
title: "How do I make Ubuntu run faster...?"
date: 2008-10-15
forum: Hardware
---

### Post by icanfly0307 on 2008-10-15
Hi everyone,
             I'd like to know how to speed up my old laptop which is running Ubuntu 8.04. I've googled around a bit but nothing seems to work. First off, here are my PCs specs:

[B]Sony Vaio PCG FX 370:
   --1 Ghz Pentium 3
   --256 Megabytes of RAM
   --744 Megabytes of Swap
   --32 Megabytes of Video RAM (I DONT use Desktop Effects)
   --100 Mhz Frontside Bus Speed[/B]

Oh, and by the way, I CANT do a memory upgrade because my second memory slot got fried.;)

(Yeah, I know, my computer's REALLY SLOW. But's that why I'm posting this thread. :biggrin: )

Here's how long my PC takes to boot up from a cold start:

**   --From the Grub screen to the Login Screen:** 1 minute 3 seconds
**   --From the Login screen to the Desktop being fully loaded:** 26 seconds

So, does anyone have ANY idea on how to speed up my computer and optimize it's general (and boot time) performance?

I recently updated my computer, (kernel, security updates, bug fixes, stuff like that...), and that seemed to shave off a few seconds of boot time.

Any help or thoughts would be appreciated. :)

---

### Post by forger on 2008-10-15
use xubuntu: [http://www.xubuntu.org/](http://www.xubuntu.org/)
download the cd and do a fresh install

---

### Post by icanfly0307 on 2008-10-15
Hey forger,
    Thanks for your quick reply. I'd like to continue using GNOME no matter what. Are there any types of hacks or tweaks to speed up Ubuntu while still running GNOME?

Thanks

---

### Post by kerry_s on 2008-10-15
> --From the Grub screen to the Login Screen: 1 minute 3 seconds
--From the Login screen to the Desktop being fully loaded: 26 seconds


suspend and hibernate can save you from all that. i'm using a vaio pcg-f430, 450mhz 256mb ram. i'm using debian lenny, with the etch kernel, full gnome install. i hibernate when i'm done for the day, suspend through out the day.

swap the slower programs for faster ones 
turn on metacity reduced resource

---

### Post by forger on 2008-10-15
> **icanfly0307 said:**
> Hey forger,
    Thanks for your quick reply. I'd like to continue using GNOME no matter what. Are there any types of hacks or tweaks to speed up Ubuntu while still running GNOME?

Thanks

xfce is gnome-like, it's based on (or at least uses) GTK.
With such specifications, you will be able to run ubuntu and gnome, but not for long or you won't be able to multiprocess (i.e. firefox and something else) :) On the other hand, if you have a month's time to kill about reading your specifications and removing kernel modules and drivers one by one, which of course, if there's a security linux kernel, will be overwritten :D

Try disabling services at System > Administration > Services.. apart from that, good luck :)

---

### Post by icanfly0307 on 2008-10-15
Hi again,
         How do I tell metacity to use less resources?

Thanks

---

### Post by forger on 2008-10-15
> swap the slower programs for faster ones 
+1 on that! e.g. use epiphany browser instead of mozilla

You could also try increasing your Swap to a 1 Gb ?

---

### Post by icanfly0307 on 2008-10-15
I'm actually trying out something new called Swiftfox. It appears to be WAY WAY WAY WAY WAY faster than plain old Firefox.:)

And also, a quarter of the way through the boot process, my system just seems to hang for a few seconds (maybe like 10 sec.) but then it continues on like nothing happened. When I disabled quiet splash in the boot options, I found out that it hangs at the line:

'Reading files needed to boot'

How do I 'jump' over this and/or make it faster?

---

### Post by Forbees on 2008-10-15
dude, you still boot faster than like any windows machine :-p

i wouldn't worry about it

i'm running dual 3.0ghz 2 gig ram and like 2.5gig of swap

and i'm about  1 min from grub to boot, and ten sec to full desktop (but i so have a bunch of effects on)

i dont think you'll get much faster

---

### Post by forger on 2008-10-15
> **icanfly0307 said:**
> Hi again,
         How do I tell metacity to use less resources?

Thanks

```
gconftool-2 -s /apps/metacity/general/reduced_resources -t bool true
```
log out and log back in

---

### Post by icanfly0307 on 2008-10-15
> **Forbees said:**
> dude, you still boot faster than like any windows machine :-p

i wouldn't worry about it

i'm running dual 3.0ghz 2 gig ram and like 2.5gig of swap

and i'm about  1 min from grub to boot, and ten sec to full desktop (but i so have a bunch of effects on)

i dont think you'll get much faster

Thanks a lot. That makes me feel so much better.:) Maybe I'll find something to tweak and still be able to boot up faster. :guitar:

---

### Post by kerry_s on 2008-10-15
> **icanfly0307 said:**
> Hi again,
         How do I tell metacity to use less resources?

Thanks

system tools> configuration editor, click edit> find, type: reduced, check both boxes, it will give you a list.see pics

also while your in there find "animations" uncheck them all.

---

### Post by icanfly0307 on 2008-10-15
> **forger said:**
> ```
gconftool-2 -s /apps/metacity/general/reduced_resources -t bool true
```
log out and log back in

I tried that and the console just returned me back to the prompt (REAL FAST). I was just wondering. How much of a performance boost will I be able to see with this tweak?

EDIT: Oh yeah. I forgot to log out and log in again. I'll be doing that now.](*,)

EDIT AGAIN: Yup, there's a LOT of significant improvement. Thanks a lot!!!

---

### Post by naveencool on 2008-10-15
hello everybody .....
i m a new user to linux ....
i just wanted to know about how to install ubuntu linux on my system????
i hav a live cd but whenever i try to install from it then after selecting the state kolkata (from world map) it shows a box with a heading partition manager but in that box there is no option activated through which i can create partition for linux....
is there a way out to solve it ?????
plz reply 
thanx in advance......

---

### Post by Samalama on 2008-10-15
> **Forbees said:**
> dude, you still boot faster than like any windows machine :-p

Well I don't know what version of Windows you've been using, but there's no question Windows XP boots quicker than Ubuntu(or its derivatives). The problem with Windows is that it easily accumulates "random crap", which in turn slows down the computer. Don't get me wrong though, I'm not a big fan of Windows, but there's no need to make Windows sound like a slow P.O.S.(even if it IS a P.O.S.;))

---

### Post by kerry_s on 2008-10-15
you already disabled aiglx and composite?

gksudo gedit /etc/X11/xorg.conf

```
Section "ServerFlags"
Option  "AIGLX" "off"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection
```

i also replaced:

gedit -> leafpad
gimp -> gpaint
evince -> epdfview
ooo writer -> abiword
gnome-terminal -> roxterm
firefox -> epiphany

---

### Post by brdokoky on 2008-10-20
> **icanfly0307 said:**
> Hi everyone,
             I'd like to know how to speed up my old laptop which is running Ubuntu 8.04. I've googled around a bit but nothing seems to work. First off, here are my PCs specs:

[B]Sony Vaio PCG FX 370:
   --1 Ghz Pentium 3
   --256 Megabytes of RAM
   --744 Megabytes of Swap
   --32 Megabytes of Video RAM (I DONT use Desktop Effects)
   --100 Mhz Frontside Bus Speed[/B]

Oh, and by the way, I CANT do a memory upgrade because my second memory slot got fried.;)

(Yeah, I know, my computer's REALLY SLOW. But's that why I'm posting this thread. :biggrin: )

Here's how long my PC takes to boot up from a cold start:

**   --From the Grub screen to the Login Screen:** 1 minute 3 seconds
**   --From the Login screen to the Desktop being fully loaded:** 26 seconds

So, does anyone have ANY idea on how to speed up my computer and optimize it's general (and boot time) performance?

I recently updated my computer, (kernel, security updates, bug fixes, stuff like that...), and that seemed to shave off a few seconds of boot time.

Any help or thoughts would be appreciated. :)


Try to use reiserfs or xfs. It could help to you.

---

### Post by Tomatz on 2008-10-20
> **brdokoky said:**
> Try to use reiserfs or xfs. It could help to you.


NO

Use ext3 ;)

This should help:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by icanfly0307 on 2008-10-20
I AM using ext3 as my filesystem. :)

---

### Post by kerry_s on 2008-10-20
i'm using ext2 on mine, it's a lot faster on the old stuff and doesn't get corrupted from suspend and hibernate.
i'm using a old vaio pcg-f430 laptop 450mhz 256mb ram running a custom debian etch install, built from the base up with only what i use.

---

### Post by snowpine on 2008-10-20
> **kerry_s said:**
> i'm using ext2 on mine, it's a lot faster on the old stuff and doesn't get corrupted from suspend and hibernate.
i'm using a old vaio pcg-f430 laptop 450mhz 256mb ram running a custom debian etch install, built from the base up with only what i use.

+1 I spent some time this weekend testing Debian Etch on my old 500mhz pentium 3 laptop. It really is nice for the old hardware! (even using gnome desktop)

---

### Post by kerry_s on 2008-10-20
> **snowpine said:**
> +1 I spent some time this weekend testing Debian Etch on my old 500mhz pentium 3 laptop. It really is nice for the old hardware! (even using gnome desktop)

yeah it surprised me to, i thought gnome would be slow, but it was working damn good and better with a little tweaking.
i missed real performance though, the kind you can only get if you do it yourself, everything opens instantly, except firefox there's no hope there, :lolflag: but for everything else the difference is huge.
you just can't beat a light wm with light programs.

---

### Post by snowpine on 2008-10-20
Debian Lenny + LXDE was kind of nice too, tried that for a couple of days.

---

### Post by kerry_s on 2008-10-20
> **snowpine said:**
> Debian Lenny + LXDE was kind of nice too, tried that for a couple of days.

lenny was slower to me, that's why i dropped back down to etch.
also debian dropped my sound card firmware from 2.6.23 kernel on, so i have to compile the firmware myself or use the etch kernel, otherwise no sound. :(

i prefer jwm for the window manager, i've just gotten so use to it, anything else is just to much work. :lolflag:

---

