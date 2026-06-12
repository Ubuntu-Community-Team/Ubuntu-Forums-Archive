---
title: "Mission impossible: add hard disk"
date: 2008-10-10
forum: General Help
---

### Post by YigalB on 2008-10-10
Since I know that using Ubuntu and easily adding hard disk are parallel lines, I simply buy bigger hard disk and re-install the whole system.
Last time, I got help by modifying system files, which should legaly forbidden for non guru personal.
This time I decided that it's either me or the Ubuntu. My rules were simple: i was allowed to use only GUI. No manual editing of /etc/anyFile.
I used GRUB, and after some time I could find the disk and mount it to a label of a previous disk I had. Still by the book. 
I wasn't able to give a new name, but still.
I think I could mount it, because now I have the ability to unmount it. 
I can even see it (have it on my desktop), but can't use it: I just wont let me create directories, nor by GUI nor by command line (I gave up). Something about permission (I hate when machines don't allow me doing things).

Before I show my computer how to swim in sea water: is there an EASY way to add additional hard disk with Ubuntu? 
By Easy I mean non-guru procedure. 
Ubuntu is so much easier to install, comparing to XP, so how was it decided to make it impossible to add additional hard disk? 

Thanks
and sorry for being cinical.

---

### Post by zergling on 2008-10-10
Hi,
Did you try

sudo chmod -R 777 /media/your_hd ?

Once you have performed the chmod command, unmount the hd and than mount it again. 

After that, go to system - > administration - > system monitor

Kill nautilus by select it, right click and select KILL process.

If everything went ok, now you should be able to create and delete directories :D

If you need further help, just let me know ok :)?

Ciao!

---

### Post by YigalB on 2008-10-10
The Chmod worked!!
Thanks.

And now we are back to the main question:
- how can we claim the Ubuntu is for the people if one needs to type such commands? Shouldnt it be assumed that if a user is adding a hard disk, then the hard disk sould be writable? and have right access? or at least: ask at the installation phase "do you want this disk to act as normal disk or should we limit it's usage for the people who knows the octal numbers?"

We need to ensure that regular humans will be able to perform such activity.

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by YigalB on 2008-10-10
sorry - but i can't read what you just posted. It looks like:
"&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;"

---

