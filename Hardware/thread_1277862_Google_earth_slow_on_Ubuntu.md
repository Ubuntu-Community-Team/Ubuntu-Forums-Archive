---
title: "Google earth slow on Ubuntu"
date: 2009-09-28
forum: Hardware
---

### Post by snakeman21 on 2009-09-28
Hi all.  I've always been a fan of Google Earth, it's a fun program.  But I've run it on lots of different computers, all with Ubuntu.  I have in on my own laptop, as well.  But today I was on a Windows computer, and it had Google Earth, so I played around with it to kill time.  

Google earth has always run pretty rough for me;  Movement is jerky, and the graphics aren't handled well.  I have 1GB of RAM on my computer.  A couple weeks ago, I used Google Earth on a friend's computer.  He was running Ubuntu 9.04 with 3GB of RAM.  Google Earth ran the same on his computer.

But this Windows computer is old, with a crappy processor and only 512MB of RAM, running a VERY bloated Windows XP.  And Google Earth runs great!  Animations are all smooth, 3D buildings load up in a snap, and the picture is very crisp.

Why is this?  My experience has shown me that Linux is capable of better performance than Windows, even with fewer resources.  So why does it hate Google Earth?

---

### Post by earthpigg on 2009-09-28
got compiz running? desktop effects set to anything other than 'none' means compiz is on.

on the windows computer, run a 3d video game and google earth at the same time... that is very much the same as running compiz and google earth at the same time :D

---

### Post by tuxxy on 2009-09-28
Also your graphics card could play a part in the problem, specifically if you have an ATI card as the drivers are poor.

---

### Post by snakeman21 on 2009-09-28
Would compiz cause it to run slow?  I always use compiz, I'm kind of an eye candy junkie...

---

### Post by earthpigg on 2009-09-28
> **snakeman21 said:**
> Would compiz cause it to run slow?  I always use compiz, I'm kind of an eye candy junkie...

yes... the video game + google earth in windows analogy was supposed to convey that compiz essentially turns your desktop into a 3d video game, and google earth is also essentially a 3d video game. 

expect performance to degrade when trying to play 2 3d video games at the same time. everything has it's price.

this is what i myself do...

quick way to disable compiz with Ubuntu/GNOME (default):
alt+f2 and enter "metacity --replace"

quick way to re-enable compiz:
alt+f2 and enter "compiz --replace"

or, if you like pointy-clicky solutions...

install the "fusion-icon" package. it puts a little icon in your system tray that does nothing but enable/disable compiz.

---

### Post by snakeman21 on 2009-09-28
> **earthpigg said:**
> yes... the video game + google earth in windows analogy was supposed to convey that compiz essentially turns your desktop into a 3d video game, and google earth is also essentially a 3d video game. 

expect performance to degrade when trying to play 2 3d video games at the same time. everything has it's price.

this is what i myself do...

quick way to disable compiz with Ubuntu/GNOME (default):
alt+f2 and enter "metacity --replace"

quick way to re-enable compiz:
alt+f2 and enter "compiz --replace"

or, if you like pointy-clicky solutions...

install the "fusion-icon" package. it puts a little icon in your system tray that does nothing but enable/disable compiz.

Sounds great!  I'll give it a shot tomorrow--I've a few too many drinks tonight.  I much prefer CLI just because I'm used to it, so I'll use that method.  I'll let you know if disabling compiz makes a difference once I try it.  

Thanks so much!  I absolutely love the open source community... One of the best things I've discovered!  The help here is SO much better than paid support.  I love helping out here, and I love how willing everyone else is to help me.  Keep it up, guys!

---

### Post by snakeman21 on 2009-09-29
Nope, that made no difference.  Google Earth runs like crap whether I use Compiz or Metacity.  Any other suggestions?

I have 1GB of RAM, an Intel Centrino Duo processor, and my graphics card is an Intel Mobile 945GM/GMS, 943/940GML Express

---

### Post by mick55 on 2009-09-29
Hi snakeman21

I agree with you, Google Earth is a great program.
When i use street view to look at my home town, it's
like taking a mini vacation there.

Did you install Google earth through synaptic package manager
or did you download the bin file from google?

In Jaunty 9.04 the version through synaptic has issues.
One of the issues is  street view does not work.

I use a dual boot Ubuntu/Winxp system and use google
earth in both.It looks better and runs faster in Ubuntu.
Also runs full speed on my laptop running Linux Mint 7.
I use the version available at googles site.

I really hope you get it working, it's such a cool program.
I use an nvidia 8500gt video card.

Cheers
Mick

---

### Post by snakeman21 on 2009-09-29
I downloaded the .bin from the Google Earth web page.  To be honest I didn't know it was available in the repos.

---

### Post by mick55 on 2009-09-29
Hi snakeman21

In windows Google Earth runs like a champ if OpenGL and
3d acceleration are enabled.If  the video card doesn't
support those features GE uses directx to simulate them,
and performance is degraded.
In Ubuntu you will experience a similar degraded performance 
if your video card doesn't support 3d acceleration.
Your video card may be your issue here.

Good luck
Mick

---

### Post by Endolith on 2009-10-29
My video card supports 3D acceleration and Google Earth is still intolerably slow.  It used to work when I first started using Ubuntu, but in the latest releases it's broken (sound familiar?)  The graphics drivers are enabled (Nvidia 173), and I'm using the version from Medibuntu.  GL screensavers work fine.

---

### Post by mick55 on 2009-10-29
Hi Endolith

The version from Medibuntu is indeed broken.
Remove it through synaptic package manager and
install the version from the Google Earth site.

That is why i originally questioned which version the OP had 
installed.He had installed the bin from the Google Earth site
and still had problems, that was why we were discussing
video cards.
You have a different issue.I had the same one when i installed
from the repositories.

I hope you can fix your problem.

peace
mick

---

### Post by Endolith on 2009-10-29
That version does work a lot better.  Thanks.  How long has the Medibuntu version been broken?  More than a year?

---

### Post by mick55 on 2009-10-30
Hi Endolith

I'm not sure exactly how long it's been messed up for.
I think since Jaunty was released, although i could be wrong.

I'm glad it worked for you.
I initially noticed problems with street view which is why
i originally switched to the one from Google Earth's site.

Glad i could help.

peace
mick

---

