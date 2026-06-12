---
title: "Come Here If You Cant Get The Xserver To Work"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by arckeda on 2006-02-11
(Sticky this so so many people can stop having to ask about 5000 times before someone who knows answers their questions like I had to.)

This is if when using live cd or just plain ubuntu and the xserver failed to load.

Now im gona help you.

[Random silly censored profanity removed by moderator.] -zenwhen

Start booting on live cd or just ubunu then after its all done loading you will get an xserver faild to start bla bla bla error.  It will ask you if you want to view logs select no and you get a black screen hold: ctrl-alt-F1 and you get bash.

Once at the bash by holding ctrl-alt-F1 type:

sudo dpkg-reconfigure xserver-xorg 

and select vesa as driver, or vega if that doesnt work (I assume that orginally it  selected ATI, if vesa or vega dont work try ATI) then you go through some steps, fill them all out, if you have no idea what to do for keyboard, press enter, and keep pressing, it should all be defualt unless you have some weird keyboard or moniter needs.  After your done type:

startx

and you will start the xserver

then you should be in ubuntu.

[Random silly censored profanity removed by moderator.] -zenwhen

---

### Post by hen3rz on 2006-02-12
Thank you veyr much. I just had this problem and did a simple search and your post turned up. I shall try this when i get home. Thanks heaps.

---

### Post by closeyourwindows on 2006-02-13
thanks for your help.  this worked like a champ.
I shut down my laptop like I always do and when I brought it back up, I had no sessions and startx did not do anything.  I was searching the forums before I used knoppix to back it all up when *voilla*, a great post.  thanks for the tech tip.  there was a little bit of configuring that had to be done, but all is well.  :-D

---

### Post by TheDude on 2006-02-15
Can we get some sticky action? :D

---

### Post by aysiu on 2006-02-15
[QUOTE=TheDude]Can we get some sticky action? :D[/QUOTE] Perhaps, instead, a real HowTo like [this one](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) can be posted in the Tips and Tricks section of the forums.

---

### Post by xero on 2006-02-26
I tried what is mentioned above and the startx command still returns error 104, and crashes. I had this problem with the live cd before, didnt think much of it. The gfx card i have is an ati express 200M (laptop) and i have an amd 64 but turion processor in here, but i am using a 32 bit version of kubuntu. Any help?

---

### Post by pointym5 on 2006-02-26
What's in your server log?

---

### Post by florencio torre on 2006-02-26
Hello poeple, 

I burned the install iso image cd, now what?
it is no bootable, i am new to linux 
you can find millions of hows to except the one needed  to
boot from de iso file , I have a pentrium III with no partition in the HD, 
a have "A>" booting from windows rescue floppy with cd rom support

Can any body help me??????????

---

### Post by Rooinek on 2006-02-27
[QUOTE=florencio torre]Hello poeple, 

I burned the install iso image cd, now what?
it is no bootable, i am new to linux 
you can find millions of hows to except the one needed  to
boot from de iso file , I have a pentrium III with no partition in the HD, 
a have "A>" booting from windows rescue floppy with cd rom support

Can any body help me??????????[/QUOTE]

just a couple of questions .......
1. Did you verify the MD5 sums ? - if not, do that please.
2. What speed did you burn the ISO at ? - most ISO's should be burnt at 8x or less. I burn mine at 4x, ( only takes a couple of minutes longer) and no longer have a bunch of coasters laying around ;) ;)

---

### Post by Rooinek on 2006-02-27
[QUOTE=arckeda](Sticky this so so many people can stop having to ask about 5000 times before someone who knows answers their questions like I had to.)

This is if when using live cd or just plain ubuntu and the xserver failed to load.

Now im gona help you.

[Random silly censored profanity removed by moderator.] -zenwhen

Start booting on live cd or just ubunu then after its all done loading you will get an xserver faild to start bla bla bla error.  It will ask you if you want to view logs select no and you get a black screen hold: ctrl-alt-F1 and you get bash.

Once at the bash by holding ctrl-alt-F1 type:

sudo dpkg-reconfigure xserver-xorg 

and select vesa as driver, or vega if that doesnt work (I assume that orginally it  selected ATI, if vesa or vega dont work try ATI) then you go through some steps, fill them all out, if you have no idea what to do for keyboard, press enter, and keep pressing, it should all be defualt unless you have some weird keyboard or moniter needs.  After your done type:

startx

and you will start the xserver

then you should be in ubuntu.

[Random silly censored profanity removed by moderator.] -zenwhen[/QUOTE]
Been there, done that, no success - says my xserver is broken and a bunch of other stuff I'll try the HOW-TO that was recommended by aisyu. Thanks for the try tho:)

---

### Post by goatman on 2006-03-04
Still can't get xserver to work? niether can I ! Is it Ubuntu, or just me?? :lol:

---

