---
title: "are the ATI Mobility supported?"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by koda on 2006-05-05
Hello people!

this is my very first post on this forum, even if i already found very precious information!
I think that this is a very nice forum as people always try to help! I hope that they'll help me out as well ;) 
Ubuntu is my first Linux experience and quite a positive one, since i'm getting my friend to try it as well! i do like the "linux world" despite i have very little experience on it!

Anyway, let's get to the subject! I have an ATI RADEON Mobility M6 on my Sony Vaio [(link to the specifications)]("http://www.vaio-link.com/specifications/specifications.asp?l=it&category=-1&serie=-1&m=457") and i tried lots and lots and lots and (did I say lots?) of wikis, Howto etc. but i just couldn't make it work!
At this time i have a doubt: is my graphic card supported by fglrx?
the Xorg log says "device not found"
Actually i'm not really interested in 3d acceleration but i do need the option to switch off the laptop monitor and keep turned on the external one! If my card is unsupported, is there an equivalent program for this feature?
Is it possible that since i have problems with my graphic card, my only way to play videos is natively (with mplayer only?) while even if installed the w32codecs I just see a blue screen on totem or any other player???

my questions are far from finished but i think that these ones are enough... for now ;) 
thanks a lot for the help
Bye!

---

### Post by richbarna on 2006-05-05
have you tried changing the xorg config file to use the vesa driver instead of ati ?

---

### Post by Mr Fat Bat on 2006-05-17
I had a whole mess of problems getting my laptop to run fglrx but amazingly after I installed on Dapper and reinstalled the fglrx drivers (and changed my xorg.conf from "vesa" to "fglrx") it all worked.

Let us know after (of if) you upgrade if it works ;)

---

