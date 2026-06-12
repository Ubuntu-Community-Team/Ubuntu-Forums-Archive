---
title: "Ubuntu doesn't work with my computer."
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by mp3_freak_721 on 2007-04-24
I have a Dell Dimension E521 and I cannot get Ubuntu to work on it. I cannot boot from the Live CD and I really want to install Ubuntu but first I have to run it from the cd of course. If this helps my pc has an AMD Athlon 64 2.0 GHz with 512 mb of ram, one 80 gb hard drive, and one 40 gb hard drive that is Ultra ATA. It is making me really mad that I cannot boot into Linux. :confused: :mad: ](*,)

---

### Post by dyous87 on 2007-04-24
Some more information would help. Which version of the Ubuntu cd were you trying. IE: x86 or 64bit. Also have you tried the alternative cd because sometimes when the live cd doesn't boot the alternative one will still install. What exactly happens when you tried booting into the live cd anyhow?

---

### Post by sjnovick on 2007-04-24
Did you try the alternative CD ?

Maybe the Live CD doesn't work for you due to some video driver (or other) issue.  You can install Ubuntu via the alternative CD though and still give it a try.

---

### Post by jml on 2007-04-24
A few more suggestions.  Where did you get the CD?  If the iso image of Ubuntu was burned to a CD-R disc, its possible that the disc is defective.  Will your disc boot on any other computer?  If not, then download and burn another disc at a slower write speed.  That may make the disc more readable.

Also, what do you mean by won't run.  Do you mean the disc begins the install process and then fails, or do you mean that when you boot your computer with the CD in the drive, it boots to the built in operating system?  If its the second case, then you should go into your computer's bios during boot up and make sure your computer is set to boot from your optical drive before the internal hard drive.  Hope this helps.

Joe

---

### Post by mp3_freak_721 on 2007-04-25
I think I am using x86 I might want to try the 64bit now that you mention it. It won't boot off the live cd. This is to clarify.

---

### Post by dyous87 on 2007-04-25
it should work fine with x86, that shouldnt be the problem. can you be more specific as to exactly what happens when you try booting it. ie does the screen just go blank, does it freeze??

---

### Post by strabes on 2007-04-25
I had the same problem. It's something about the ATI cards. You have two options:

1) Once the gui fails to load on the live CD, hit CTRL+ALT+F1, run these commands:
```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
startx
```

2) Download the alternate CD and install from it.

I chose the latter.

---

### Post by dyous87 on 2007-04-25
Hmm I don't know if that's it.  It could be but the reason I'm not so sure is because I have an ATI card and I haven't had to do those steps since dapper. Usually ubuntu will just pick the vesa drivers which should still allow the gui to load, then you can install the fglrx ones latter. It is worth a try though I could be mistaken.

---

