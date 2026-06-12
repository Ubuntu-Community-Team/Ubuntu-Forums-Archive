---
title: "What happened to 'displayconfig-gtk"
date: 2008-10-31
forum: General Help
---

### Post by DougieFresh4U on 2008-10-31
Acouple of weeks ago I was able to type
sudo displayconfig-gtk
into terminal and a window would pop up where I could set/change screen resolution and graphics drivers. All I am getting from terminal now is:
[B]dougie@DougiesLeanMachine:~$ sudo displayconfig-gtk
sudo: displayconfig-gtk: command not found
dougie@DougiesLeanMachine:~$[/B]
Did I miss something?

---

### Post by overdrank on 2008-10-31
> **DougieFresh4U said:**
> Acouple of weeks ago I was able to type
sudo displayconfig-gtk
into terminal and a window would pop up where I could set/change screen resolution and graphics drivers. All I am getting from terminal now is:
[B]dougie@DougiesLeanMachine:~$ sudo displayconfig-gtk
sudo: displayconfig-gtk: command not found
dougie@DougiesLeanMachine:~$[/B]
Did I miss something?

Hi and if you are using intrepid, yes it was removed.

---

### Post by somersetsimon on 2008-11-01
> **overdrank said:**
> Hi and if you are using intrepid, yes it was removed.

So how are we supposed to manage our graphics cards and screen resolution now? I can't get out of my 800x600 resolution now I've installed Intrepid and I can't find any utility that even mentions my graphics card.

---

### Post by steveydoteu on 2008-11-01
System > Preferences > Screen Resolution could be a good place to look.

---

### Post by thasban on 2008-11-01
thing is, i tried typing sudo displayconfig-gtk in the terminal but it worked for me, and i'm using intrepid.

---

### Post by victor220 on 2008-11-01
Professional golf gives you the opportunity to play a game you love, to earn big money doing it, and to possibly write your name in the pages of golfing history.  

As a professional golfer your place of business will be the golf course and the practice range. You won't be stuck behind a desk or in an office cubicle, and your job description - well, you get to write that yourself.  
You will share the game with other players who love it as well. As you travel from tournament to tournament, your competitors will become your friends. Together you will see the world and share a game with a legendary heritage

So choosing a club which is fit you is very important. I suggest you could have a look at the [www.golforderonline.com:lolflag:](www.golforderonline.com:lolflag:)

---

### Post by malcuy on 2008-11-01
> **steveydoteu said:**
> System > Preferences > Screen Resolution could be a good place to look.

Yep. It would be a good place to look.
It'd also be a great place for there to be something to find.
I moved from 8.04 to 8.10 to see if it helped with the SiS graphics problem, but it looks like I now have less working then I did. 600x800 just kills this for me.

---

### Post by Jim Danner on 2008-11-01
Maybe you need to make it visible with the Menu editor (System... Preferences... Main menu)

---

### Post by steveydoteu on 2008-11-01
> **malcuy said:**
> Yep. It would be a good place to look.
It'd also be a great place for there to be something to find.
I moved from 8.04 to 8.10 to see if it helped with the SiS graphics problem, but it looks like I now have less working then I did. 600x800 just kills this for me.

It allows you to change your screen resolution, which if I am not mistaken, is one of your original points?

---

### Post by malcuy on 2008-11-02
It allows me to change my screen resolution to a resolution that it believes my screen can handle. Without being able to tell it explicitly what hardware it's dealing with, it's defaulting to 600x800 or 640x480 as my only options.  I understand that the new version of xorg almost entirely does away with the need to tell it what hardware you have, so there is almost no need for displayconfig-gtk, but there appears to be a need for it or something similar. 
In this area this release of ubuntu has less functionality then the last for me and others with less supported graphics hardware.

---

### Post by fronten on 2008-11-08
i second that need!

obviously some LCDs are not detected properly so there MUST be a way to tell the driver exactly how to drive the monitor. (and test it before using it as default setting[!!!])

with xorg.conf gone and displayconfig-gtk gone what stays?
:confused::(:confused::confused::confused::confused:

---

### Post by lunchbox330 on 2008-11-08
Ok, so 8.04 gets rid of dpkg-reconfigure xserver-xorg, and 8.10 gets rid of displayconfig-gtk, so if our graphics cards and monitors are not detected properly by the new X autoconfig in 8.10, how are us commoners supposed to reconfigure our Xorg without writing it by hand? Removing functionality from Ubuntu makes no sense to me, as X really isn't as bulletproof as the developers would like it to be.

Give us our old tools back!

---

### Post by karlmp on 2008-11-08
they can't hear you


[SIZE="7"]**GIVE US OUR OLD TOOLS BACK! **[/SIZE]

---

### Post by soro2005 on 2008-11-08
I can still do dpkg-reconfigure xserver-xorg.

---

### Post by snakyjake on 2008-11-08
I switched to OpenSUSE, and now my resolution works perfectly.  I don't know how anyone else feels, but it's this kind of @%^% that made me dislike Windows.  I don't want to have my computer not work or work poorly after an upgrade....that's what Microsoft does.

So I'm looking at OpenSUSE before I look at Apple, or even Windows again.

---

### Post by soro2005 on 2008-11-08
It can't be said often enough: If you need stability, wait at least two months after release before you upgrade to a new distribution. There are always bugs and inconsistencies, and it's virtually impossible to catch them all before "the masses" (we) try it out on their computers.

The Mac will be a good choice if breakage is a no-no for you. They control what hardware their OS is allowed to run on, so they are able to make sure that everything works on the five models they offer.

---

### Post by feistybird on 2008-11-11
> **karlmp said:**
> they can't hear you


[SIZE="7"]**GIVE US OUR OLD TOOLS BACK! **[/SIZE]


Please vote here:

[http://brainstorm.ubuntu.com/idea/7655/](http://brainstorm.ubuntu.com/idea/7655/)

---

### Post by Rob-e on 2008-11-12
ahhhhhhhhhh, i cant change the resolution!!!!!!!!!!  its stuck at 640x480, it didnt detect the monitor, "o, ill just edit xorg.conf... theres nothing here to edit!?" ********  "o, ill use displayconfig-gtk" *double *******  "i will just install it... ITS NOT THERE" *triple *******

wtf ubuntu, what am i supposed to do, this isnt making anything easier, its ******* us all, what am i supposed to do?????????????





/rant

---

### Post by bodhi.zazen on 2008-11-12
I agree 1000 %

I am a recovering command line junkie and I do not mind GUI tools.

BUT, if they fail we need command line options.

sudo dpkg-reconfigure xserver-xorg and manually editing xorg.conf (and other config files) no longer works.

This leaves us stuck if the gui tools fail, just like Windows.

The more things change, the more they stay the same.

---

### Post by Rob-e on 2008-11-13
yeah, that actually happend today, i was mad, hence the rant, but yeah

---

### Post by mickbuntu on 2008-11-22
Out of range error on my display on one of the Live Cd's. That tool helped from another terminal.  Now no tool in place, nor  possible to configure easily any other way. Speechless really!   

No way to get to that gui tool since i can't even start "X'

---

### Post by fantasyl on 2009-01-19
+1 for the request too, any news on the matter?

I cannot change refresh rate anymore, upgrading from 8.04 to 8.10, so I'm stuck with 60hz. 

This makes any 24fps and 25fps video unbearable to watch :(, with stutters all over the place.......

sudo dpkg-reconfigure xserver-xorg and manually editing xorg.conf (and other config files) no longer works for me, too......

---

### Post by AggravatedGestalt on 2010-09-09
I actually, really, REALLY believe they don't care. I think Ubuntu/Canonical has been infested by diseased humans. (I wonder if the newest distro will be named Cyber-Command)

"Just go to 'squeak' System 'squeak' Preferences 'squeak' Monitors 'squeak'". ......Sickening. 

I too will shout: GIVE US BACK OUR TOOLS! And stuff your smarmy replies.

---

### Post by bodhi.zazen on 2010-09-09
> **AggravatedGestalt said:**
> I actually, really, REALLY believe they don't care. I think Ubuntu/Canonical has been infested by diseased humans. (I wonder if the newest distro will be named Cyber-Command)

"Just go to 'squeak' System 'squeak' Preferences 'squeak' Monitors 'squeak'". ......Sickening. 

I too will shout: GIVE US BACK OUR TOOLS! And stuff your smarmy replies.

And with that time to close this thread. The OP is almost 2 years old and "displayconfig-gtk" has, to the best of my knowledge, long been dropped and, again to the best of my knowledge, was never maintained by the Ubuntu dev, talk to the xorg developers or the displayconfig-gtk crew. displayconfig-gtk was last updated in 2008 and does not appear to be maintained.

Perhaps you would be willing to volunteer to maintain the code and adapt to the new xorg ?

If you do not like Ubuntu, that is your choice, use an alternate OS, Linux / BSD or otherwise.

---

