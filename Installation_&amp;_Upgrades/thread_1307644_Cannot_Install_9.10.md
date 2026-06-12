---
title: "Cannot Install 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by matt.p on 2009-10-31
Hi, I am new to Ubuntu and want to dual boot with my current XP install.  At first I tried using Wubi, but it hung on what looked like the Ubuntu desktop.  After further reading I decided I would rather *properly* dual boot anyway, so tried to install from the iso I downloaded.  

When I got to the install menu, any time I tried to select anything it just froze.  So I tried burning a new disc, this time onto DVD and slower.  

Now when I try to install, the screen goes black and the Ubunto logo fades in and out for a while, but then it freezes completely.  I have run Memtest and the disk check and both are fine.

PC Spec:
P4 2.4GHz
1.5Gb RAM
i845 Chipset
nVidia GeForce FX 5200

I have read that some people have problems with certain Intel chipsets in previous versions, but haven't found anything specific to the i845, could this be the issue?

Thanks for any help or pointing me in the right direction.

---

### Post by matt.p on 2009-11-01
Can anyone possibly shed any light onto this, or anything else I could try?

---

### Post by sprintexec on 2009-11-01
hi matt,
I am also having similar problems. downloaded karmic iso and verified and burnt cd. this will load onto my dell dimensions win xp box but at the last moment returns an error message. All the ubuntu files appear to be where they should be on my partition but I can't get it to boot at all, aj

---

### Post by matt.p on 2009-11-02
Hmmm I am going to give 9.04 a bash tonight and see how that goes...

---

### Post by nixed242 on 2009-11-02
I'm going to take a guess and say your having the same problem a few of us are also having. It's the NVIDIA Driver that's causing the problem. You can probably install Ubuntu using the Alternative CD, but it'll crash seconds after the desktop is loaded the first time you boot it up. 

See: [URL="http://ubuntuforums.org/showthread.php?t=1305130"]
[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1305130[/COLOR][/URL]

I think the way around it is to have the kernel not load the NVIDIA driver on boot, but I don't know how to make that happen since the Live CD, and the Installation process automatically detect my NVIDIA card and install the driver. 

See: 
[[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1311208[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1311208")

---

### Post by matt.p on 2009-11-02
I am very new to Linux so that might be a little over my head but I will have a read up on those threads, thanks a lot for the ideas :)

Is this version specific or will all recent Ubuntu releases have the same issue do you know?

---

### Post by nixed242 on 2009-11-02
> **matt.p said:**
> I am very new to Linux so that might be a little over my head but I will have a read up on those threads, thanks a lot for the ideas :)

Is this version specific or will all recent Ubuntu releases have the same issue do you know?

I have no clue. I'm just as frustrated as you are. :( Ubuntu 8.10 worked perfectly for me. When they changed to the newer kernels that load the video driver module at boot, I began having these issues. Try the Alternative Install CD. See if that works for you.

---

### Post by matt.p on 2009-11-02
Ok thank you - I will try the alternative install CD and if that doesn't work I will install 8.10 for now and see how that goes.  Cheers :)

---

### Post by bubbles99 on 2009-11-02
I think Ubuntu after 8.10 had a part of its graphics core updated and has *reduced* support for your card. i dont think the alternate install will work, have a good look through the forums.

---

### Post by matt.p on 2009-11-02
I best grab a copy of 8.10 for now I think then!  Thanks for the input :)

---

