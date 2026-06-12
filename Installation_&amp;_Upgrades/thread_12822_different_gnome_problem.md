---
title: "different gnome problem"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by sisya on 2005-01-27
hello all,

put simply my problem is that gnome just wont start...

ya i know other threads have discussed this thread-bare (pardon the pun)

but i feel mine is slightly different..

in the other threads which discuss gnome probs people talk of some brown screen.  but my problem is when i boot my system...it goes blah blah blah [ok] [ok] [ok] and then it says something like "....starting gnome..." and then....

and then....

IT GOES BLANK....IT GOES ABSOLUTELY BLANK....NO BROWN NO RED NO SPLASH NO DRUMMING....IT SIMPLY GOES BLANK....


PLEASE HELP ME...I AM NEW TO LINUX AND UNLIKE MANY OF YOU THOUGH I AM GIVING LINUX A TRY I AM NOT EXACTLY A MS OR M$(AS U GUYS WUD PUT IT) HATER.  I LOVE WINDOWS...AND NOBODY CAN CONVINCE ME OTHERWISE.  IF U GIVE ME 100 REASONS Y I SHOULD HATE M$ I CAN GIVE U 1000 REASONS Y I LOVE IT....WELL THAT IS ENTIRELY A DIFFERENT DEBATE...

for now, please for god's sake somebody help me out....pleeeeeeeeese....this is the first time am asking for help on a linux forum and please show me that the open source community doesnt hate the non converts.   

ok i'll end my ranting....but again pleeeeeeeeeese help me. please

my comp specs

p3
nvidia
256 mb ram
733 mhz
16 mb video
dual boot - win 2k and hopefully ubuntu.

---

### Post by sisya on 2005-01-27
i also tried booting into the ubuntu recovery mode.

it only takes me to the root prompt.. ..that is it....no gnome..:(

---

### Post by Buffalo Soldier on 2005-01-27
I'm not sure what the problem/solution is. But maybe by providing more info it will be easier for others to help.

[list]
[*] Is this your first time booting to Ubuntu after fresh install?
[*] What type of install did you use? default/custom/expert? Just pressing enter at the beggining of the installation starts the default install (automatically installs and configure everything you need)
[*] If its not your first time booting into Ubuntu and you manage to get a nice clean desktop before... what was the last changes that you've made before having this problem?
[/list]

It's hard if you're a first timer to GNU/Linux. Everyone here have faced some problems during their first encounter with GNU/Linux. Keep your head cool, don't panic and read a lot. I'm sure after all the problem is solved, you'll be proud of yourself :)

---

### Post by sisya on 2005-01-27
hey buffalo soldier
thanks for the encouraging words man well here're the details

yes this is the very first time i installed ubuntu. i've actually been playing around with  linux for a few weeks now....started with RH 8 moved to rh9 and then moved to fedora core 1...i didnt find any of them good enough for a home desktop.  i couldnt care less how good linux is for running servers and stuff but in my opinion, all said and done, all things considered windows is the best os on the face of this earth for home desktop.

well as for my ubuntu installation....

what i did was i first deleted the partition that i was using for fedora...and installed ubuntu on it...the install went well and it asked me if i wanted to get other needed stuff from the net and upadate and i said yes.  it then took forever to download and install but it still went well...and finally after it was all done and restarted...it went the usual linux blah [ok] blah [ok] blah blah [ok] and between all the [ok] s i saw this

modpobs:FATAL ERROR inserting pciehp...........operation not permitted
modpobs:FATAL ERROR inserting shpchp.........operation not permitted

and then it continued with a few more [ok]s ...and then said something i think was to the effect, "fasten your seatbelts!! here comes gnome!! and then poof! 
the screen goes BLANK....

totally blank....

so then i used my beloved win 2000 came to this forum read a little posted my groan and went back and REINSTALLED ubuntu this time....

but this time i didnt do any updates from the net...just plain vanilla whatever was on the cd.....

same shit....no change....

blah blah blah blah...gnome about to start.......

blank screen

god help me!!  please

---

### Post by Adrenal on 2005-01-28
Sounds like a faulty install disk, or a faulty install. If you downloaded the .iso, reburn it and try again

---

### Post by nikopol on 2005-01-28
RE:modpobs:FATAL ERROR inserting pciehp...........operation not permitted
modpobs:FATAL ERROR inserting shpchp.........operation not permitted

Though it says fatal, it actually isn't. See ubuntuguide.org on how to prevent the message from appearing...


Your problem is however very vague - it could be that your Xserver is misconfigured. How about you do the following

cat /var/log/XFree86.0.log | grep EE

and write down what's there and post it in this thread?

---

### Post by crane on 2005-01-28
sisya,

 hmmmm.... more info would have been nice.

Oh wait I just saw your other post. Poor attitude, enjoy Windows!

---

### Post by nikopol on 2005-01-28
[QUOTE=crane]sisya,

 hmmmm.... more info would have been nice.

Oh wait I just saw your other post. Poor attitude, enjoy Windows![/QUOTE]
 Yeah - realised after I responded the chap was a troll. Wouldn't have bothered if I knew :(

---

