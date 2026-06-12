---
title: "Ubuntu: Xserver doesn't start"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by Putinocchio on 2007-02-07
Hi!
That's my first post here and unfortunately it is something really sad...

1. First of all, my laptop is:

MSI M520
[http://www.msi.com.tw/program/products/notebook/nb/pro_nb_detail.php?UID=613](http://www.msi.com.tw/program/products/notebook/nb/pro_nb_detail.php?UID=613)

Specs:
BIOS Version: A1016IMS V1.90 12/02/05
Intel(R) Celeron(R) M processor 1.50GHz
Video Processor : Intel(R) 915GM/GMS,910GML Express Chipset - 128Mb
512+256 RAM
Windows XP

2. Problem
a. When I try to run LiveCD, I see the splash screen, then it takes me back to the black screen with freezed "_", then the CD stops. Only thing I can do - Alt Ctrl Del
b. If I go to the second option (Safe graphical mode), it starts loading with a splash screen. Then goes black screen and continues loading. Then at some moment it crashes bringing me a message about "Xserver could not start (your graphical interface) blah blah blah)"

3. What I did:
a. explored the web for possible solution...

b. sudo dpkg-reconfigure xserver-xorg  --->  Vesa ---> the rest by default. But then I do "startx" and receive a message:
Vesa: no matching modes
Screen(s) found but none have usable configuration

Fatal server error: no screens found
XIO: fatal error 104:( 

c. I tried installing alternative cd, just servers, Fluxbuntu (was hoping maybe it will work)
d. Tried some other drivers apart from Vesa (vga, ati, i810...) - no way!:mad: 

And what really makes me sad is the fact that last 5 days I am exploring web and probably tried already everything possible and still it doesn't work. I don't know what to do...:confused: 

Any help?

P.S.: Today even received my Free ShipIt CDs - still the same...**[B][B][FONT="Arial Black"][/FONT]**[/B][/B]

---

### Post by Brunellus on 2007-02-07
this is being moved to a more relevant forum.

---

### Post by benson444 on 2007-02-07
Just did a bit of searching and came across a few bits and pieces. Apparently your GPU uses the i810 driver so you should choose that when reconfiguring xserver. Also found a couple of references to the boot option acpi=off.

Try the Livecd with acpi=off and using the i810 drivers. Also when choosing resolutions disable all of them except 1024x768.

Other than that I can't help. Good luck, I hope you get it sorted.

---

### Post by shadyzay on 2007-04-13
Ok I have the exact same problem and I don't know what to do with it, I googled it a bit but I found nothing relevant ( except for a bug report [ here ]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/102462") )

I tried reconfiguring xorg but nothing changed, I don't know how to go further with this,
would anybody help?

---

### Post by dacelo on 2007-04-21
I have the exact same problem with my MSI Megabook M520 but sadly nobody can help me with this problem.
So, unfortunately I have to use Windows.

I hope that anyone can help us with this problem... I posted this in an german forum, too,  but there was also nobody who can help me.

---

### Post by shadyzay on 2007-04-22
SUSE 10.2 installed and working fine (With the provided patches from MSI of course ).
I'm gonna test feisty, I'll post the results

---

### Post by dacelo on 2007-04-24
Okay that's a possibility I think but do you also have the Megabook M520 ?

And which updates do you mean? Do you maybe have an link for me?

---

### Post by strabes on 2007-04-24
My xserver wouldn't start on the feisty live CD so I just downloaded the alternate CD and used it to install. It was much faster (since it doesn't have to load the GUI) than dapper, edgy, & the feisty test CDs and it even asked me if I used a proxy to connect to the internet. I think I'll always use the alternate CDs from now on.

---

### Post by dacelo on 2007-04-24
And now the x-server starts, after the install?

---

