---
title: "sleep/screen issues on my lifebook E8210"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Face1 on 2006-06-12
Well, judging from past experiences on my desktop and others' posts, I consider myself lucky that suspend has worked perfectly on my laptop right out of the box.  However, it is coming *out* of suspend that is more iffy.  (by the way, I am using 915resolution and the i810 drivers)

Firstly, when I come out of suspend, the brightness of my screen is waaaaay down.  As in, far lower than you can usually make it.  I can just barely make out the edges of the "enter password" box.  However, all I have to do to is adjust the brightness once to bring it back to normal.  By that, I mean that I can just press the key to turn down brightness one notch, and the brightness returns to normal, or actually one notch less than normal.  I can live with this, but I'd much rather not have to do it every time I take my computer out of suspend.

Secondly, and more importantly, suspend seems to be causing little lines to appear on my display.  When I first start linux, my display is normal--everything looks fine, it scrolls properly, etc.  Even if I suspend the computer and bring it back once, things seem to be in order (I've only tested this once or twice, so it could have been a fluke).  However, when I suspend/restore my computer a second time, I start seeing these lines.  They are two horizontal lines of what appear to be single pixels.  One stretches from the right side of the screen to a bit less than the middle, and is located about 1/4th of the way up from the bottom of the screen.  The other is located about 1/16th of the way up the screen, comes from the left, and is apparently the same length as the other.  The lines do seem to be related to each other.  For example, if I am at my GNOME desktop and click&drag to create a shaded box, and cover part of one line with the box, a corresponding part of the other line will also change to that light orange color.  This is not just in GNOME, however--in KDE I have the same problem, and the lines are visible on the GDM login screen.

Additionally, the lines are especially problematic when I scroll.  For example, in firefox, if I have a long page loaded, and I scroll down it, the lines leave visible, very annoying artifacts.  

My second problem is a much higher priority for me, but I figure that they could possibly be related, which is why I posted both here.  Any help would be greatly appreciated.

---

### Post by Face1 on 2006-06-12
Surprisingly, a screenshot of my screen displays the artifacts that I mentioned.  This could be useful both because I can show what they look like, but also the fact that I am able to do it sheds some light on their nature, probably.

---

### Post by Face1 on 2006-06-15
Okay, well I spoke with a very knowledgeable guy yesterday about this using [qunu]("http://alpha.qunu.com/index.html") (which is an incredibly brilliant site by the way, IMHO), and here is what we came up with.  

My laptop uses the Intel GMA 950 for graphics, which, as you may know, shares memory with the system.  We figured that maybe some of the graphics memory is being overwritten or otherwise corrupted when the computer is suspended.  Unfortunately, neither of us knew any way to avoid the issue.  Anyone have any thoughts on this?

Also, I mentioned in my first post that the issue didn't arise after the first time I suspend.  I was wrong...It takes only one suspend to cause it.

---

