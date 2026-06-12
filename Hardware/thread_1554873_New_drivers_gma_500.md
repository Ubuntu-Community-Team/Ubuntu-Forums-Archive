---
title: "New drivers gma 500"
date: 2010-08-17
forum: Hardware
---

### Post by pek007 on 2010-08-17
hi,

last two day i am trying to fix that problem. it looks like a new update for psp is not compatible with something new...

now i lost VLC picture... well, any picture in any movie player... also in "mpalyer"...

and also the thunderbird 3 does not work... it dont display any emails to me... just that there are...

any ideas what can i do, to fix that?

bye, ziga

---

### Post by Fafler on 2010-08-17
I don't know what to do about your gma 500 problems, but try mplayer -vo list and test some different video out drivers, for a temporary solution.

---

### Post by pek007 on 2010-08-17
well, nothing works :S
i add some pic, too see how everything looks :S

bye

---

### Post by Fafler on 2010-08-17
You could try making a Xorg.conf and use the vesa driver instead of whatever it's using now, but i'm not sure vesa works with the gma 500.

What actions exactly brought into this mess?

---

### Post by pek007 on 2010-08-17
update? :D
no, really, 2 days ago, there was new update of something... everything works if i do clean install and than go to this page: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) and just do what it says. i also tryed to download that iso... it worked till now. now it is not working, not the dl, but the install when you make it. yes, and after i do like it says on this page, restart, everything works nice... than go to update manager... and it dont work anymore. i also tryed to update first, than do that what it says on page... same result... dont work anymore...

i dont know linux so well, that i could do anything by myself... but i was looking on forums... and i couldnt find out anything...

:S

bye

ps: vesa dont work with gma 500 i think

---

### Post by Fafler on 2010-08-17
You should spend some extra on your next laptop. Life is way to short for crappy hardware.

I don't really know what to look for, but i'll give it a shot.

Try posting your /var/log/Xorg.0.log and ls -l /var/cache/apt/archives/

---

### Post by pek007 on 2010-08-17
thank you.
well, i have dell mini 10 :P and yes, i see it sux :S

i am trying to look into that you wrote, but i cant open that log file. can only open .old
and the second comand it gives me a lot of lines in terminal... i dont even see top. you will have to tell me step by step... or i am doing something wrong...

ps: i opened with nano. but dont know how to copy you all... so i put it in zip and added it here.

---

### Post by Fafler on 2010-08-17
sudo cat /var/log/Xorg.0.log

If you still cant access it, just give me the old one. Cut'n'paste from the terminal. Or

sudo cp /var/log/Xorg.0.log /home/[insert your username] 
sudo chown [your username] /home/[well i gues you get it by now...]/Xorg.0.log

As for ls, just cut'n'paste the whole thing. Or

ls -l /var/cache/apt/archives/ > packagelist.txt

And post the resulting file. It's a list of all the packages you've upgraded.

---

### Post by pek007 on 2010-08-17
ok, i think i did it... :P
i put them into zip, because they were too big and with wrong ending to attach.

---

### Post by Fafler on 2010-08-17
I can't really read anything relevant out of your Xorg log file, but the directory listing shows you have upgraded both your kernel and your Xserver.

-rw-r--r-- 1 root root 31473052 2010-08-04 23:15 linux-image-2.6.32-24-generic_2.6.32-24.39_i386.deb
-rw-r--r-- 1 root root    83452 2010-07-21 15:06 xserver-common_2%3a1.7.6-2ubuntu7.3_all.deb
-rw-r--r-- 1 root root  2408744 2010-07-21 15:06 xserver-xorg-core_2%3a1.7.6-2ubuntu7.3_i386.deb
-rw-r--r-- 1 root root   889238 2010-07-05 03:18 xserver-xorg-video-psb_0.36.0-0ubuntu3~1004um9_i3

Your problem probably lies in one of those packages. The best thing i can think of is that you try to boot your old kernel, which should still be present.

See this link for directions and ask if you need more help.

Edit: Now with link: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by pek007 on 2010-08-17
well, i think the problem is in new Xorg. because with this kernel allready everything worked nice. is there any way that i get back old kernel?

---

### Post by Fafler on 2010-08-17
When the ubuntu logo first appear or maybe even before that, press escape and you should get a menu where you can choose the old kernel.

But why don't we just downgrade? Do a

apt-cache search linux-image generic

And it should give you a list of available kernels. Either post a complete list or do a 

sudo apt-get install linux-image**=**2.6.32-24.39

The version number should of course be that of the old kernel instead and note the = instead of a -. Do the same with xserver-common, xserver-xorg-common and xserver-xorg-video-psb.

---

### Post by pek007 on 2010-08-17
well, i tryed to go into old kernel, but it didnt go. stayed at the black screen. also the safe mode with low Xorg didnt work. black screen again. i will try to downgrade all the things. hope it will work.

---

### Post by pek007 on 2010-08-19
ok, nothing wotks... :S i found out, that there was update to 10.04.1 ... and in this version all the stuff doesnt work as it should :S

---

