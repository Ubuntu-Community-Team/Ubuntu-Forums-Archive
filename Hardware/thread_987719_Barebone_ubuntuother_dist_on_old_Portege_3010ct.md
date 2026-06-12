---
title: "Barebone ubuntu/other dist on old Portege 3010ct"
date: 2008-11-19
forum: Hardware
---

### Post by mangoes on 2008-11-19
Hi I'm a newbie and just stumbled on a Toshiba Portege 3010ct. Pentium MMX 266MHz, 64Mb ram. 4.3Gb HD.
Ancient but cute(like iguanas). Won't have the time to play with it
till next week, so meanwhile trying to hatch a little plan and get feedbacks on 
what sort of barebone system can run it for my purpose below. So if this post looks more like a
braindump  than a question, my apology.

I know this sort of topic has been done to death, but since I have a pretty clear
idea on what this little pudding will be used for(if possible), then maybe the discussions
can be a little bit more pointed. 

====================
Laptop Purpose
====================
Main Purpose:
Remotely connect (preferably wirelessly) to linux machines at home and work 
via ssh and vpn, mainly in order to run, check and post-process numerical simulations remotely. 
(The laptop has two typeII pcmcia slots, and I have a 2.4Ghz dlink airplus
extremeG cardbus adapter lying around somewhere. Not sure if they're
compatible,or if it's possible to have wireless at all on such an old machine.
Anyone?)

Secondary  purposes: 
- Surf the net mainly using text-based browser,occassionally with lightweight graphic browser if I'm forced to. 
- check emails 
- read Word and excel 
- write and typeset latex documents and beamer presentations
(if typesetting beamer is too taxing then plan b is to just edit the latex doc
in the laptop,scp it to my home box,typeset it there, and scp it back)
- view pdf,dvi,postscripts
- run lightweight maths and plotting scripts in python (too ambitious?)
)- Don't care about: video,sound,looks.
=====================
Programs
=====================
Given the above, the applications in mind are:
ssh,vpnc,elinks,epiphany,abi/antiword,gnumeric,xpdf,python,vim,latex(perhaps tikz/pgf is pushing it a bit)
Windows manager: Fluxbox,IceWM (never used before)
Other things: pc card driver, perhaps needs apm support,acpi.Anything I miss?
=======================
"Lit Review"
=======================
Debian has been successfully installed on the same laptop, minus wireless card
[http://www.gweep.net/~sfoskett/linux/p3010.html](http://www.gweep.net/~sfoskett/linux/p3010.html)

This howto on running barebone ubuntu looks great, although in the end 
advocates vectorlinux for <128Mb systems.
[http://ubuntuforums.org/showthread.php?t=62650](http://ubuntuforums.org/showthread.php?t=62650)

Enlightening discussions on fluxbox and fluxbuntu
[http://ubuntuforums.org/showthread.php?t=333796](http://ubuntuforums.org/showthread.php?t=333796)

Very encouraging discussions on vector linux in a 64mb machine 
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/linux-for-old-233mhz-64mb-laptop-that-performs-better-than-win98-546947/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/linux-for-old-233mhz-64mb-laptop-that-performs-better-than-win98-546947/)
==========================
Considered OSs
==========================
1. Ubuntu Server + IceWM/Fluxbox.
Why:used to ubuntu, good howtos lying here and there, can ask you guys&gals
Q: is ubuntu server going to be tricky for laptops in terms of wireless card driver detection etc?
2. VectorLinux Lite with IceWM/Fluxbox
Why: sounds like it's fast on low memory systems.
Q: nothing yet
3. Puppy or DSL. I've tried them and they're really fast with old machines. But prefer to keep them as live os only.
4. Debian
=========================
My experience
========================
Only have installed ubuntu on easy systems. Gutsy on a desktop, full xubuntu gutsy from alternate cd on a 192mb PII dell laptop,dabbled w/ minix on the same laptop but couldnt get x running. Set up ssh dynamicdns vpnc vnc. I've been a passive user of unix/linux systems(at work) for 
the last 5 years and v comfortable with (and  prefer) command lines. A bit hazy with admin stuff though.
====================
Over to you
===================
Suggestions? Is is a feasible project (esp getting wireless going) ? Anything I miss ?
==============
Edit
==============
Forgot to say no cd drive, so install from USB stick.

---

### Post by cariboo on 2008-11-19
You could use the mini iso to install to the cli, then add extra packages as you need them. THe mini iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I used the mini iso on an 400Mhz eMachine with 128Mb ram. I originally just ran it without a gui, but decided to try Ubuntu Lite to see how it would work on an older computer. I have since disabled gdm, so it won't start and have gone back to using it from the command line. :)

Jim

---

### Post by mangoes on 2008-11-21
> **cariboo907 said:**
> You could use the mini iso to install to the cli, then add extra packages as you need them. THe mini iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I used the mini iso on an 400Mhz eMachine with 128Mb ram. I originally just ran it without a gui, but decided to try Ubuntu Lite to see how it would work on an older computer. I have since disabled gdm, so it won't start and have gone back to using it from the command line. :)

Jim

Thanks I'll give it a try. This maybe a stupid question, but would this work using external cdrom drive with pcmcia card ? If so then I'll borrow one from a friend.

---

