---
title: "XPS m1330 with X3100 graphics problem"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by stlcoptony on 2008-02-10
Hi everyone. I have removed vista from the above mentioned computer and installed nothing but ubuntu (I formatted the whole drive and the media direct thing has not nuked the system yet). I have now found out about the whole blacklisted Intel X3100 graphics with compiz..... This is really annoying as I had picked Intel because I thought they would be better supported. 

Does anyone know if this will be resolved, either with a new driver or with version 8.04? I know it sounds bad, but I would really like some nice effects on here.

Also, I found the workaround by amaranth which allows you to skip checks and run compiz anyway. What should I avoid to keep the system from crashing?

thanks
Tony

---

### Post by stlcoptony on 2008-02-11
also, at this site [HERE]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61") they use the hardy repositories to enable compiz. Has anyone tried this yet? does it help with the crashing while playing video?

thanks

---

### Post by stlcoptony on 2008-02-14
anyone have any ideas?

thanks

---

### Post by mybunche on 2008-02-16
I really hope they get this working out of the box for 8.04. X3100 is quite abundant now.

Sorry, I have no idea how to help you. I hope someone can.

---

### Post by stlcoptony on 2008-02-17
yeah, me too. It seems like a pretty capable integrated graphics chip.

---

### Post by jespdj on 2008-02-18
According to [http://www.ubuntu.com/dell](http://www.ubuntu.com/dell) the XPS M1330 with Intel X3100 is officially supported to run Ubuntu by Dell, so it should work.

My M1330 has an nVidia 8400M GS and it works perfectly. Sorry I can't help you more specifically with your problem.

---

### Post by stlcoptony on 2008-02-18
it works with ubuntu fine. It is blacklisted by Compiz, however

---

### Post by PAMD on 2008-02-27
I have a laptop Sony Vaio VGN-FZ29VN with an Intel GMA X3100 graphics card.

-Installation trough Ubuntu 7.10 live CD was not possible since only the fourth of my screen displayed a small part of the graphical data.
-Installation in safe graphical mode was even worse, just a black screen with strange colors
-Installation through Fedora 8 was fine. 

I wanted Ubuntu but the graphical card left me no choice ...

PAMD

---

### Post by Yellow Pasque on 2008-02-27
You could try un-blacklisting and seeing if it works
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by stlcoptony on 2008-02-27
I have done that, but it crashes if you try to play video at the same time. The current solutions allow you to either run compiz without video playback (or turn compiz off when watching video) or use the CPU for video processing (very slow and power hungry). These are the current solutions as I understand them. 

Let me know if I am missing something

tony

---

### Post by Yellow Pasque on 2008-02-27
> **stlcoptony said:**
> I have done that, but it crashes if you try to play video at the same time. The current solutions allow you to either run compiz without video playback (or turn compiz off when watching video) or use the CPU for video processing (very slow and power hungry). These are the current solutions as I understand them. 

Let me know if I am missing something

tony
Yeah, that sums it up pretty well.

---

### Post by dgr62679 on 2008-02-27
I just bought an ACER 4720Z and want to dual boot it with Gusty, my laptop has the X3100 card, is this going to be a problem?  Should I look at another version of Linux?  If so, what do you recommend for beginners?

---

### Post by ethanay on 2008-02-28
Hi dgr62679

No, it shouldn't be a problem at all unless for some reason you can't live without Compiz.  I am running just fine without it, and actually prefer the simpler format.  You can still have a sharp looking desktop without it -- it just won't be 3D.

I tried Compiz and it was buggy and distracting.  I have yet to see ANY writeup of specifics on how it actually "improves the desktop experience" beyond adding 3D eye candy for the computer-gaming generation (of which I am a part!).

I run three virtual desktops, have a drop-down panel, all the standard keyboard shortcuts for workspace and window management.

cheers,
Ethan

---

### Post by stlcoptony on 2008-02-28
> **ethanay said:**
> Hi dgr62679

No, it shouldn't be a problem at all unless for some reason you can't live without Compiz.  I am running just fine without it, and actually prefer the simpler format.  You can still have a sharp looking desktop without it -- it just won't be 3D.

I tried Compiz and it was buggy and distracting.  I have yet to see ANY writeup of specifics on how it actually "improves the desktop experience" beyond adding 3D eye candy for the computer-gaming generation (of which I am a part!).

I run three virtual desktops, have a drop-down panel, all the standard keyboard shortcuts for workspace and window management.

cheers,
Ethan

It's not really a problem unless you spend all day on the computer for school or work. I use ubuntu just for fun and as such, wants everything to work. Hopefully this will be fixed at some time

---

### Post by dgr62679 on 2008-02-29
I think that the 3D stuff is cool for about a week, so I am fine without it.  I am not a gamer.  I just wasn't sure if it was going to work.  I don't even know what you can do with compiz?  I am a true beginer with linux and am just looking to pick up a few skills, like bowstaff skills, knife skills, you know stuff like that, no but really I want to try and learn as much as possible so that I can manage my computer and help others out and let them know how awesome ubuntu is.

---

### Post by stlcoptony on 2008-02-29
you won't really need compiz for any of that

---

### Post by ethanay on 2008-04-25
yeah, compiz isn't really even the icing on the cake -- it's more like the sprinkles on the icing on the cake.

---

### Post by visionofarun on 2008-05-03
As Hardy Heron is out now, has anyone tried if it has fixed the compiz problem with X3100 on m1330?

---

### Post by stlcoptony on 2008-05-04
I, too, am wondering about this. Before I nuke another vista install (that works) has anyone tried this with the X3100?

thanks

---

### Post by Yellow Pasque on 2008-05-04
IIRC, the problem is with Intel's video driver code, so the OS change has no impact. Search for a site that has the latest repo and changelogs for that project and stay abreast of developments.

---

