---
title: "Live Cd fails to boot--- video card problem?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Dylius on 2006-10-30
Neither the Edgy 64 or Edgy 32 bit Live CDs will boot on my computer. When I put the CD in, the Ubuntu startup screen comes up, but when I press start (or try any other boot option for that matter)it goes through the loading process normally, and then it gets to the splash screen, the startup sound plays and the window comes up all mangled and choppy. I've tried booting it in graphics safe mode which has no effect, I've tried adding "noapic" to the boot options, and a number of other things, and nothing works. A friend of mine suggested that it might be my video card and said I should try taking it out and then boot it, but I can't take out my only video card, can I? I have nothing to put in in it's place.

Does anyone have any idea of what's going on here?

My system specs are:

AMD Athlon 64 X2 3800+ (socket 939)CPU
Epox 9NPA+ SLI mobo
Seagate Barracuda Ultra ATA 120g hard drive
Evga 7800GT graphics card
2gigs DDR-3200 RAM (1 gig Ultra, 1 gig random company/generic

---

### Post by Sef on 2006-10-31
Have you tried the Live CD in another computer?  It might be the disk, the download, or the burn was bad.

---

### Post by didobuntu on 2006-10-31
+1

I have this problem on my new laptop (Asus W2Jc) too since Egdy Knot 1, and never resolved, altough with a correct CD burning.

This never happens on my older laptop (Asus 3800S) nor on my Desktop (where I installed Edgy too).

"Dylius", you have to reboot with the live CD as many times as necessary. To have an idea, it happens 9 times over 10 on my laptop. It is completetly independent on the options you chose (safe or not safe graphic mode).

Once you get a clean live gnome session, install ubuntu and then this will be only an old souvenir.

P.S. It is difficult to explain this problem since it is impossible to take a screen shot when the window is completeley diagonalized and the pixels randomly merged.

---

### Post by ZDemon on 2006-11-02
I have the same problem too, on my desktop.

i have a AMD 3000++ with Nvidia 6600GT.

I just cant boot the ubuntu Live CD. Is there any solution?

---

### Post by Kira-cjd on 2006-11-02
well it dose  the same on my old computer and it had 512mb ram and a 30gig harddirve runiing 128 vid card dose any 1 kow y it dosent  work email me the answer or post a replay

---

### Post by idjut on 2006-11-02
Had the same problem and solved it by changing the UMA setting in BIOS from 1mb to 8mb. Did a fair share of ](*,) until I got there tho. ;)  Now I have the problem of it reverting to 1 mb every few boots, but thats a different issue..

---

### Post by Dylius on 2006-11-03
I thought it might have been just a bad disk at first, so I burned another and had the same problem. I used the same CD for installing Ubuntu on my dad's laptop, and it worked perfectly. I guess I'll fiddle with it some more until I get it, thanks for the suggestions.

---

### Post by Hitman_Forhire on 2006-11-21
I have the same problem and have seen many similar instances witht the eVGA 7800GT that we both have....I think it is the card. I have successfully used Gentoo and FreeBSD with other drives but Ubuntu will not boot up using any type of graphical interface, I've tried both regular and graphic safe mode. FC6 also does the same thing. I have ubuntu running on all of my other machines and I'm avid about having ubuntu on this machine as well, I've done everything you can think of and nothing. I'd definately love some help with this as well.

-Hitman

---

### Post by Hitman_Forhire on 2006-11-21
Oh yeah, full sys specs:


AMD64 4200+ [ 939 ]
2GB Patriot RAM [DC Kit]
eVGA 7800GT
Epox NF4 Ultra Board
Using IDE HD.

Thx

---

### Post by Hitman_Forhire on 2006-11-21
OK, actually after just a few minutes of poking around here at work, I found this:

[http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)

I'll try this once I get home and hopefully I can get it to work.

-Hitman

---

