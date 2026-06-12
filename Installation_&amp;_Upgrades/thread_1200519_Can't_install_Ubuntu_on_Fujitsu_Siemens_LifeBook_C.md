---
title: "Can't install Ubuntu on Fujitsu Siemens LifeBook C Series"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Adavur on 2009-06-30
Hi everybody. A friend gave me his old laptop, a Fujitsu Siemens LifeBook C Series with 30 GB hard disk divided on two partitions and with 368 megabytes of RAM. It runs Windows XP Professional very slowly, so I though of installing Ubuntu on it to make it faster.

Here is a video I made about it, if it helps:
[http://www.youtube.com/watch?v=bpaXj6Y7dqw]("http://www.youtube.com/watch?v=bpaXj6Y7dqw")

I've already got a comment about holding F11, but I don't really know when I should hold it.

As you can see in the video it boots from the Ubuntu-CD very well, but then it just loads and the screen goes black and nothing else happens.

What Can I do? Is there any other way to install Ubuntu?
Whould it help if I maybe could boot it from a hard disk (it can't boot from USB, but can I copy the CD to the hard drive or something?)?

Please help me, this computer would be so much nicer with Linux than with XP (especially this ;))

---

### Post by frankwakeman on 2009-06-30
Press F6 when you've got the Live CD's opening screen, then put a 'x' next to nacpi and nolapic

It will probably boot then (but you may find other soluble or not-so-soluble trouble, like graphics chip not being recognised, and even my fairly new laptop isn't totally smooth as far as that trailing goes).  If the resolution looks right when the desktop starts though, bingo!

Either way, bump your RAM up a bit, that improved things drastically with my XP laptop.

---

### Post by Sef on 2009-06-30
>  Either way, bump your RAM up a bit, that improved things drastically with my XP laptop. 	

Yes, 368 mb ram is too low to run Ubuntu well.

---

### Post by Adavur on 2009-06-30
Will this alternate installer help me?

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Adavur on 2009-06-30
Now I tried installing Ubuntu from the alternate CD as it was requested from another site and it removed Windows XP, but when I boot up now with the new system installed it does exactly the same.

Is it the 368 MB of RAM? I just though that it could run Ubuntu, maybe a bit slow, but that it could run it faster than Windows XP.
Aren't Linux smaller and faster than Windows?

And is there other Linux distributions I could use if Ubuntu really is too big for the pc? I won't pay 100 $ for 512 MB RAM instead (yes, I checked the prices ;P)

---

### Post by frankwakeman on 2009-06-30
512 mb in Ram total is fine many of us find, and a 256 mb chip of the correct ram from a reliable person on ebay won't cost much at all (used RAM in a used laptop, a happy marriage!), $10 maybe.  I'm guessing you've got a 256 mb chip and a 128 mb, the latter likely needing to be taken out for the 'new' chip, a quick job usually.  Both my desktop pc and my netbook run Ubuntu fine with 512 mb.

Did you not try the acpi lapic thing?  A certain point in your youtube video suggested that that was the problem, and I had the same freeze with my dad's laptop solved by what I suggested.

---

### Post by Adavur on 2009-06-30
Yes I did try to put an 'x' on both of those you mentioned at the same time. Should I try to do it with only one of them at a time (to be honest I don't really know their function)

---

### Post by frankwakeman on 2009-06-30
I'm not technical enough to explain that but I know it has worked, but yes try one and not the other or type the actual remark (e.g. noacpi) on that line of Linux gibberish :-) that you see for Boot commands on the same screen.

You could try Xubuntu but it is a bit uninspiring....

Knoppix, maybe.

---

### Post by frankwakeman on 2009-06-30
And have you seen this?

[http://tuxmobil.org/fujitsu.html](http://tuxmobil.org/fujitsu.html)

---------------------------------------------
I'd also overlooked that you can put a x next acpi=off in those options too, so there's three not two of those
---------------------------------------------

---

### Post by Adavur on 2009-07-02
Yes, thank you, they don't have exacly the C 1010 model, I have, but I might find something in there ;)

But anyway, I still think that it must be some kinda graphical error. Now I installed Ubuntu Jaunty through the alternate installer as requested and if I press ESC under startup I enter the GRUB bootloader.
Will any things under the Recovery Mode help me? If yes, which should I try?

---

### Post by crimpshinre27 on 2009-07-09
I'm in the exact same boat - Siemens Lifebook C-series 1066mHz 256mb of Ram

these are the OSs i've tried so far and fail in the same manner:

Ubuntu live CD
Ubuntu text based installer
Crunchbang
Fluxbuntu
OpenSolaris

These Live CDs work:

Damn Small Linux 
SLAX

Bizarrely the Ubuntu live CD worked once and ran fairly smoothly too - detected my PCMCIA Wireless card and could connect to the internet but hasn't run since. I don't think it's a graphics problem - you don't get the Jumanji sound Ubuntu makes when the login screen crops up and the hard disk LED is as dark as the screen after the splash disappears.

let me know if you have any luck
Jamie

---

### Post by Adavur on 2009-07-11
Well, I've been told by the earlier owner of my pc that it ran Ubuntu once, but I haven't seen it. So seems like the same problem.
Since then I've got Knoppix, Puppy Linux, PCLinuxOS and OpenSUSE to work. I have SUSE with GNOME installed right now and it works fine. I think I will keep it even though Ubuntu is my favourite.

Post if you ever find any solution, but SUSE actually runs faster on such an old PC that we've got ;) Puppy is the fastest because it runs in your RAM, but installed SUSE with GNOME is very much like Ubuntu.

Good luck and have a nice day.

---

