---
title: "T41 broken resume following upgrade to Feisty"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by mylesorme on 2007-04-29
Hi there. On upgrading a thinkpad T41 from Edgy to Fiesty resuming from suspend doesn't work.It will suspend but it hangs on a blank screen on resume. I don't tend to use hibernate. The same happened from Dapper to Edgy. That one was resolved by stopping powernowd and starting it again after resume. Not so this time. I've been keeping an eye open since I know lots of others had the same problem, but not found anything to suggest a solution. can anyone point me in the right direction please? Thanks

---

### Post by tanguyr on 2007-04-30
Hello,

Just off the top of my head: you wouldn't happen to be using an ATI card with the fglrx driver from the ubuntu repository by any chance? I've got the same problem you describe and i suspect it has to do with the fglrx i installed for feisty.

/t

---

### Post by mylesorme on 2007-05-01
I do have an ATI card - a Radeon Mobility 7500 - but not the fglrx driver which I found problematic - I did try installing it following a post I found somewhere but it knocked out Beryl and the experimental desktop effects. I've gone back to the xserver-xorg-video-ati driver. The resume problems occur with or without these effects and Beryl incidentally.

---

### Post by mylesorme on 2007-06-04
Solved by latest kernel update. Although I now have another problem - now it resumes but hangs if I try to launch an application...

---

### Post by veebis on 2007-08-04
T41, ATI FireGL 9000 @ 1400x1050.
Everything perfect, except on resume from suspend, black screen. Disk activity, bluetooth/etc. light up, but no backlight. All the latest updates, tried everything I can find, including kernel update (gutsy -- that hosed, had to revert)... :confused:

Any advice would be MUCH appreciated!
Thanks,
-Vb

---

