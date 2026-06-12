---
title: "Newbie on Compaq Presario V2000"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by Lord_Aragorn on 2006-01-14
Hello all out there in Linux land,

Am pretty new to this so bear with me.

Have just purchased a Compaq Presario V2000 laptop PC, specs :
AMD Sempron, 256MB RAM, 40GB HDD, ATI Raedon Express 200M Video Card.
Have just installed Ubuntu 5.1 (Breezy Badger) and upon booting up receive message "Failed to start X Server...." and end up in text only mode.
To make matters worse have no access to root at all, so could some kind sould out there please off any suggestions on a workaround, would dearly love to use it. Was able to install on desktop PC fine, must be sone crumby VGA card on laptop..

Much obliged and we all love you Bill..

---

### Post by Greg2 on 2006-01-14
[QUOTE=Lord_Aragorn]
Have just purchased a Compaq Presario V2000 laptop PC, specs :
AMD Sempron, 256MB RAM, 40GB HDD, ATI Raedon Express 200M Video Card.
Have just installed Ubuntu 5.1 (Breezy Badger) and upon booting up receive message "Failed to start X Server...." and end up in text only mode.[/QUOTE]
Reading this post and the links attached to it should solve most of your problems:
[http://ubuntuforums.org/showthread.php?t=112681](http://ubuntuforums.org/showthread.php?t=112681)

The hardware is &#8216;almost&#8217; identical.

---

### Post by shawnmcdonald on 2006-01-27
Hi Greg,
You should read the thread at:
[http://ubuntuforums.org/archive/index.php/t-84082.html](http://ubuntuforums.org/archive/index.php/t-84082.html)

I have my v2000 running GREAT, and have documented the problems I encountered as well as the solutions.
Hope this helps,
Shawn

---

### Post by Skye on 2006-01-28
Hey-

I've got my v2000 up and running using the methods in the aforementioned thread (unfortunately, I had to find all the individual steps out for myself, because I didn't know that thread existed until just now.)

I also used the Suspend2 how-to, (located at [http://www.ubuntuforums.org/showthread.php?t=75443](http://www.ubuntuforums.org/showthread.php?t=75443)) which is an excellent guide to getting software suspend to work.

Good Luck!

---

### Post by Greg2 on 2006-01-28
[QUOTE=shawnmcdonald]Hi Greg,
You should read the thread at:
[http://ubuntuforums.org/archive/index.php/t-84082.html](http://ubuntuforums.org/archive/index.php/t-84082.html)

I have my v2000 running GREAT[/QUOTE]
Thanks Shawn, I have archived that with my other laptop notes.

You may have misread my post; I have my ze2308wm running great also. I was linking my documentation for Lord_Aragorn to use... but now he has yours setting up the v2000.:)

---

### Post by Lord_Aragorn on 2006-02-03
Many thanks to you all, working like a charm now.

God bless.

Regards

Dennis

---

### Post by USA1 on 2006-02-14
[QUOTE=shawnmcdonald]Hi Greg,
You should read the thread at:
[http://ubuntuforums.org/archive/index.php/t-84082.html](http://ubuntuforums.org/archive/index.php/t-84082.html)

I have my v2000 running GREAT, and have documented the problems I encountered as well as the solutions.
Hope this helps,
Shawn[/QUOTE]
ATI installation

Thank you so much for this link:

[http://ubuntuforums.org/archive/index.php/t-84082.html](http://ubuntuforums.org/archive/index.php/t-84082.html)

Most of the help notations here leaned to the How-to post which is a bit scarry.  I am a new bee and not so much into deletining stuff, downloading and installing new stuff...

The link I pasted above provides a very easy fix to get your xwindow working without having to install anything.

Basically the ATI Radeon 200M video card is installed by default with the ubuntu installation.  It just need an extra option on the configuration to get it to work properly.  Add the Option="noacel" to the *.conf file and that fix it all. reload the xwindows system and you will have it full resolution and sharp.

Maybe am just lazy or a scarry cat, but I always preffer the path of least resistance and the above worked my way....

good lock.

---

