---
title: "Are VAIO's any good with Linux?"
date: 2004-12-22
forum: Hardware &amp; Laptops
---

### Post by Enygma on 2004-12-22
I'm most likely going to be off to Australia at some stage in the new year and don't fancy dragging my desktop with me, so it looks like I'll be getting a laptop then.

I was looking at some Sony VAIOs on [www.sonystyle-europe.com](www.sonystyle-europe.com) the prices are fairly ok. 

Just wondering if people have had many problems with VAIO's and Linux. Is the hardware support ok?

---

### Post by safecracker on 2004-12-22
I've always found Vaio's to work great with Linux. my 505fx is running Gentoo. 

Edit now running Ubuntu

---

### Post by keylargodave on 2004-12-22
[QUOTE=Enygma]I'm most likely going to be off to Australia at some stage in the new year and don't fancy dragging my desktop with me, so it looks like I'll be getting a laptop then.

I was looking at some Sony VAIOs on [www.sonystyle-europe.com](www.sonystyle-europe.com) the prices are fairly ok. 

Just wondering if people have had many problems with VAIO's and Linux. Is the hardware support ok?[/QUOTE]
 My PCG-GRZ610 works great. It's almost 2 years old and I've been using only linux on it for the past year so I know a few of the pitfalls. Install the spicctrl deb and put sonypi into your /etc/modules so that you can control the backlight when on battery. Acpid is your friend and powernowd works great with the clockmod-p4 module.

---

### Post by Jerrac on 2004-12-23
[QUOTE=keylargodave]My PCG-GRZ610 works great. It's almost 2 years old and I've been using only linux on it for the past year so I know a few of the pitfalls. Install the spicctrl deb and put sonypi into your /etc/modules so that you can control the backlight when on battery. Acpid is your friend and powernowd works great with the clockmod-p4 module.[/QUOTE]
 I have a FRV37, Ubuntu is working great on it! Way better than any other distro I have tried. 

So far I haven't been able to get the backlight and suspend working though. But I haven't tried everything I have found out yet. So... I would suggest you decide what model you want and then figure out if all the hardware is supported before you buy.

Question for keylargodav, What are the spicctrl deb and clockmod-p4 things you are talking about? Are they extra packages to install, or modules that you can compile into the kernel?

---

### Post by serendipity on 2004-12-27
Like all laptops; most important will be your choice on motherboard; i.e. onboard display; i.e. 3D hardware accel, etc.

My VAIO runs like a dream; on Gentoo; not Ubuntu though [Personal preference; still investigating Ubuntu] -  Trickiest part was getting the dual boot installed with the crappy pre-packaged XP thing; Our idea of ideal partitioning was not in sync ...  

The only thing I would change if I could at all; was finding one with a decent; properly supported display card 

HTH

---

### Post by richosus on 2005-02-23
The Vaios are good, the Sony-Europe service is very bad (not only laptops).
I had to send my old F801 2 times to them, had to pay more than 150 Euros and the failure is still the same  ](*,) .
Most things in Ubuntu on Vaio work good.
If you buy a new laptop, don't buy a Sony because they have a very bad support.

---

### Post by jliedeka on 2005-03-03
I sure hope so because I just ordered a new Vaio S270.  I'll be installing Ubuntu Warty on it.  I plan to post details on my web site including any workarounds needed to get all the hardware working.  I'm anticipating a little mode line tweaking for X and possibly struggling with ACPI issues.  I'm pretty confident I'll get all the functionality out of it in fairly short order.  (Famous last words)

     Jim

---

### Post by mafbuntu on 2005-03-19
I've a Sony Vaio, there support is just a disgrace   Buy Toshiba IBM or Dell probably in that order

---

### Post by igeldard on 2005-04-18
Hi,

I'm a Linux wannabee who's Win98SE laptop needs to be scrubbed clean and an OS installed. I'm thinking of Linux/Ubuntu.

Do I need the Sony recovery disc? (can't find it) or could I install from the Ubuntu disc (which I have - the two disc Live and Install set)

Ian (UK)

---

### Post by mendicant on 2005-04-18
[QUOTE=igeldard]
Do I need the Sony recovery disc? (can't find it) or could I install from the Ubuntu disc (which I have - the two disc Live and Install set)
[/QUOTE]

You can just install using the Ubuntu discs.  The recovery discs Sony provides are only for Windows.  Of course, if you ever want to back out of Linux and go back to Windows, you'd need those discs again.

---

### Post by mendicant on 2005-04-18
[QUOTE=mafbuntu]I've a Sony Vaio, there support is just a disgrace   Buy Toshiba IBM or Dell probably in that order[/QUOTE]

I'd agree with not buying a Vaio for their support.  IBM and Dell are much better (no experience with Toshiba).  Just be sure to get the 3 year (or more) support agreements.  It's nice to ship it back to them overnight and have them pick up the tab both ways.

As for installing, I've found the IBMs and Dells to be straightforward.  Back a couple of years ago, I couldn't necessarily say the same thing about Sony.

---

### Post by igeldard on 2005-04-19
Thanks. Are there any "gotchas" or specific issues with the 505FX I should be aware of, or will it install with no trouble  :???:

---

