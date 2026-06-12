---
title: "Dell Inspiron 6000 Display Issue ."
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by moodyz on 2006-07-24
Greetings all ...
im on my way of shifting from Windows OS to Linux Inviroment ,which is a a major shift i may say .

Any how , I installed Ubuntu Ver 5.04 HH , not sure of the version exactly , I completed the installation and rebooted my system , now once it finishs the post and loading linux login page , i can HEAR the Login Drums Sound , but i cannot see anything ...

i have no idea how to fix this ! any one got this Problem before ?

I think its because of my Wide monior ? 

AnyHelp is much appreciated ...

---

### Post by Paerez on 2006-07-24
I am not sure what the problem is, but why did you install 5.04? Thats over a year old! I would try 6.06 or at least 5.10.

If you want to try to fix this issue, please post your /var/log/Xorg.0.log.

---

### Post by Ziox on 2006-07-24
what video graphic card do you have? and what does this command return?

cat /etc/X11/xorg.conf

---

### Post by bsalt on 2006-07-24
> **moodyz said:**
> Greetings all ...
im on my way of shifting from Windows OS to Linux Inviroment ,which is a a major shift i may say .

Any how , I installed Ubuntu Ver 5.04 HH , not sure of the version exactly , I completed the installation and rebooted my system , now once it finishs the post and loading linux login page , i can HEAR the Login Drums Sound , but i cannot see anything ...

i have no idea how to fix this ! any one got this Problem before ?

I think its because of my Wide monior ? 

AnyHelp is much appreciated ...

moodyz, i have a dell inspiron 6000 with the basic video card (i think it's the intel gma 900 or 950) and i have no problems. i've never tried Ubuntu 5.04, but i know it works flawlessly under 5.10 or 6.06 (what i'm running now). don't install such an old distro man! go to [www.ubuntu.com/download](www.ubuntu.com/download) , choose a mirror (the first one is good enough) and get the iso for the desktop x86 install. or if you have a slow internet connection, go to [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) and request a cd be sent to you. don't go to as old as 5.04 though. 

good luck and God bless,
jonathan

---

### Post by moodyz on 2006-07-25
Thanks Paerez & Ziox , i installed the 5.04 because thats what i have on CD , the live CD works fine ...
its just the installation CD giving me a hard time ..
My Display card is Intel 's 915 GM ...

bsalt , thanks for the advice , i've already Requested  the CD's but that will reach in 3 - 6 weeks i beleive ?

Btw , Paerez & Ziox , im a total n00b in linux , 
cat /etc/X11/xorg.conf looks like a path to me , but since i cant login to the GUI , how can i reach that ?

Safe mode , ? ls command ? any command list available on the internet with explanation for each one ?

Thanks for replying :-D 

Blessing ...

---

### Post by dasunst3r on 2006-07-25
I remember this happening to me one time.  Try connecting an external monitor.

I do not quite remember how to solve this; and now that I am on SLED 10, I do not know how to solve it without using some graphical tool to help me choose where my video out should go.

---

### Post by moodyz on 2006-07-25
> **dasunst3r said:**
> I remember this happening to me one time.  Try connecting an external monitor.

I do not quite remember how to solve this; and now that I am on SLED 10, I do not know how to solve it without using some graphical tool to help me choose where my video out should go.

SUSE that is yeah ?
as i told you im new to this , and looking forward to master it , like i did with Windows O.S and Cisco Products ...

i just need resources and time ...
Will appreciate any good resources for learning Linux , i have to know and understand many things such as Software installation , Troubleshooting , etc ...

---

### Post by Ziox on 2006-07-25
> **moodyz said:**
> Thanks Paerez & Ziox , i installed the 5.04 because thats what i have on CD , the live CD works fine ...
its just the installation CD giving me a hard time ..
My Display card is Intel 's 915 GM ...

bsalt , thanks for the advice , i've already Requested  the CD's but that will reach in 3 - 6 weeks i beleive ?

Btw , Paerez & Ziox , im a total n00b in linux , 
cat /etc/X11/xorg.conf looks like a path to me , but since i cant login to the GUI , how can i reach that ?

Safe mode , ? ls command ? any command list available on the internet with explanation for each one ?

Thanks for replying :-D 

Blessing ...

there are couple "virtual consoles" in linux, activated by ctrl+alt+F1 to F7.  There you can login and then activate commands, but there isn't any graphics.  But if you can, login to ctrl+alt+F1 and then activate the command cat /etc/X11/xorg.conf. Or if you can't see the whole file then do: nano /etc/X11/xorg.conf

If you want to learn some basci things about ubuntu, then check out my signature's link: general help

---

### Post by moodyz on 2006-07-25
> **Ziox said:**
> there are couple "virtual consoles" in linux, activated by ctrl+alt+F1 to F7.  There you can login and then activate commands, but there isn't any graphics.  But if you can, login to ctrl+alt+F1 and then activate the command cat /etc/X11/xorg.conf. Or if you can't see the whole file then do: nano /etc/X11/xorg.conf

If you want to learn some basci things about ubuntu, then check out my signature's link: general help

cheers Buddy ...
will try it tomowoz and will let ya know ..
tnx

---

