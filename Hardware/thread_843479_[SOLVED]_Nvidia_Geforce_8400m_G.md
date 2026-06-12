---
title: "[SOLVED] Nvidia Geforce 8400m G"
date: 2008-06-28
forum: Hardware
---

### Post by kenji.nanashi on 2008-06-28
hi everyone
I have an ACER ASPIRE 5520, with a nvidia geforce 8400m g video card, and just recently installed ubuntu (toooootal noob, btw)
if i don't install any drivers i can get th,e video card to work, but with very poor results (no compiz, video is ver sketchy, etc)
so i hunted around the net for solutions and found ENVY, which I installed, got it to install the nvidia driver, and Ubuntu fires up quite well. the desktp effects work and the video playback is good. but the pc freezes. at random times, not specifically if i open a video or run a program.

so i have to shut down brutally, restart and i get the same problem
the only way i can avoid this is by uninstalling the drivers, but that's a pity seen as the video card isn't that bad (when it runs on vista i get pretty good performance, so I'm guessing Ubuntu should take it to a different level)

can anyone help or tell me where is should be looking for solutions?

thank you everyone in advance

---

### Post by Mikecore on 2008-06-29
> **kenji.nanashi said:**
> hi everyone
I have an ACER ASPIRE 5520, with a nvidia geforce 8400m g video card, and just recently installed ubuntu (toooootal noob, btw)
if i don't install any drivers i can get th,e video card to work, but with very poor results (no compiz, video is ver sketchy, etc)
so i hunted around the net for solutions and found ENVY, which I installed, got it to install the nvidia driver, and Ubuntu fires up quite well. the desktp effects work and the video playback is good. but the pc freezes. at random times, not specifically if i open a video or run a program.

so i have to shut down brutally, restart and i get the same problem
the only way i can avoid this is by uninstalling the drivers, but that's a pity seen as the video card isn't that bad (when it runs on vista i get pretty good performance, so I'm guessing Ubuntu should take it to a different level)

can anyone help or tell me where is should be looking for solutions?

thank you everyone in advance

I'm not sure what ENVY is but you should be using your add remove gui program to install the "new" nvidia drivers for your graphics card.
make sure you enable the view for "all available applications" and in the search bar type nvidia you should see two options I pretty sure your card needs the "new" driver. ( uninstall ENVY before installing the new driver )

---

### Post by starcannon on 2008-06-30
Heres how I install the Nvidia 8400m GS drivers, don't skip steps and you'll be golden:

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL

---

### Post by kenji.nanashi on 2008-06-30
Thanks mikecore, 
ENVY is a little program that automatically installs drivers for ATI and NVIDIA cards.
I tried installing the drivers from synaptic but got no luck out of it.
Will try with the "all available applications" tonight and see if that works.
thanx again!!

---

### Post by kenji.nanashi on 2008-06-30
will try to follow the guide starcannon, thanx for the help, i hadn't found this onee in the search
hopefully one of the 2 solutions offered will solve this
will update you with the outcome

---

### Post by kenji.nanashi on 2008-07-01
well, i tried reinstalling the system from scratch, and am now getting problems with vista too (nasty error messages about the video driver not working)
so, it looks like i'll be taking my laptop to get fixed (hopefully) or replaced (maybe a better idea)
thank you for the help anyway guys!!

---

### Post by starcannon on 2008-07-02
My one and only dual boot box (currently partially disassembled, scavenged it to deal with a troubleshooting situation), anyway that box, the 6600gt works flawlessly under Ubuntu, and under windows it requires me to adjust its resolution every boot... I could probably fix it, but pft who cares, I can't even remember the last time I needed to boot the dualboot box into windows, in fact, its so important that its still in my office partially disassembled lol.

---

### Post by kenji.nanashi on 2008-07-03
Only reason I dual boot (well, apart from still being too much of a newbie to linux) is because of work. I need programs like Pro Tools and Cubase to run flawlessly.. 
But I must say, Ubuntu has already replaced Windows for my day-to-day activities..

---

### Post by starcannon on 2008-07-04
I wonder how those programs would run in Virtual Box? Probably fine, it may be worth a look:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by kenji.nanashi on 2008-07-05
I heard these programs don't run well on virtual machines, but hey, i'll give it a try.. you never know..
i'll also be trying ubuntustudio for my own projects, it seems to be a nice innovative solution..

---

