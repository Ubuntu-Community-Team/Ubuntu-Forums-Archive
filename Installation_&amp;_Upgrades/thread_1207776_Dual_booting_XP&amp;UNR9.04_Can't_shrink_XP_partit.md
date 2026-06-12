---
title: "Dual booting XP&amp;UNR9.04: Can't shrink XP partition size"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by AeroRG on 2009-07-08
Hi people, I'm new to the forum. I don't like creating accounts just to ask a question, but I've been reading a lot and couldn't find an answer to my problem.

I have a HP mini 2140 with XP pre-installed, I want to dual boot it with UNR.

It recognizes WinXP Home, but I don't get the "Install Side By Side" option. So choose the manual option.

My problem is, when I get to the partition part of the installation, the XP partition takes almost all of the HDD, 152617MB, and just leaves 8MB free, so I need to resize it to make space to install Ubuntu.

When I rightclick it>edit I don't get any option to change its size, I only get options like selecting the format and something else I can't remember..

I also tried GParted, and when i click on resize it it only allows me to make it bigger, adding those 8 MB free, but it doesnt allow me to shrink it...

I already ran the defrag program in xp.

I don't know what else to do. Any help guys? This is really frustrating =/

Thanks in advance!

---

### Post by cariboo on 2009-07-08
I noticed that some of the installers depending on what version you are using mount all the partitons at boot. If your Windows partitons is mounted and there is an icon on the desktop, just right click it and unmount the drive. You should now be able to partiton your XP partiton.

---

### Post by AeroRG on 2009-07-08
Thanks for the answer mate.

But what do you mean with unmount the drive? I'd say I know pretty much about Windows but I cosider myself noob at Linux.. =P

And also what desktop are you talking about? Win's or Ubuntu's ?

---

### Post by AeroRG on 2009-07-08
Just in case anyone had a problem like mine, the solution is simple, i just found it by myself..

You need to boot into windows, go to start>run and type cmd

then type "chkdsk c: /f" withoutquotes, that's assuming the hdd you want to fix is the C drive

it will say you need to reboot, type y and then hit enter

the next time you boot windows the process will begin, and depending on how much stuff you have in you hdd and the speed of your computer, of course, is the time it will take to fix the problem

Since my netbook is new, like 3 days old, it fixed the problem in less than 5 minutes.

Also be sure to defrag you hdd.

I did both of these procedures twice and now i can acces the partition perfectly (:

hope this can be useful for people out there with my same problem.

---

### Post by kle on 2009-07-25
> **AeroRG said:**
> Just in case anyone had a problem like mine, the solution is simple, i just found it by myself..

You need to boot into windows, go to start>run and type cmd

then type "chkdsk c: /f" withoutquotes, that's assuming the hdd you want to fix is the C drive

it will say you need to reboot, type y and then hit enter

the next time you boot windows the process will begin, and depending on how much stuff you have in you hdd and the speed of your computer, of course, is the time it will take to fix the problem

THANKS AeroRG! This was just what was needed for people who are more at home in (k)ubuntu than in Windows.

---

