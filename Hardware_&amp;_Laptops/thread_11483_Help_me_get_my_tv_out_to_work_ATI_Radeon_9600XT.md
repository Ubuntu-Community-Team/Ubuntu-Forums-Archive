---
title: "Help me get my tv out to work ATI Radeon 9600XT"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by Nolgthorn on 2005-01-17
Hello I am using Gnome 2.8.1 with Warty Warthog Ubuntu.

I have a small television set on my desk I would like it to view media with while I code, except I cannot for the life of me figure out how this is done.

The tv does show an image while it's plugged into the s- video slot on my card. Though when Ubuntu boots it comes up only as a scrambled mess on the screen. I plan to use totem and Xine to view said media.

Please help, thank you.

---

### Post by poofyhairguy on 2005-01-17
[QUOTE=Nolgthorn]Hello I am using Gnome 2.8.1 with Warty Warthog Ubuntu.

I have a small television set on my desk I would like it to view media with while I code, except I cannot for the life of me figure out how this is done.

The tv does show an image while it's plugged into the s- video slot on my card. Though when Ubuntu boots it comes up only as a scrambled mess on the screen. I plan to use totem and Xine to view said media.

Please help, thank you.[/QUOTE]

What kind of video card do you have. If you have a NVidia card, use their drivers from their website. It supports tv out. 

If you have an ati card use well, this?

[http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/](http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/)

say what card it is and I can help more.

---

### Post by Nolgthorn on 2005-01-17
Well I tried using the utility "atitvout" with my ATI radeon 9600XT, I can modify it's display slightly but I still cannot get any clear picture. The screen just looks like fat lines all the way across.

Thank you again for any further help you can provide for me.

---

### Post by artnay on 2005-01-17
It sounds you're running monitor 1 (in this case, tv) with too high resolution. The picture is messy, but you still can see that the display adapter is sending signal to tv. You should have told what kind of tv you have. Old-fashioned CRT or brand new HDTV?

I'm using 2 and 3 as frequency options (in fglrxconfig) to tv, I have huge CRT Sony 32FQ70. The resolution isn't great, but there's no HDTV yet in this country, so no need to renew the television yet.  8-[ Of course it would be nice to use TV as a secondary monitor with good resolution.

Be patient and wait for new drivers from Ati. They should be released today. *yay*

Actually the new driver set IS OUT! Go get it! Is it already avaible via apt-get? Dunno, I think I compile it by myself.

---

### Post by Nolgthorn on 2005-01-18
Well I broke it. I installed the new drivers it does indeed seem as if there is TV out support on a seaporate desktop I ran the configuration program and I must have set up something incorrectly.

When I reset the computer I get a dark screen on my desktop, and the television is just black. I cannot even login, I tried and still nothing happened. I believe my entire system is compromised.

Well it was my mistake, is there anything anyone can suggest in order to fix this. When I tried to login using the repair kernel on startup, it requested my root administration password but continued saying login was failed. I have no idea what is wrong there, please help? :-#

---

### Post by Nolgthorn on 2005-01-19
I'll reinstall tomorrow.

---

### Post by richbayliss on 2005-01-19
Dude, let us know how the new ATi drivers work out.

Im currently running Warty on a standalone server, but am tempted to move over from XP on my main machine.

If i can get my drivers running dual-head monitor and play some UT2004 and CoD, im moving

Radeon 9800pro btw  :mrgreen: 

Anyway, await the post.

---

### Post by daniels on 2005-01-19
Mmm, TV out on r2xx and above is kind of hairy.  It's in the open-source BeOS driver, and I have the register docs here to do it on r2xx/r3xx, but a) I don't have time, b) seemingly, neither does anyone else.  Ideally, t should just work with the standard drivers, though.

---

### Post by Nolgthorn on 2005-01-20
I'm sorry I have not been able to get tv out to function the way I want it to with new drivers. It does mirror my desktop but this doesn't help me because I would rather a seaporate desktop to view media with first of all, secondly the resolution of my desktop is too high for my tv to view anything other than colorful wavy lines on it.

I have looked everywhere for a decent walkthrough of the text based ati driver config but to no avail. I'd rather not venture this on my own because of what happened the last time and I had to start from scratch.

Is there any news about when a graphical ui for this driver will be available like the "catalyst control center" Windows has? Or any external links to websites how I would set this up so there is less chance of an error on my part again.

---

### Post by vettejock99 on 2005-01-21
You say with the new drivers you have gotten it to clone?  Would you mind posting your xorg.conf and or any other applicable files?  I am using a similar setup and my TV screen is black, though my LCD on the analog connector is just fine.

---

### Post by Nolgthorn on 2005-01-27
Sorry vette, it does this for me with the default settings.

---

